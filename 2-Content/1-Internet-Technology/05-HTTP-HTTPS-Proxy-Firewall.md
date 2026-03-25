# Day 5 — HTTP, HTTPS, Proxy Servers & Firewalls

📖 **Type:** Theory Session
🕐 **Duration:** 2 Hours
📚 **Unit:** 1 — Internet Technology

---

## Learning Objectives

By the end of this session, students will be able to:
- Explain the HTTP protocol and its features
- Describe the HTTP request-response model with methods and status codes
- Differentiate between HTTP and HTTPS
- Explain what proxy servers and firewalls do

---

## 1. HTTP — HyperText Transfer Protocol

### What is HTTP?

> **Analogy:** HTTP is like the **language** spoken between a customer (browser) and a waiter (server) in a restaurant. The customer says "I'd like the menu" (GET request), and the waiter brings it. The customer says "I'd like to order butter chicken" (POST request), and the waiter takes the order to the kitchen.

**HTTP** is an application-layer protocol that defines how messages are formatted and transmitted between web clients and servers.

### Features of HTTP

| Feature | Description |
|---------|-------------|
| **Stateless** | Each request is independent — server doesn't remember previous requests |
| **Text-based** | Messages are readable text (not binary) |
| **Request-Response** | Client always initiates; server always responds |
| **Connectionless** | Connection is closed after each request-response (HTTP/1.0) |
| **Media independent** | Can transfer any type of data (HTML, images, video, JSON) |
| **Port** | Uses port 80 by default |

---

## 2. HTTP Request-Response Model

### HTTP Request Structure

```
GET /index.html HTTP/1.1          ← Request Line
Host: www.example.com             ← Headers
User-Agent: Chrome/120.0
Accept: text/html
Accept-Language: en-IN
                                  ← Empty line
                                  ← Body (empty for GET)
```

### HTTP Response Structure

```
HTTP/1.1 200 OK                   ← Status Line
Content-Type: text/html           ← Headers
Content-Length: 1234
Date: Sat, 28 Mar 2026 10:00:00 GMT
                                  ← Empty line
<html>                            ← Body (the actual content)
  <body>Hello World!</body>
</html>
```

### HTTP Methods (Verbs)

> **Restaurant Analogy Continued:**

| Method | Purpose | Restaurant Analogy |
|--------|---------|-------------------|
| **GET** | Retrieve data | "Show me the menu" |
| **POST** | Submit data | "I'd like to place an order" |
| **PUT** | Update/Replace data | "Change my order to paneer" |
| **PATCH** | Partially update data | "Add extra spice to my order" |
| **DELETE** | Remove data | "Cancel my order" |
| **HEAD** | Get headers only (no body) | "Do you serve Chinese food?" (yes/no) |
| **OPTIONS** | Check what methods are allowed | "What services do you offer?" |

### HTTP Status Codes

Status codes tell the client what happened with their request.

| Code Range | Category | Meaning |
|-----------|----------|---------|
| **1xx** | Informational | "Hold on, I'm working on it" |
| **2xx** | Success | "Here you go!" |
| **3xx** | Redirection | "Look somewhere else" |
| **4xx** | Client Error | "You made a mistake" |
| **5xx** | Server Error | "I (server) messed up" |

#### Common Status Codes

| Code | Message | Meaning | When You See It |
|------|---------|---------|-----------------|
| **200** | OK | Request successful | Page loads normally |
| **201** | Created | New resource created | After form submission |
| **301** | Moved Permanently | Page has a new URL forever | Old URL redirects |
| **302** | Found (Temporary Redirect) | Page temporarily at another URL | Login redirects |
| **304** | Not Modified | Use cached version | Browser cache used |
| **400** | Bad Request | Request was malformed | Invalid form data |
| **401** | Unauthorized | Authentication required | Need to log in |
| **403** | Forbidden | You don't have permission | Restricted page |
| **404** | Not Found | Page doesn't exist | Typo in URL |
| **500** | Internal Server Error | Server crashed/bug | Server-side problem |
| **502** | Bad Gateway | Gateway/proxy got bad response | Server overloaded |
| **503** | Service Unavailable | Server temporarily down | Maintenance mode |

