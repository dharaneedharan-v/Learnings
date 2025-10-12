
# Ansible Conditionals and Loops

- Using conditionals in Ansible to control task execution.
- Implementing loops for repetitive tasks.
- [x] Practical examples of conditionals and loops in playbooks.

## Condition (when)

We use `when` to run a task **only if** some condition is true.

### 🔹 Example 1: Simple variable check

```yaml

- name: Install nginx only on Ubuntu
  apt:
    name: nginx
    state: present
  when: ansible_facts['os_family'] == "Debian"

```

👉 This will run **only if** the OS family is Debian (Ubuntu, etc.).

---

### 🔹 Example 2: Use your own variable

```yaml
- name: Restart service only if enabled
  service:
    name: nginx
    state: restarted
  when: service_enabled | bool

```

If you set in vars:

```yaml
service_enabled: true

```

Then it will restart. If `false`, it’ll skip.

---

## 🔁 **Loops**

Loops are used when you want to **repeat a task** multiple times with different values.

---

### 🔹 Example 1: Simple loop with `loop`

```yaml
- name: Install multiple packages
  apt:
    name: "{{ item }}"
    state: present
  loop:
    - git
    - curl
    - vim

```

👉 This will install `git`, `curl`, and `vim` one by one.

---

### 🔹 Example 2: Loop with dictionary (key-value)

```yaml
- name: Create multiple users
  user:
    name: "{{ item.name }}"
    state: present
    shell: "{{ item.shell }}"
  loop:
    - { name: 'muthu', shell: '/bin/bash' }
    - { name: 'ravi', shell: '/bin/zsh' }

```

👉 Creates users `muthu` and `ravi` with different shells.

---

### 🔹 Example 3: Using `with_items` (old method)

```yaml
- name: Install tools
  yum:
    name: "{{ item }}"
    state: present
  with_items:
    - httpd
    - wget
    - unzip

```

👉 Same as `loop`, just old-style syntax (still works).

---

## 💪 3️⃣ — **Combine condition + loop**

You can use both `when` and `loop` together!

```yaml
- name: Install packages only on RedHat
  yum:
    name: "{{ item }}"
    state: present
  loop:
    - httpd
    - vim
  when: ansible_facts['os_family'] == "RedHat"

```

👉 Loops through both packages, **only if** the OS is RedHat.

---

## ⚙️ Bonus: Loop until condition (like retry)

```yaml
- name: Wait for website to come up
  uri:
    url: http://localhost:8080
    status_code: 200
  register: result
  retries: 5
  delay: 10
  until: result.status == 200

```

👉 Tries 5 times every 10 seconds until it gets a 200 OK.

---

## 🧾 Summary Table

| Concept | Keyword | Example |
| --- | --- | --- |
| Condition | `when` | Run task if OS is Debian |
| Simple Loop | `loop` | Install multiple packages |
| Dictionary Loop | `loop` | Create users with details |
| Old style loop | `with_items` | Install list of tools |
| Condition + Loop | `loop` + `when` | Run on specific OS only |
| Retry loop | `until` | Wait for service availability |


---


Ansible Realtime project
Task 1
Create three(3) EC2 instances on AWS using Ansible loops

2 Instances with Ubuntu Distribution
1 Instance with Centos Distribution
Hint: Use connection: local on Ansible Control node.

Task 2
Set up passwordless authentication between Ansible control node and newly created instances.

Task 3
Automate the shutdown of Ubuntu Instances only using Ansible Conditionals

Hint: Use when condition on ansible gather_facts