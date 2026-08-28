# 🌐 Web Fundamentals: HTTP, HTTPS, & Protocol Architecture

This section covers the underlying mechanics of web communication, detailing how clients interact with web servers through requests, responses, status codes, headers, and session tracking mechanisms.

---

## ❓ 1. What is HTTP & HTTPS?

* **HTTP (HyperText Transfer Protocol):** Developed by Tim Berners-Lee and his team between 1989–1991, HTTP defines the set of rules used for transmitting web page resources (HTML, images, videos, etc.) between web browsers and servers.
* **HTTPS (HyperText Transfer Protocol Secure):** The encrypted version of HTTP. HTTPS uses encryption to protect data in transit, preventing unauthorized eavesdropping and providing authentication to ensure the client is communicating with the legitimate web server rather than an impersonator.

---

## 🔗 2. Anatomy of a URL (Uniform Resource Locator)

A URL provides specific instructions to a browser on how and where to access a target web resource.

```
http://user:password@example.com:80/view-room?id=1#task3
|__|   |-----------| |---------||--||-------| |---||---|
  |         |            |        |      |      |      |
Scheme     User      Host/Domain Port  Path  Parameter Fragment
(Protocol) (Credentials)                      (Query String)
```
* **Scheme:** Specifies the protocol used to access the resource (e.g., `http`, `https`, `ftp`).
* **User:** Optional authentication credentials (`username:password`) embedded directly within the URL.
* **Host:** The domain name or IP address of the target server.
* **Port:** The network port used for the connection (default is port `80` for HTTP and port `443` for HTTPS; configurable from `1` to `65535`).
* **Path:** The specific file path or resource location on the server.
* **Query String:** Parameters passed to the target path to send extra data (e.g., `?id=1`).
* **Fragment:** A page position anchor starting with `#` that directs the browser to a specific section of the loaded page.

---

## 🔄 3. HTTP Request & Response Architecture

