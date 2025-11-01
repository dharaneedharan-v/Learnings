
## Fiber Optic Cables  :

Used for **high-speed data transmission** using **light signals** instead of electricity.

There are two main types: **Single-Mode** and **Multi-Mode** fiber cables.

---

### 🔹 **Single-Mode Fiber (SMF)**

- **Core Diameter:** ~9 micrometers (very thin)
- **Light Source:** Laser
- **Distance:** Long distance (up to 100 km or more)
- **Speed:** Very high (10 Gbps to 100 Gbps)
- **Color Code (Jacket):** **Yellow**
- **Use Case:** Long-distance communication — telecom, internet backbone, WAN link
---
### 🔹 **Multi-Mode Fiber (MMF)**

- **Core Diameter:** 50 or 62.5 micrometers (thicker)
- **Light Source:** LED or laser (VCSEL)
- **Distance:** Short distance (up to 2 km max)
- **Speed:** High, but less than SMF
- **Color Code (Jacket):** **Orange** (OM1/OM2) or **Aqua** (OM3/OM4)
- **Use Case:** Short-range — LANs, data centers, campus networks
---

### ⚙️ **Quick Comparison**

|Feature|**Single-Mode Fiber**|**Multi-Mode Fiber**|
|---|---|---|
|**Core Size**|9 µm|50–62.5 µm|
|**Light Source**|Laser|LED/VCSEL|
|**Distance**|Long (up to 100 km+)|Short (up to 2 km)|
|**Speed**|Very High|High|
|**Color Code**|Yellow|Orange / Aqua|
|**Use Case**|WAN, Telecom|LAN, Data Center|

---

💡 **Summary:**

> - **SMF →** Long distance, single light path, high cost.

> - **MMF →** Short distance, multiple light paths, cheaper.
- ---

# Straight Through Cable and Crossover Cable :

### 🔹 **Straight-Through Cable**

- **Definition:** Same wire order on both ends (T568A–T568A or T568B–T568B).
- **Purpose:** Connect **different types of devices**.
- **Use Between:**
    - PC ↔ Switch
    - PC ↔ Hub
    - Router ↔ Switch
- **Function:** TX of one → RX of another (already opposite).
- **Example Use:** Office LAN, home network connections.

---

### 🔹 **Crossover Cable**

- **Definition:** Different wire order at each end (T568A–T568B).
- **Purpose:** Connect **similar devices** directly.
- **Use Between:**
    - PC ↔ PC
    - Switch ↔ Switch
    - Router ↔ Router
- **Function:** TX and RX wires are crossed.
- **Example Use:** Direct data transfer or lab setup.



### Why we Want the Straight Through Cable and Crossover Cable: 

- To connect **similar devices** (both having the same pin roles) directly — without a hub or switch in between.  
- It **crosses the transmit and receive wires** so that data from one device’s TX goes into the other’s RX.

|Cable|Purpose|Used Between|Real Example|
|---|---|---|---|
|**Straight-Through**|Connect _different_ devices|PC ↔ Switch|Home or office LAN|
|**Crossover**|Connect _similar_ devices|PC ↔ PC, Switch ↔ Switch|Lab testing, direct transfer|
