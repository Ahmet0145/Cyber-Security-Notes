# 🌐 Domain Name System (DNS) Fundamentals & Traffic Flow

This section details how the Domain Name System (DNS) functions as the backbone of internet communication, its hierarchical architecture, core record structures, request flows, and relevant security considerations.

---

## ❓ 1. What is DNS?

DNS (Domain Name System) provides a user-friendly way to communicate with devices across the internet without having to memorize complex numerical addresses. 

* **The Core Problem:** Every system connected to the internet is identified by a unique IP address (such as IPv4 addresses formatted as four sets of digits ranging from 0 to 255 separated by periods, e.g., `104.26.10.229`). 
* **The Solution:** Because remembering raw numeric IP addresses for every website is impractical, DNS acts as the "phonebook of the internet," resolving human-readable domain names (e.g., `tryhackme.com`) into their respective target IP addresses.

---

## 🌳 2. Domain Hierarchy

Domain names are structured in a tree-like hierarchy from right to left, managed by different authoritative levels.

```
Root Domain (".")
                   |
    +--------------+--------------+
    |                             |
.com (TLD)                    .edu (TLD)
    |                             |
tryhackme (SLD)                  mit (SLD)
    |
admin (Subdomain)
```

### Hierarchy Breakdown:
* **Root Domain (`.`):** The absolute top of the DNS hierarchy, denoted by a single dot (`.`).
* **TLD (Top-Level Domain):** The rightmost portion of a domain name (e.g., `.com` in `tryhackme.com`).
  * **gTLD (Generic TLD):** Denotes the purpose of a site, historically including `.com` (commercial), `.org` (organizations), `.edu` (education), and `.gov` (government). Modern gTLDs also include formats like `.online`, `.biz`, and `.website`.
  * **ccTLD (Country Code TLD):** Indicates geographic affiliation, such as `.ca` (Canada) or `.co.uk` (United Kingdom).
* **Second-Level Domain (SLD):** Sits directly to the left of the TLD (e.g., `tryhackme` in `tryhackme.com`). SLDs are limited to 63 characters plus the TLD, using alphanumeric characters (`a-z`, `0-9`) and hyphens (without starting, ending, or consecutive hyphens).
* **Subdomain:** Positioned to the left of the Second-Level Domain, separated by a period (e.g., `admin` in `admin.tryhackme.com`). Multiple subdomains can be chained together (e.g., `jupiter.servers.tryhackme.com`). The total overall hostname length cannot exceed 253 characters.

---

## 📋 3. DNS Record Types

DNS uses specific resource record types to handle different categories of network traffic and administrative functions:

| Record Type | Target / Format | Functional Description |
| :--- | :--- | :--- |
| **A** | IPv4 Address (e.g., `104.26.10.229`) | Directly maps a hostname/domain name to a standard 32-bit IPv4 address. |
| **AAAA** | IPv6 Address (e.g., `2606:4700:20::681a:be5`) | Maps a domain name to a modern 128-bit IPv6 address. |
| **CNAME** | Canonical Domain (e.g., `shops.shopify.com`) | Alias record; points a subdomain (e.g., `store.tryhackme.com`) to another domain, requiring a secondary lookup. |
| **MX** | Mail Server (e.g., `alt1.aspmx.l.google.com`) | Directs domain email to handling mail servers; includes priority weights for failover support. |
| **TXT** | Text Strings (e.g., `v=spf1 ...`, `v=DMARC1 ...`) | Holds plain text data used for domain ownership validation and email security policies (SPF/DMARC). |

---

## 🔄 4. What Happens When You Make a DNS Request?

When a host requests a site address (e.g., `www.tryhackme.com`), the resolution workflow progresses through up to 5 steps:
```
[ Client Computer ] ---- (1. Local Cache / Check) ----> [ Recursive DNS Server ]
^                                                       |
|                                             (2. Query Root Server)
|                                                       v
|                                             [ Root DNS Server (".") ]
|                                                       |
|                                             (3. Refer to TLD)
|                                                       v
|                                             [ TLD DNS Server (".com") ]
|                                                       |
|                                             (4. Query Nameserver)
|                                                       v
+===================== (5. Return IP) ======== [ Authoritative Server ]
```
1. **Local Cache Check:** The host operating system checks its internal cache to see if the mapping was recently saved. If absent, a lookup request goes to the **Recursive DNS Server** (typically hosted by the ISP or configured public resolvers like Cloudflare/Google).
2. **Recursive Server Lookup:** The Recursive server checks its own cached entries. If uncached, it initiates a recursive search starting at the internet's **Root DNS Servers**.
3. **Root Server Direction:** The Root server reads the rightmost segment (the TLD like `.com`) and redirects the recursive query to the responsible **TLD DNS Server**.
4. **TLD Server Direction:** The TLD server evaluates the domain request and provides the address for the domain's designated **Authoritative DNS Server** (Nameserver, e.g., `kip.ns.cloudflare.com`).
5. **Authoritative Resolution & TTL Caching:** The Authoritative server retrieves the stored resource record (IP address) and responds to the Recursive server. The Recursive server delivers the result to the client and saves a copy locally based on the record's **TTL (Time To Live)** setting—a lifespan metric defined in seconds to prevent unnecessary network lookups.

---

## 🛡️ 5. Security & Forensics Perspective

* **DNS Spoofing & Cache Poisoning:** Attackers can inject forged IP entries into an unverified Recursive DNS Server's cache, redirecting unsuspecting users away from legitimate hosts toward malicious phishing portals.
* **DNS Tunneling (Exfiltration):** Threat actors often encapsulate secret data within TXT records or subdomains in DNS requests to bypass standard outbound firewall restrictions and extract compromised information.
* **Email Verification Protections:** TXT records form the defensive baseline for email security by storing **SPF (Sender Policy Framework)** and **DMARC** rules, verifying that outbound servers are legally authorized to send emails on behalf of the domain.