### HTTP Request Breakdown
A basic HTTP request contains a request line, headers, and an optional body.

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: [https://tryhackme.com/](https://tryhackme.com/)
```
### HTTP Request Breakdown

* **Line 1 (Request Line):** Specifies the HTTP method (`GET`), the requested target path (`/`), and the protocol version (`HTTP/1.1`).
* **Line 2 (Host Header):** Identifies the target domain name (`tryhackme.com`).
* **Line 3 (User-Agent Header):** Identifies the client browser software and operating system details.
* **Line 4 (Referer Header):** Indicates the previous webpage address that linked the user to the requested page.
* **Line 5 (Blank Line):** HTTP requests conclude with an empty line to signal the end of the request header section.

```
HTTP Response Breakdown
The response from the server includes status information, headers, and the requested payload content.
Line 5 (Blank Line): HTTP requests conclude with an empty line to signal the end of the request header section.

HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
  <title>TryHackMe</title>
</head>
<body>
  Welcome To TryHackMe.com
</body>
</html>
```

### HTTP Response Breakdown

* **Line 1 (Status Line):** Specifies the protocol version (`HTTP/1.1`) and the HTTP status code (`200 OK`).
* **Line 2 (Server Header):** Discloses the web server software type and version (`nginx/1.15.8`).
* **Line 3 (Date Header):** Displays the current timestamp and timezone of the web server.
* **Line 4 (Content-Type Header):** Informs the client about the media type of the returned content (e.g., `text/html`).
* **Line 5 (Content-Length Header):** Specifies the exact payload size in bytes to ensure full data delivery.
* **Line 6 (Blank Line):** Indicates the end of response headers before the payload body.
* **Lines 7–14 (Body):** The requested HTML content or data payload.

---

## 🛠️ 4. HTTP Methods

HTTP methods indicate the desired action to be performed on the target resource:

| Method | Functional Purpose |
| :--- | :--- |
| **`GET`** | Retrieves data or content from the web server without modifying server state. |
| **`POST`** | Submits data to the server to create new records or process user input. |
| **`PUT`** | Uploads data to update or replace an existing resource on the web server. |
| **`DELETE`** | Requests the permanent removal of a specified resource from the server. |

---

## 📊 5. HTTP Status Codes

Status codes are 3-digit numerical responses returned by the server to inform the client about the request outcome.

### Status Code Ranges

* **`100–199` (Informational):** Indicates that the request was received and processing continues.
* **`200–299` (Success):** Confirms that the client request was successfully received and processed.
* **`300–399` (Redirection):** Directs the client browser to take further action or navigate to a new URL.
* **`400–499` (Client Errors):** Indicates that the request contains invalid syntax or cannot be fulfilled.
* **`500–599` (Server Errors):** Indicates that the server encountered an error while processing a valid request.

### Common Status Codes

| Code | Status Message | Description |
| :--- | :--- | :--- |
| **`200`** | OK | The request completed successfully. |
| **`201`** | Created | A new resource was successfully created on the server. |
| **`301`** | Moved Permanently | The requested resource has been permanently relocated to a new URL. |
| **`302`** | Found | The resource is temporarily residing under a different URL. |
| **`400`** | Bad Request | The server could not understand the request due to invalid client syntax. |
| **`401`** | Unauthorized | Authentication is required to access the requested resource. |
| **`403`** | Forbidden | The client lacks access permissions, regardless of authentication status. |
| **`404`** | Page Not Found | The requested path or resource does not exist on the server. |
| **`405`** | Method Not Allowed | The requested HTTP method is not supported for the target path. |
| **`500`** | Internal Server Error | The server encountered an unexpected error processing the request. |
| **`503`** | Service Unavailable | The server is temporarily unable to handle requests (e.g., overload or maintenance). |

---

## 📑 6. HTTP Headers & Cookies

Headers allow the client and server to pass additional metadata within HTTP messages.

### Key Headers

#### 📤 Request Headers:
* **`Host`**: Specifies the targeted hostname (enabling virtual hosting for multiple sites on one IP).
* **`User-Agent`**: Supplies browser engine and platform identification strings.
* **`Content-Length`**: Specifies the byte size of data sent in request bodies (e.g., forms).
* **`Accept-Encoding`**: Lists supported compression algorithms (e.g., `gzip`, `deflate`).
* **`Cookie`**: Sends previously assigned session tokens back to the server.

#### 📥 Response Headers:
* **`Set-Cookie`**: Sends a session token or identifier to be saved on the client machine.
* **`Cache-Control`**: Defines caching policies and expiration times for local storage.
* **`Content-Type`**: Declares the MIME type of the returned resource (`text/html`, `application/json`, etc.).
* **`Content-Encoding`**: Discloses the compression format used on the response payload.

---

## State Management via Cookies
Because HTTP is a stateless protocol (it does not natively retain state across separate connections), web applications use cookies to maintain user sessions.

```
Client                                                   Server
  |                                                        |
  |--- (1) GET / ----------------------------------------->|
  |<-- (2) HTTP 200 OK (HTML Form) ------------------------|
  |                                                        |
  |--- (3) POST / (name=adam) ---------------------------->|
  |<-- (4) HTTP 200 OK [Set-Cookie: name=adam] ------------|  <-- Server issues token
  |                                                        |
  |--- (5) GET / [Cookie: name=adam] --------------------->|  <-- Client echoes token
  |<-- (6) HTTP 200 OK ("Welcome back adam") --------------|
```

### Session Workflow / Cookie Lifecycle

1. **Initial Request:** The client sends an unauthenticated `GET` request.
2. **Authentication / Form Input:** The client submits credentials or identifying information via a `POST` request.
3. **Session Issuance:** The server verifies the input and issues a `Set-Cookie` header containing a unique session identifier or token.
4. **State Persistence:** Subsequent HTTP requests automatically attach the `Cookie` header, allowing the server to recognize the client identity and maintain authentication status.
