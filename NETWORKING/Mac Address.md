
Mac Address Aging. 
Ethernet Addressing 
NIC 




## Address Resolution Protocol (ARP)

### 🔹 **Definition:**

**ARP (Address Resolution Protocol)** is used to find the **MAC address** (Layer 2 address) of a device when you only know its **IP address** (Layer 3 address).

---

## ⚙️ **How ARP Works (Step by Step)**

Let’s say **PC1 (192.168.1.10)** wants to send data to **PC2 (192.168.1.20)** on the same network.

1. **PC1 checks its ARP cache**
    - It looks for PC2’s MAC address in its ARP table.
    - If found → it uses it directly.
    - If **not found** → goes to step 2.
2. **PC1 sends an ARP Request (Broadcast)**
    - Message:
        
        “Who has IP 192.168.1.20? Tell 192.168.1.10.”
        
    - Broadcasted to all devices in the LAN (MAC: FF:FF:FF:FF:FF:FF).
        
3. **PC2 receives the ARP Request**
    - It sees that the IP matches its own (192.168.1.20).
4. **PC2 sends an ARP Reply (Unicast)**
    - Message:
        
        “I’m 192.168.1.20 — my MAC is AA:BB:CC:DD:EE:FF.”
        
    - Sent directly to PC1.
        
5. **PC1 updates its ARP Cache**
    - Stores IP ↔ MAC pair for future use.
    - Now it can send data directly to PC2’s MAC address.

---

## 🧠 **ARP Table Example**

|IP Address|MAC Address|Type|
|---|---|---|
|192.168.1.1|00-14-22-01-23-45|Dynamic|
|192.168.1.20|AA-BB-CC-DD-EE-FF|Dynamic|

Check on Windows:

```bash
arp -a

```

```bash 
PS C:\Users\dhara> arp -a

Interface: 10.10.64.208 --- 0x14
  Internet Address      Physical Address      Type
  10.10.64.1            c0-42-d0-a5-46-e0     dynamic
  10.10.64.110          4a-66-6f-4e-ed-3b     dynamic
  10.10.66.115          92-3b-85-ce-48-9f     dynamic
  10.10.68.224          26-58-60-7e-b4-f0     dynamic
  10.10.71.255          ff-ff-ff-ff-ff-ff     static
  224.0.0.22            01-00-5e-00-00-16     static
  224.0.0.251           01-00-5e-00-00-fb     static
  224.0.0.252           01-00-5e-00-00-fc     static
  239.255.255.250       01-00-5e-7f-ff-fa     static
  255.255.255.255       ff-ff-ff-ff-ff-ff     static
PS C:\Users\dhara>
```
---

## 📡 **Purpose**

- Converts **IP → MAC** (necessary for communication on Ethernet/LAN).
- Enables devices in the same network to identify each other’s **hardware addresses.**

---

## 🔒 **Bonus — ARP Types**

|Type|Description|
|---|---|
|**Request**|Broadcast asking for MAC of an IP|
|**Reply**|Unicast answer with the MAC|
|**Gratuitous ARP**|Device announces its own IP/MAC (used in redundancy or updates)|

---

## 🎯 **In Short (Exam Note)**

> ARP maps an IP address to a MAC address.
> 
> It uses **broadcast request** and **unicast reply.**
> 
> Used within the **same LAN** for data delivery.



## 🧠 **Why We Need Both IP and MAC**

- **IP address** → tells **where** the device is (location).
    
- **MAC address** → tells **who** the device is (identity).
    

---

### 🔹 Example:

Think like a **post letter** 📨

- **IP = House address** (to reach the correct street/city).
    
- **MAC = Person’s name** (to give it to the right person in that house).
    

---

### ⚙️ Why both are needed:

- **Router** uses **IP** to send data between networks.
    
- **Switch** uses **MAC** to send data inside the same network.
    

---

### ⚠️ If only one is used:

- Only IP → can’t find exact device.
    
- Only MAC → can’t reach other networks.
    

---

### ✅ Simple line for exam:

> “IP shows location, MAC shows identity.  
> Both are needed to send data correctly in and out of a network.”


### ARP HEADER : 
- Ethernet Header Contains the ARP also

<img width="774" height="401" alt="image" src="https://github.com/user-attachments/assets/f737de7d-b5f1-4152-b426-61f50f669c1a" />




