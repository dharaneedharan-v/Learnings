
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