---

## 3. HTTP Versions

| Version | Year | Key Features |
|---------|------|-------------|
| **HTTP/0.9** | 1991 | Only GET method, no headers |
| **HTTP/1.0** | 1996 | Headers, status codes, content types |
| **HTTP/1.1** | 1997 | Persistent connections, chunked transfer, host header |
| **HTTP/2** | 2015 | Multiplexing, header compression, server push |
| **HTTP/3** | 2022 | Based on QUIC (UDP), faster connections |

### HTTP/1.1 vs HTTP/2 — Visual Comparison

```
HTTP/1.1 (One at a time):
Browser: ──request1──▶ ◀──response1── ──request2──▶ ◀──response2──

HTTP/2 (Multiplexing):
Browser: ──request1──▶ 
         ──request2──▶  ◀──response1──
         ──request3──▶  ◀──response2──
                        ◀──response3──
```

---

## 4. HTTPS — HyperText Transfer Protocol Secure

### What is HTTPS?

> **Analogy:** HTTP is like sending a **postcard** — anyone handling it can read the message. HTTPS is like sending a **sealed, locked envelope** — only the recipient has the key to open it.

**HTTPS** = HTTP + **TLS/SSL** encryption

| Feature | HTTP | HTTPS |
|---------|------|-------|
| **Full Form** | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
| **Port** | 80 | 443 |
| **Encryption** | None (plaintext) | TLS/SSL encrypted |
| **URL** | `http://` | `https://` |
| **Security** | Data can be intercepted | Data is encrypted end-to-end |
| **Certificate** | Not required | Requires SSL/TLS certificate |
| **Speed** | Slightly faster | Slightly slower (encryption overhead) |
| **SEO** | Not preferred | Preferred by Google |
| **Browser** | "Not Secure" warning | Lock icon (🔒) shown |

### How HTTPS Works (TLS Handshake)

```
Browser                                  Server
   │                                       │
   │────── ClientHello ───────────────────▶│  "I support these encryption methods"
   │                                       │
   │◀───── ServerHello + Certificate ──────│  "Let's use this one. Here's my ID."
   │                                       │
   │  (Browser verifies certificate        │
   │   with Certificate Authority)         │
   │                                       │
   │────── Key Exchange ──────────────────▶│  "Here's a shared secret (encrypted)"
   │                                       │
   │◀───── Finished ──────────────────────│  "Got it. Encryption active!"
   │                                       │
   │◀═══ ENCRYPTED DATA TRANSFER ═════════▶│
```

### SSL/TLS Certificates

- Issued by **Certificate Authorities (CAs)** like Let's Encrypt, DigiCert, Comodo
- Verify that a website is who it claims to be
- **Let's Encrypt** provides free certificates
- Certificates must be renewed periodically

---

## 5. Proxy Servers

### What is a Proxy Server?

> **Analogy:** A proxy server is like a **personal assistant** who makes calls on your behalf. When you want to call someone, your assistant dials the number, talks to the person, and gives you the message. The person on the other end only knows your assistant's number, not yours.

A **proxy server** acts as an intermediary between a client and a server.

```
Without Proxy:
Client ──────────────────────────▶ Server

With Proxy:
Client ──────▶ Proxy Server ──────▶ Server
Client ◀────── Proxy Server ◀────── Server
```

### Types of Proxy Servers

| Type | Direction | Purpose |
|------|-----------|---------|
| **Forward Proxy** | Client → Proxy → Server | Hides client identity, content filtering |
| **Reverse Proxy** | Client → Proxy → Server(s) | Load balancing, caching, security |
| **Transparent Proxy** | Client → Proxy → Server | Monitoring without client's knowledge |

### Benefits of Proxy Servers

| Benefit | Description |
|---------|-------------|
| **Privacy/Anonymity** | Hides client's real IP address |
| **Content Filtering** | Block certain websites (e.g., in schools/offices) |
| **Caching** | Store copies of frequently accessed pages for faster loading |
| **Load Balancing** | Distribute requests across multiple servers |
| **Logging/Monitoring** | Track internet usage |

