
- Passwordless Authentication
- Ansible Inventory
- Understanding Adhoc commands and their usage.
- Examples of common Adhoc commands for system management tasks.
- Exploring the power of Adhoc commands for quick tasks.


### Passwordless Authentication in Ansible: 

**Definition:**

Passwordless authentication allows the **Ansible control node** to connect to **managed nodes** securely **without entering a password** every time.

**How it works:**

1. **SSH Key Pair**:
    - **Private Key** → stays on the Ansible control machine
    - **Public Key** → copied to the `~/.ssh/authorized_keys` file of each managed node
2. **Connection Process:**
    - When Ansible connects to a node, it uses the SSH key pair for authentication.
    - No password prompt appears, enabling automated tasks.

**Benefits:**

- Faster and easier automation
- More secure than using plain passwords
- Avoids storing sensitive credentials in scripts or playbooks

**Setup Example (Simplified):**

```bash
# On control node
ssh-keygen -t rsa
ssh-copy-id user@managed_node

# Test passwordless connection
ssh user@managed_node

```

After this, Ansible can run playbooks or adhoc commands without asking for a password.

---

###  Ansible Inventory :

Is the File Where All the Managed Nodes ( VM Machine ) ip address are Listed There To Comunicate  to the Client Machine.. 

It will Ends withs .YAML or .INI  format 

Example : 
### Super simple example (INI style)

```
[webservers]
web1.example.com
web2.example.com

[dbservers]
db1.example.com

```

- `[webservers]` → group name
- `web1.example.com` → actual machine
- `[dbservers]` → DB machines group

---

### 🔹 IP use panna example

```
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
192.168.1.20

```

**In short:**

> Inventory = “Ansible-ku ethha servers ku Update panna pora nu sollura list.”



---

### What is Adhoc commands : 

Ansible ad-hoc commands are single-line commands executed directly from the command line on an Ansible control node, without the need for a playbook. 

They are designed for quick, one-time tasks and immediate operations across multiple managed nodes.


**Structure of an Ansible ad-hoc command:**

Code

```yaml
ansible <host-pattern> -m <module-name> -a "<module-arguments>"
```

**Key components:**

- **`ansible`:** The main Ansible command-line tool.

- **`<host-pattern>`:** Specifies the target hosts or groups from your inventory file on which the command will be executed. Examples include `all`, `webservers`, `server1:server2`.

- **`<host-pattern>`:** Specifies the target hosts or groups from your inventory file on which the command will be executed. Examples include `all`, `webservers`, `server1:server2`.
- **`m <module-name>`:** Defines the Ansible module to be used for the task. Ansible offers a wide range of modules for various operations (e.g., `ping`, `command`, `shell`, `apt`, `yum`, `service`, `copy`, `file`).
- **`a "<module-arguments>"`:** Provides arguments or parameters specific to the chosen module. These are typically in a `key=value` format or a JSON string for complex structures.


Examples :

Common examples of ad-hoc commands:

Pinging hosts.

Code

```
    ansible webservers -m ping
```

Running a shell command.

Code

```
    ansible all -m shell -a "uptime"
```

- Installing a package (e.g., `nginx`):

Code

```
    ansible webservers -m apt -a "name=nginx state=present"
```


