# 🌐 Network Protocols & Traffic Analysis (TCP/UDP & Packets)

This documentation provides an operational overview of core networking protocols, packet structures, dynamic connection workflows, and key security perspectives.

---

## 📦 1. Packets vs. Frames

Data moving across a network is chunked into smaller transmission units to optimize bandwidth usage and prevent system bottlenecks.

* **Packet (Layer 3 - Network Layer):** Contains logical network routing data (IP header information) along with payload contents.
* **Frame (Layer 2 - Data Link Layer):** Wraps the layer 3 packet with local physical link layer information (MAC addressing) for delivery inside the immediate network segment.

> **Analogy:** Consider a **Packet** to be a letter addressed to an end destination, while a **Frame** acts as the envelope carrying local delivery information to get it across intermediate transfer points.

### Key Header Fields
| Header Field | Function | Operational Relevance |
| :--- | :--- | :--- |
| **Time to Live (TTL)** | Decrements with each hop to kill unroutable looping packets. | Useful for OS fingerprinting and tracing path dynamics. |
| **Checksum** | Computes a validation value to verify payload integrity. | Identifies packet corruption or dynamic inline modifications. |
| **Source IP** | Specifies the originating device address. | Identifies sender location; subject to spoofing in stateless models. |
| **Destination IP** | Indicates the intended destination IP address. | Used by firewalls and routers to direct packet movement. |

---

## 🔄 2. TCP (Transmission Control Protocol)

TCP is a **connection-oriented** protocol designed to establish reliable and sequenced communication paths between network nodes.

### Standard 3-Way Handshake
Before sending actual data, a baseline connection is built using the following control sequence:
1. **SYN (Synchronize):** Initiator requests connection setup with a initial sequence number.
2. **SYN/ACK (Synchronize-Acknowledge):** Receiver validates the initial request and transmits back its own parameter response.
3. **ACK (Acknowledge):** Initiator sends a confirmation message to complete connection setup.
```
Client (Host A)                            Server (Host B)
     | --- SYN (Init Sequence Number) ----------> |
     | <-- SYN/ACK (Ack ISN + Send Server ISN) -- |
     | --- ACK (Ack Server ISN + Session Ready)-> |
```
### Complete Network Event Execution Log (Simulation Example)
The log below demonstrates how ARP layer resolution precedes the TCP connection sequence when two systems communicate across local routing boundaries:

```text
HANDSHAKE: Initiating connection flow from computer1 to computer3
HANDSHAKE: Dispatching SYN frame from computer1 to target computer3
ROUTING: computer1 determines computer3 is external; offloading to local gateway router
ARP REQUEST: Querying MAC address for gateway router from computer1
ARP RESPONSE: Gateway router returns MAC identity to computer1
ARP REQUEST: Gateway router queries MAC address belonging to computer3
ARP RESPONSE: computer3 provides MAC destination details to gateway router
HANDSHAKE: computer3 receives initial SYN; responds with SYN/ACK frame
HANDSHAKE: computer1 receives SYN/ACK; dispatches final ACK back to computer3
HANDSHAKE: Connection established successfully between computer1 and computer3
TCP DATA: Payload transmission initiated from computer1 to computer3
TCP DATA: computer3 accepts payload and returns transmission ACK frame

```
---

### Connection Termination (4-Step Teardown)
Because active TCP sessions maintain allocated system buffers and state tracking tables, sessions undergo explicit graceful termination using **FIN** (Finish) and **ACK** flags:
`Client (FIN) -> Server (ACK) -> Server (FIN) -> Client (ACK)`

---

## ⚡ 3. UDP (User Datagram Protocol)

UDP is a **stateless / connectionless** transport layer protocol. It dispenses with connection pre-allocation, sequencing, and delivery guarantees in favor of low-latency execution.

* **Advantages:** Minimal protocol overhead, zero connection establishment latency, high efficiency for real-time streams.
* **Use Cases:** Optimal for performance-sensitive applications tolerating minor data loss (e.g., DNS resolution, VoIP, live video streaming, SNMP management).
* **Inherent Risks:** Lack of state verification allows threat actors to easily forge source addresses, making UDP a frequent carrier for reflective Denial-of-Service (DoS) attacks.

---

## 🔌 4. Common Network Ports & Services

Ports are 16-bit numerical identifiers (0–65535) used by host operating systems to map incoming transport traffic to specific application processes. Well-Known Ports range from **0 to 1023**.

| Service / Protocol | Default Port | Transport | Operational & Security Profile |
| :--- | :--- | :--- | :--- |
| **FTP** | 21 | TCP | File Transfer Protocol. Transmits control commands and user authentication credentials in cleartext. |
| **SSH** | 22 | TCP | Secure Shell. Provides encrypted command-line management and secure data tunneling. |
| **HTTP** | 80 | TCP | HyperText Transfer Protocol. Serves unencrypted web application communications. |
| **HTTPS** | 443 | TCP | HTTP Secure. Encrypts web communications using Transport Layer Security (TLS/SSL). |
| **SMB** | 445 | TCP | Server Message Block. Handles network file sharing; frequently targeted for internal lateral movement and ransom payloads. |
| **RDP** | 3389 | TCP | Remote Desktop Protocol. Grants graphical user interface access to remote host endpoints. |

---

## 🛡️ 5. Security & Forensics Perspective

Analyzing layer protocols and packet behaviors helps identify attack vectors and perform traffic forensics:

* **SYN Flood Attacks (Layer 4):** Attackers exploit TCP connection establishment by flooding target endpoints with continuous `SYN` requests using spoofed source IPs. The target allocates resources to track each session state while awaiting non-existent `ACK` responses, depleting connection queues and inducing a Denial-of-Service (DoS) state.
* **Packet Tampering & Integrity Verification:** Forensics analysts evaluate protocol **Checksum** fields and frame check sequences to identify corrupted transmissions, deliberate payload modifications, or hardware layer faults.
* **UDP Abuse & Amplification:** Because UDP operates without connection handshakes (stateless), malicious actors frequently spoof target IP addresses when querying public UDP-based services (such as open DNS resolvers or NTP servers), redirecting amplified payload responses to crush victim targets.
* **Cleartext Inspection & Traffic Sniffing:** Legacy protocol implementations—such as unencrypted HTTP (80) or FTP (21)—allow internal or adversary network sniffers (e.g., Wireshark) to capture session identifiers, sensitive administrative payloads, and authentication hashes directly off the wire.
* **Stateful vs. Stateless Inspection:** Security controls utilize **Stateless Firewalls** to quickly parse static packet parameters (source/destination IP, port rules) for bulk traffic filtering, while **Stateful Firewalls** inspect full protocol sessions and handshake states to block anomalous or out-of-sequence network packets.
