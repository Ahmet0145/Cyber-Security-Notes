# 🌐 Network Protocols & Traffic Analysis (TCP/UDP & Packets)

This section covers fundamental networking concepts derived from practical lab experiences (TryHackMe), detailing how data is structured, transmitted, and controlled across networks.

---

## 📦 1. Packets vs. Frames

Data transmitted across a network is broken down into smaller chunks to prevent bottlenecks.

* **Packet (Layer 3 - Network Layer):** Contains logical addressing (IP headers) and data payload. Used for routing data across different networks.
* **Frame (Layer 2 - Data Link Layer):** Encapsulates the network packet by adding physical addressing (MAC addresses) for local network delivery.

> **Analogy:** Think of a **Packet** as a letter and a **Frame** as the envelope. The envelope (Frame) gets the letter to the destination building; once opened, the letter (Packet) dictates who gets the message inside.

### Essential Packet Headers
| Header | Purpose |
| :--- | :--- |
| **Time to Live (TTL)** | A counter/timer that prevents packets from looping infinitely on the network if unroutable. |
| **Checksum** | Ensures data integrity. If data is modified in transit, this value changes, flagging corruption. |
| **Source Address** | The IP address of the device sending the packet (so data knows where to return). |
| **Destination Address** | The target IP address where the packet is being routed. |

---

## 🔄 2. TCP (Transmission Control Protocol)

TCP is a **connection-oriented** protocol that guarantees reliable data delivery through synchronization and error control.

### The 3-Way Handshake Process
Before transmitting data, TCP establishes a connection using a 3-step sequence:
1. **SYN (Synchronize):** Client sends an Initial Sequence Number (ISN) to initiate a connection.
2. **SYN/ACK:** Server acknowledges the client's ISN and sends its own sequence number back.
3. **ACK (Acknowledge):** Client acknowledges the server's response. Connection is established.

```
Client (Alice)                             Server (Bob)
    | --- SYN (Init Sequence Number) ----------> |
    | <-- SYN/ACK (Ack ISN + Send Server ISN) -- |
    | --- ACK (Ack Server ISN + Start Data) ---> |
```
### Connection Termination (4-Step Close)
TCP connections reserve system resources and must be closed properly using **FIN** and **ACK** packets:
`Client (FIN) -> Server (ACK) -> Server (FIN) -> Client (ACK)`

---

## ⚡ 3. UDP (User Datagram Protocol)

Unlike TCP, UDP is a **stateless / connectionless** protocol. It does not perform handshakes or track whether packets arrive safely.

* **Advantages:** Minimal overhead, extremely fast transmission rates.
* **Use Cases:** Ideal for real-time applications tolerating packet loss (e.g., VoIP, Video Streaming, DNS queries).
* **Security Note:** Because UDP lacks connection validation, it is frequently exploited in IP spoofing and Reflection Denial-of-Service (DDoS) attacks.

---

## 🔌 4. Common Network Ports & Protocols

Ports are numerical identifiers (0–65535) used to route network traffic to the correct service on a host. Ports **0–1024** are standard reserved ports.

| Protocol | Port | Purpose / Security Context |
| :--- | :--- | :--- |
| **FTP** | 21 | File Transfer Protocol. Unencrypted; sends credentials in cleartext. |
| **SSH** | 22 | Secure Shell. Encrypted remote terminal access. |
| **HTTP** | 80 | HyperText Transfer Protocol. Plaintext web traffic. |
| **HTTPS** | 443 | HTTP Secure. Web traffic encrypted via TLS/SSL. |
| **SMB** | 445 | Server Message Block. Used for file/printer sharing (frequent target for lateral movement). |
| **RDP** | 3389 | Remote Desktop Protocol. GUI-based remote system access. |

---

## 🛡️ 5. Security & Forensics Perspective

Analyzing layer protocols and packet behaviors helps identify attack vectors and perform traffic forensics:

* **SYN Flood Attacks (Layer 4):** Attackers send spoofed `SYN` packets without completing the 3-way handshake with an `ACK`. This keeps server connection queues open, leading to Denial of Service (DoS).
* **Packet Tampering & Integrity:** Forensics analysts rely on the **Checksum** header to verify whether a packet was altered in transit by an adversary or corrupted by bad hardware.
* **UDP Abuse:** Because UDP lacks connection validation (stateless), it is frequently exploited in IP spoofing and Reflection/Amplification DDoS attacks.
* **Unencrypted Cleartext Protocols:** Monitoring traffic on legacy ports like FTP (21) or HTTP (80) allows attackers to capture sensitive data (like credentials and session tokens) directly using packet sniffers like Wireshark.
