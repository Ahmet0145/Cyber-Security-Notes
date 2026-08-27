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
