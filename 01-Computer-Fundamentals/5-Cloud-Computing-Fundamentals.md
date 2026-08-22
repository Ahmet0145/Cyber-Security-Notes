# ☁️ 5. Cloud Computing Basics & Cost Optimization

## 📌 Context & Practical Scenario: Scalability
When deploying applications locally, scaling requires purchasing physical hardware, configuring networks, and managing potential downtime during traffic spikes. Cloud computing eliminates hardware dependencies by delivering computing power, storage, and networking on demand over the internet.

### 🧪 Hands-on Lab Simulation (Practicing Deployment & Billing)
In practical lab environments (simulating AWS EC2 management), we deploy and optimize cloud resources based on operational demand:
* **Provisioning Resources:** Deploying small instances (`t3.micro` @ 10 credits/mo) for core services (web/db) and high-performance instances (`m5.large` @ 70 credits/mo) for intensive tasks.
* **Cost Optimization (Billing Control):** Halting inactive instances reduces unnecessary resource drain—dropping estimated monthly usage from **170.00 credits/month down to 30.00 credits/month** while keeping critical interfaces active.

---

## ⏳ Evolution of Server Infrastructure

| Era | Infrastructure Model | Key Characteristics |
| :--- | :--- | :--- |
| **1960s – Early 2000s** | **Physical Servers Era** | On-premise hardware; single-purpose deployment; expensive and slow to scale. |
| **1999 – 2006** | **Virtualization Era** | Multiple virtual servers on single physical hosts; improved hardware utilization. |
| **2003 – 2006** | **Automation & Remote Management** | Early automated infrastructure provisioning over the internet. |
| **2006** | **Cloud Computing Launch (AWS)** | On-demand virtual instances and storage rental without hardware ownership. |
| **2012 – Present** | **Modern Cloud & Containers** | AWS/Azure/GCP dominance, containerized microservices, global-scale platforms. |

---

## 🏠 Service Models: The Housing Analogy

Cloud service models reflect different levels of user management responsibility:

### Core Cloud Deployment Models
* **Public Cloud:** Cost-effective, highly scalable shared infrastructure managed by third-party vendors (AWS, Azure, GCP).
* **Private Cloud:** Dedicated infrastructure exclusive to single organizations requiring strict control and regulatory compliance.
* **Hybrid Cloud:** Integrated environment combining private control for sensitive data with public cloud scalability for peak loads.

---

## ⚡ Key Characteristics & Benefits

* **Scalability & Elasticity:** Dynamically scale compute capacity up or down to match real-time workload demands.
* **On-Demand Self-Service:** Instantly provision or terminate servers and storage without manual vendor intervention.
* **Pay-Only-For-What-You-Use:** Consumption-based billing models that eliminate upfront infrastructure capital expenditure (CapEx).
* **High Availability & Global Access:** Distributed data centers ensure service availability and low-latency access worldwide.

---

## 🛡️ Security & Defensive Perspective

* **Shared Responsibility Model:** Cloud security is divided; the cloud provider secures the infrastructure *of* the cloud (hardware, hypervisors), while the customer secures everything *in* the cloud (OS patches, IAM roles, application security).
* **Identity & Access Management (IAM) Misconfigurations:** Over-privileged API keys or permissive IAM roles represent the leading entry vector for cloud environment breaches.
* **Publicly Exposed Storage Containers:** Misconfigured access controls on cloud storage (e.g., open AWS S3 buckets) frequently expose confidential data to unauthorized indexing.
* **Denial of Wallet (DoW) / Resource Exhaustion:** Attackers triggering high resource utilization or spin-up scripts can cause massive financial exhaustion via pay-per-use billing models.
