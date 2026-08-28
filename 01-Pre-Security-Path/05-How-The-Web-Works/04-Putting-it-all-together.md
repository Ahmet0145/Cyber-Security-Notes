## 🧩 Putting It All Together & Web Infrastructure

Here is how the entire web request process works from start to finish, along with the key infrastructure components that keep websites fast, reliable, and secure:

---

### 🌐 How a Web Request Works (The Big Picture)

1. **Requesting a Site:** You type a web address into your browser.
2. **DNS Resolution:** Your computer uses **DNS** (Domain Name System) to look up the server's IP address.
3. **Connecting via HTTP:** Your browser contacts the server using the **HTTP protocol**.
4. **Rendering Content:** The server sends back files (HTML, CSS, JS, images), and your browser builds the web page you see.

---

### ⚙️ Key Infrastructure Components

* **Load Balancers:** 
  * **Concept:** When web traffic gets too heavy for one server, a load balancer sits in front and splits incoming traffic across multiple servers.
  * **How It Works:** It uses algorithms like **round-robin** (sending requests to each server in turn) or **weighted** (sending requests to the least busy server).
  * **Health Checks:** It regularly tests each server. If a server stops responding, the load balancer routes traffic away from it to ensure high availability.

* **Content Delivery Networks (CDNs):**
  * **Concept:** CDNs cut down loading times by saving static files (CSS, JS, images, videos) on thousands of servers globally.
  * **How It Works:** When a user requests a file, the CDN delivers it from the server physically closest to the user rather than a distant main server.

* **Databases:**
  * **Concept:** Web servers use databases to store and retrieve data (such as user accounts, posts, or products).
  * **Examples:** MySQL, MSSQL, PostgreSQL, and MongoDB.

* **Web Application Firewall (WAF):**
  * **Concept:** A security shield that sits between incoming web requests and the web server to block attacks and bots.
  * **How It Works:** It inspects traffic for malicious patterns and uses **rate limiting** to restrict how many requests an IP can make per second.

---

### 🖥️ How Web Servers Function

* **Web Server Software:** Programs like **Apache**, **Nginx**, **IIS**, and **Node.JS** listen for HTTP connections and serve files from a root folder (e.g., `/var/www/html` on Linux or `C:\inetpub\wwwroot` on Windows).
* **Virtual Hosts:** Allows one physical server to host multiple websites with different domain names by reading the incoming `Host` header.
* **Static vs. Dynamic Content:**
  * **Static:** Files served exactly as they are saved on the disk (pictures, CSS, static HTML).
  * **Dynamic:** Pages generated on the fly by backend code (PHP, Python, Node.JS) based on user input or database queries.
 
## 🛡️ Security & Forensics Perspective

Understanding web architecture, request dynamics, and client-side execution is essential for web security analysis and forensic investigations:

### 1. Sensitive Data Exposure in Frontend Code
* **Mechanism:** Occurs when developers accidentally leave sensitive information inside client-side source code, accessible via *"View Page Source"* or Developer Tools.
* **Exposed Assets:** Hardcoded credentials (e.g., `<!-- TODO: remove test credentials admin:password123 -->`), hidden internal paths, or API keys embedded inside HTML/JavaScript comments.
* **Security Risk:** Attackers harvest these secrets to gain unauthorized access to administrative functions or backend interfaces.

### 2. Client-Side & HTML Injection (Cross-Site Scripting Fundamentals)
* **Mechanism:** Occurs when an application accepts user input and displays it on the web page without sanitization or encoding.
* **Security Risk:** If input fields accept raw scripts (e.g., `<script>alert(1)</script>`), the browser executes the injected code within the victim's session context.
* **Mitigation Rule:** **Never trust user input.** Always sanitize and encode user-supplied text before rendering it in the DOM.

### 3. Cleartext Transmission & Eavesdropping
* **Mechanism:** Plain HTTP transmits headers, cookies, URL parameters, and request bodies in unencrypted text across the network.
* **Security Risk:** Attackers on the network path can intercept, read, or tamper with sensitive traffic using network sniffing tools. Using HTTPS mitigates this risk through TLS/SSL encryption.

### 4. Information Disclosure via Headers
* **Mechanism:** Response headers like `Server` or `X-Powered-By` often expose exact server software types and version numbers (e.g., `Server: nginx/1.15.8`).
* **Security Risk:** Threat actors use these version details during reconnaissance to identify known unpatched vulnerabilities (CVEs) targeting specific software builds.

### 5. Session Hijacking & Cookie Theft
* **Mechanism:** Because HTTP is stateless, web applications rely on cookies to maintain session states.
* **Security Risk:** Intercepting or stealing an active session cookie (via network sniffing or XSS) allows an attacker to hijack the session and impersonate the victim without needing their credentials.