## **How a Switch Learns MAC Addresses**

A **switch** learns **which device (MAC address)** is connected to **which port** by watching the **source MAC** of the frames it receives.

---

### ⚙️ **Step-by-Step 

Working**

Let’s take an example:

|Device|MAC Address|Connected Port|
|---|---|---|
|PC1|AA-AA-AA-AA-AA-AA|Port 1|
|PC2|BB-BB-BB-BB-BB-BB|Port 2|

---

### 🪄 Step 1: **Frame Enters the Switch**

- PC1 sends a frame → it enters the switch via **Port 1**.
- Inside the frame:
    - **Source MAC:** AA-AA-AA-AA-AA-AA
    - **Destination MAC:** BB-BB-BB-BB-BB-BB

---

### 🪄 Step 2: **Switch Learns the Source MAC**

- Switch reads the **Source MAC (AA-AA...)**
- Adds it to its **MAC Address Table  like this:

|MAC Address|Port|
|---|---|
|AA-AA-AA-AA-AA-AA|Port 1|

So the switch now knows:

> “If anyone wants to reach MAC AA-AA-AA, send data out of Port 1.”

---

### 🪄 Step 3: **Switch Checks Destination MAC**

- Switch checks if **BB-BB-BB-BB-BB-BB** is already in its table.

🟡 **If found:**

→ Sends frame only to that port (**Unicast**).

🔴 **If not found:**

→ Floods the frame to all ports except the one it came from (**Broadcast flood**) to find the destination.

---

### 🪄 Step 4: **Switch Learns the Return Path**

- PC2 replies back.
- Now, switch sees:
    - **Source MAC:** BB-BB-BB-BB-BB-BB
    - It learns that MAC belongs to **Port 2**.

|MAC Address|Port|
|---|---|
|AA-AA-AA-AA-AA-AA|Port 1|
|BB-BB-BB-BB-BB-BB|Port 2|

✅ Now the switch knows where both PCs are connected.

---

### ⚙️ **Step 5: Frame Forwarding**

From now on, the switch sends frames **only to the correct port** — no more flooding.

This is called **intelligent forwarding** or **MAC learning**.

---

## 📚 **MAC (CAM) Table Example**

|MAC Address|VLAN|Port|Type|
|---|---|---|---|
|AA-AA-AA-AA-AA-AA|1|Fa0/1|Dynamic|
|BB-BB-BB-BB-BB-BB|1|Fa0/2|Dynamic|

---

## ⚙️ **Types of MAC Entries**

|Type|Meaning|
|---|---|
|**Dynamic**|Learned automatically by switch (auto timeout)|
|**Static**|Manually configured (never expires)|

---

## 🎯 **In Simple (Exam Line)**

> “Switch learns MAC addresses by reading the source MAC of incoming frames and mapping them to the port number.
> 
> It then uses this MAC table to forward frames only to the correct destination.”



## Switch Forwarding Methods

When a frame arrives at a switch, it can use different **forwarding techniques** based on **how quickly** and **how accurately** it wants to send data.

---

### 🧠 1. **Store-and-Forward Switching**

**🪄 How it works:**

- The switch **receives the entire frame** first.
- It **checks for errors** using the **Frame Check Sequence (FCS)** at the end.
- If no errors → forwards the frame to the correct port.

**✅ Advantages:**

- Error-free forwarding (detects bad frames).
- Works with different network speeds (port speed mismatch).

---

### ⚡ 2. **Cut-Through Switching**

**🪄 How it works:**

- Switch **starts forwarding** the frame **as soon as it reads the destination MAC address** (first 6 bytes).
- Doesn’t wait for the full frame or error check.

**✅ Advantages:**

- Very **low latency** (fast forwarding).
---

### 🧩 Summary Table

| Method                | Waits for Full Frame? | Error Checking | Speed      | Typical Use                   |
| --------------------- | --------------------- | -------------- | ---------- | ----------------------------- |
| **Store-and-Forward** | ✅ Yes                 | ✅ Yes (FCS)    | 🐢 Slowest | Reliable enterprise switching |
| **Cut-Through**       | ❌ No                  | ❌ No           | ⚡ Fastest  | Low-latency networks          |
| **Fragment-Free**     | Partially (64 bytes)  | Partial        | ⚙️ Medium  | Legacy LANs (CSMA/CD)         |
