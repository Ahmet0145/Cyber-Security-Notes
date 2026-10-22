
# 🛡️ OWASP Top 10 Web Application Security Risks

Welcome to my OWASP Top 10 research and documentation repository. This folder serves as a comprehensive technical knowledge base covering the critical web application security risks defined by OWASP.

---

## 📊 Vulnerability Matrix & Overview

| Identifier | Vulnerability Name | Primary Risk Factor | Key Prevention Strategy |
| :--- | :--- | :--- | :--- |
| **A01:2021** | [Broken Access Control](./01-A01-Broken-Access-Control.md) | Unauthorized privilege escalation | Enforce Principle of Least Privilege |
| **A02:2021** | [Cryptographic Failures](./02-A02-Cryptographic-Failures.md) | Sensitive data exposure | Strong encryption algorithms (AES, TLS) |
| **A03:2021** | [Injection](./03-A03-Injection.md) | Untrusted user data execution | Parameterized queries & Input sanitization |
| **A04:2021** | [Insecure Design](./04-A04-Insecure-Design.md) | Architectural flaws | Threat modeling & Secure design patterns |
| **A05:2021** | [Security Misconfiguration](./05-A05-Security-Misconfiguration.md) | Unhardened default settings | Automated hardening & Patch management |
| **A06:2021** | [Vulnerable & Outdated Components](./06-A06-Vulnerable-and-Outdated-Components.md) | Unpatched third-party libraries | Software Bill of Materials (SBOM) & Audits |
| **A07:2021** | [Identification & Authentication Failures](./07-A07-Identification-and-Authentication-Failures.md) | Session hijacking & Weak logins | Multi-Factor Authentication (MFA) & Limit logins |
| **A08:2021** | [Software & Data Integrity Failures](./08-A08-Software-and-Data-Integrity-Failures.md) | Insecure CI/CD pipelines & Deserialization | Digital signatures & Verification checks |
| **A09:2021** | [Security Logging & Monitoring Failures](./09-A09-Security-Logging-and-Monitoring-Failures.md) | Undetected active breaches | Centralized SIEM & Real-time alerting |
| **A10:2021** | [Server-Side Request Forgery (SSRF)](./10-A10-Server-Side-Request-Forgery-SSRF.md) | Unauthorized internal network requests | URL Whitelisting & Network segmentation |

---

## 📚 References & Citation

This documentation is compiled and adapted using official resources and industry security standards from OWASP:

* **Official Source:** [OWASP Top 10 Official Documentation](https://owasp.org/www-project-top-ten/)
* **Educational Material:** Concepts and practical lab scenarios adapted from [TryHackMe](https://tryhackme.com/) OWASP Top 10 Modules.
* **Author Note:** All vulnerability notes are enriched with independent research, code analysis, and a dedicated *Security & Forensics Perspective*.
