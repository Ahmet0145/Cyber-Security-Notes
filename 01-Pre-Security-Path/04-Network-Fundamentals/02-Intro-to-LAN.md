# 🌐 Network Topologies, Hardware & Core Protocols

---

## 📌 1. Local Area Network (LAN) Topologies

A **network topology** defines the physical or logical arrangement in which devices connect and communicate within a network.

| Topology | Network Architecture | Key Advantages | Critical Disadvantages |
| :--- | :--- | :--- | :--- |
| **Star Topology** | Devices connect individually to a central switch/hub. | Highly scalable and easy to troubleshoot. | Central device forms a **Single Point of Failure**. |
| **Bus Topology** | Devices connect to a single central backbone cable. | Low initial setup cost and minimal cabling. | Backbone cut drops entire network; high traffic collision. |
| **Ring Topology** | Devices connect sequentially in a circular loop. | Reduces bottlenecks; predictable data flow. | Failure of a single device or cable breaks the loop. |

### Visual Layouts & Flow
* **Star:** `[Device] -- (Central Switch) -- [Device]`
* **Bus:** `[Device] --|-- (Backbone Cable) --|-- [Device]`
* **Ring:** `[Device] --> [Device] --> [Device] --> [Device]`

---

## 🔀 2. Network Infrastructure: Switches vs. Routers

Connecting and routing data across networks requires specialized Layer 2 and Layer 3 devices.
```
              +-------------------+
              |   The Internet    |
              +---------+---------+
                        |
                +-------+-------+
                |   Router #1   |  <--- (Layer 3: IP Routing)
                +---+-------+---+
                    |       |
        +-----------+       +-----------+
        |                               |
+-------+-------+               +-------+-------+
|   Switch #1   |               |   Switch #2   |  <--- (Layer 2: MAC Switching)
+---+-------+---+               +---+-------+---+
   |        |                      |       |
[PC 1]   [PC 2]                 [PC 3]   [PC 4]

```
* **Switch (Layer 2):** Connects endpoints within the same local network using MAC address forwarding tables.
* **Router (Layer 3):** Connects separate subnets/networks together and routes packets across optimal paths using IP addresses.

---

## 🍰 3. Network Segmentation & Subnetting

Subnetting divides a larger IP network into smaller, isolated logical subnets.

```
                 +-------------------+
                 |   Internal LAN    |
                 +---------+---------+
                           |
        +------------------+------------------+
        |                                     |
+-------+-------+                     +-------+-------+
|  Accounting   |                     |    Finance    |
| Subnet (.1.0) |                     | Subnet (.2.0) |
+---------------+                     +---------------+
```
### Subnet Components & Roles
* **Network Address:** Identifies the start of the specific network subnet (e.g., `192.168.1.0`).
* **Host Address:** Uniquely identifies an individual device within that subnet (e.g., `192.168.1.100`).
* **Default Gateway:** Router interface address used to forward traffic destined outside the local network (e.g., `192.168.1.254`).

---

## 📡 4. Key Network Protocols (ARP & DHCP)

### 🤝 Address Resolution Protocol (ARP)
Maps Layer 3 logical IP addresses to Layer 2 physical MAC addresses.

```
[Request]  (Host) --- Broadcast: "Who has 192.168.1.10?" ---> [All Devices]
[Reply]    (Target) --- Unicast: "I have 192.168.1.10, MAC: 18:AC:33:..." ---> (Host)
```
### 📜 Dynamic Host Configuration Protocol (DHCP)
Automatically assigns IP network configuration parameters to client devices via the 4-step **DORA** process.

```
Client                                               DHCP Server
|                                                        |
| -------- 1. DHCP Discover (Are servers available?) ->  |
| <------- 2. DHCP Offer (IP 192.168.1.10 reserved) ---- |
| -------- 3. DHCP Request (Accepting IP offer) ------>  |
| <------- 4. DHCP ACK (Configuration confirmed) ------  |
```
---

## 🛡️ 5. Security & Forensics Perspective

Understanding core network topology and low-level protocol behavior is critical for threat hunting, incident response, and vulnerability analysis:

* **ARP Poisoning & Man-in-the-Middle (MitM) Attacks:**  
  Because standard ARP lacks packet authentication, attackers can flood malicious, unsolicited ARP replies across a LAN. By claiming ownership of the Default Gateway's IP address, the attacker's machine receives all outgoing subnet traffic for inspection, interception, or modification before forwarding it.

* **Switch Port Security & MAC Flooding:**  
  In a Star topology, switches isolate traffic per port using a Content Addressable Memory (CAM) table. Attackers can launch MAC flooding attacks to fill the switch CAM table, forcing the switch into a "fail-open" mode where it behaves like a hub, broadcasting all frames across every port and enabling packet sniffing.

* **Rogue DHCP Server Deployment:**  
  An attacker can deploy an unauthorized DHCP server on a local network segment to answer `DHCP Discover` broadcasts faster than the legitimate server. By distributing rogue configuration parameters (such as pointing the default gateway or DNS server to an attacker-controlled host), the adversary seamlessly hijacks network traffic.

* **Subnet Segmentation Deficiencies & Lateral Movement:**  
  Flattened networks without strict VLANs or subnet boundary firewalls allow attackers who compromise a single low-security endpoint (e.g., a guest Wi-Fi host) to freely move laterally into sensitive internal subnets (e.g., Finance or HR databases).
