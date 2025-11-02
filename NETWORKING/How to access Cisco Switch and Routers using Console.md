<img width="809" height="482" alt="image" src="https://github.com/user-attachments/assets/cc574cd7-0ac2-488b-9463-4cc59a1791f5" />



https://medium.com/@jobanjitsinghamritsar/how-to-configure-cisco-switch-in-10-steps-tutorial-with-commands-8b8ad6927ac5


## **Cisco IOS Modes**

| **Mode No.** | **Mode Name** | **Prompt Example** | **Purpose / Function** |
| --- | --- | --- | --- |
| 1️⃣ | **User EXEC Mode** | `Router>` | Basic monitoring commands (can’t configure). |
| 2️⃣ | **Privileged EXEC Mode (Enable Mode)** | `Router#` | Access all commands and configuration modes. |
| 3️⃣ | **Global Configuration Mode** | `Router(config)#` | Make system-wide configuration changes. |
| 4️⃣ | **Interface Configuration Mode** | `Router(config-if)#` | Configure specific interfaces (like GigabitEthernet or FastEthernet). |
| 5️⃣ | **Line Configuration Mode** | `Router(config-line)#` | Configure console, SSH, or Telnet access lines. |


### Work Flow or Mode Hierarchy

<img width="508" height="271" alt="image" src="https://github.com/user-attachments/assets/75565b8d-1e62-471d-a2c4-f9d7616cd842" />


## **Types of Storage in Cisco IOS**

Cisco devices have **four main types of memory/storage**, each with a **specific purpose**.

| **Memory Type** | **Full Form** | **Purpose / Function** |
| --- | --- | --- |
| **1️⃣ ROM** | Read Only Memory | - Contains **bootstrap program** and **POST (Power-On Self-Test)**.  - Used to **load the IOS** during bootup. |
| **2️⃣ FLASH** | — | - Stores the **Cisco IOS image (Operating System)**.  - **Non-volatile**, data remains even after reboot. |
| **3️⃣ NVRAM** | Non-Volatile RAM | - Stores **startup configuration file** (`startup-config`).  - Configuration loads from here when the device boots. |
| **4️⃣ RAM** | Random Access Memory | - Stores **running configuration** (`running-config`) and **routing tables**.  - **Volatile**, data is lost after reboot. |

---

### 🧠 **In short:**

- **ROM:** Boot and diagnostics.
- **FLASH:** Stores IOS software.
- **NVRAM:** Saves startup configuration.
- **RAM:** Holds running configuration.





To login : Possible ways to configure it.. 

  

logins :

console

Telnet

SSH
