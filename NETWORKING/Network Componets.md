# Function of HUB, Switch and Router and POE Switch

#### HUB : 

It works at the **Physical Layer (Layer 1)** of the **OSI model** and acts as a **central connection point** for devices like computers, printers, and servers.

When a hub receives data (in the form of electrical signals or bits) from one device, it **broadcasts** that data to **all other connected devices**, regardless of the intended destination.
## Scenario

Suppose four computers (A, B, C, D) are connected to a hub.

- If **A** sends a message to **B**, the hub will forward that message to **B, C, and D**.
    
- Only **B** accepts it; others discard it.
    
- However, bandwidth is wasted because all received the same data.


> The hub doesn’t have any intelligence it is called as Multiport Reapeter 

### SWITCH :

It works at the **Data Link Layer (Layer 2)** of the **OSI model** and is **intelligent**, unlike a hub.

The switch uses **MAC addresses** to send data **only to the intended device**, not to everyone.

### **Working of a Switch**

1. When a computer sends data, the **frame** (data + MAC info) reaches the switch.
    
2. The switch **reads the destination MAC address** in the frame.
    
3. It **looks up** the address in its **MAC address table** (a list mapping MAC addresses to ports).
    
4. Then it **forwards the data** only to the **specific port** where the destination device is connected.
    
5. If the MAC address is unknown, the switch **temporarily broadcasts** the frame to all ports.
    

💡 **This reduces collisions and increases efficiency** compared to hubs.

###  Scenario

Suppose 4 computers (A, B, C, D) are connected to a switch:

- If **A** sends data to **B**, only **B** receives it.
    
- **C** and **D** don’t see that data.  
    ✅ Efficient and secure communication.


####  PoE Switch (Power over Ethernet Switch)


🔹Same As the Switch But Only thing is it will Share the Electrical Signal and data also , Electrical Signal for the Telephone calling..  

🔹 Works on Layer =2 

This means it can **power network devices** like:

- IP cameras
    
- Wireless access points (Wi-Fi routers)
    
- VoIP phones
    
- IoT devices
    

 > Without needing a separate power adapter.

### ⚙️ Working of PoE Switch

1. The PoE switch sends **data + DC power** through the Ethernet cable.
    
2. The connected device (called a **PD – Powered Device**) receives both power and data.
    
3. The switch automatically **detects** whether a device supports PoE or not:
    
    - If it’s PoE-capable, power is supplied.
        
    - If not, only data is transmitted.



### ROUTER 


🔹A **Router** is a **networking device** that **connects multiple networks together** and directs **data packets** between them.  

🔹 It works at the **Network Layer (Layer 3)** of the **OSI model** using **IP addresses** to find the **best path** for data to travel.

### Working

1. The router receives a **data packet** from one network.
    
2. It reads the **destination IP address** inside the packet.
    
3. It uses a **routing table** to decide the **best route** to reach the destination.
    
4. It then **forwards** the packet to the next network or device along that path.
    

📡 The router ensures that data takes the **most efficient and accurate path** to reach its destination (like between LANs and the Internet).

---

## Half Duplex vs Full Duplex

Both define **how data is transmitted** between two devices in a network.

- **Half Duplex →** One-way at a time. [ HUB ]
    
- **Full Duplex →** Both ways at the same time. [ Switch ]