### Real-World Example

> In your college computer lab, the network likely uses a **proxy server** that:
> - Blocks social media sites during class hours
> - Caches frequently accessed educational sites for faster access
> - Logs which sites are visited

---

## 6. Firewalls

### What is a Firewall?

> **Analogy:** A firewall is like a **security guard at a building entrance**. The guard has a list of who is allowed in and who is not. Every person (data packet) trying to enter must pass the guard's checks. Suspicious persons are turned away.

A **firewall** is a network security system that monitors and controls incoming and outgoing network traffic based on predefined security rules.

```
 Internet                Firewall               Internal Network
┌────────┐          ┌──────────────┐          ┌────────────────┐
│Allowed │──────────│              │──────────│                │
│Traffic │    ✅    │   Security   │    ✅    │  Your Devices  │
│        │──────────│    Rules     │──────────│                │
└────────┘          │              │          └────────────────┘
┌────────┐          │              │
│Blocked │───── ✖ ──│              │
│Traffic │          └──────────────┘
│(Hackers│
│ Malware│
│ etc.)  │
└────────┘
```

### Types of Firewalls

| Type | How It Works | Analogy |
|------|-------------|---------|
| **Packet-Filtering** | Checks each packet's header (source, destination, port) | Guard checks ID cards |
| **Stateful Inspection** | Tracks active connections, allows related packets | Guard remembers who came in and expects their return |
| **Application-Level** | Inspects packet content (not just headers) | Guard opens bags and checks contents |
| **Next-Gen (NGFW)** | Deep packet inspection + intrusion prevention | Guard with X-ray scanner + threat database |

### Firewall Rules — Examples

| Rule | Action | Description |
|------|--------|-------------|
| Allow port 80 inbound | ✅ ALLOW | Let web traffic in |
| Allow port 443 inbound | ✅ ALLOW | Let HTTPS traffic in |
| Block port 23 inbound | ❌ BLOCK | No Telnet (insecure) |
| Allow port 22 from admin IP | ✅ ALLOW | SSH only from trusted IP |
| Block all other inbound | ❌ BLOCK | Default deny |

### Software vs Hardware Firewalls

| Feature | Software Firewall | Hardware Firewall |
|---------|-------------------|-------------------|
| **Location** | Installed on individual device | Standalone device on network |
| **Example** | Windows Defender Firewall | Cisco ASA, pfSense |
| **Protection** | Single device | Entire network |
| **Cost** | Usually free (built into OS) | Can be expensive |

---

## Summary

| Concept | Key Takeaway |
|---------|-------------|
| HTTP | Text-based, stateless protocol for web communication (port 80) |
| HTTP Methods | GET (read), POST (create), PUT (update), DELETE (remove) |
| Status Codes | 2xx = success, 4xx = client error, 5xx = server error |
| HTTPS | HTTP + encryption (TLS/SSL) — secure communication (port 443) |
| Proxy Server | Intermediary between client and server — privacy, caching, filtering |
| Firewall | Security guard for network traffic — allows or blocks based on rules |

---

## Self-Assessment Questions

1. What does "stateless" mean in the context of HTTP?
2. What HTTP method would you use to submit a login form? Why?
3. What status code would a server return if the requested page doesn't exist?
4. Explain the difference between HTTP and HTTPS with a real-world analogy.
5. What is the role of a proxy server in a college network?
6. How does a firewall protect a network from unauthorized access?
7. You see a "502 Bad Gateway" error — what might have gone wrong?

---

## What's Next?

Unit 1 is complete! Starting **Day 6 (30 March)**, we begin **Unit 2: HTML Fundamentals** — where you'll write your very first web page. Make sure you have a text editor (VS Code recommended) and a web browser (Chrome) installed.

### Software to Install Before Day 6

| Software | Download Link | Purpose |
|----------|---------------|---------|
| **VS Code** | https://code.visualstudio.com | Code editor |
| **Google Chrome** | https://www.google.com/chrome | Web browser |
| **Git** | https://git-scm.com | Version control |

---

*Day 5 of 55 | Unit 1 — Internet Technology | Web Technology (25BCA060)*
