# **Nmap Scan Report**

---

## **Scan Details**

| Field | Details |
|-------|---------|
| **Target** | `demo.testfire.net` |
| **Resolved IP** | `65.61.137.117` |
| **Tool** | Nmap 7.95 |
| **Date & Time** | 2026-05-23 at 20:59 IST |
| **Host Status** | **Up** (latency: 0.098s) |

---

## **Raw Scan Output**

```
nmap demo.testfire.net
Starting Nmap 7.95 (https://nmap.org) at 2026-05-23 20:59 IST
Nmap scan report for demo.testfire.net (65.61.137.117)
Host is up (0.098s latency).
Not shown: 997 filtered top ports (no-response)

PORT      STATE  SERVICE
80/tcp    open   http
443/tcp   open   https
8080/tcp  open   http-proxy

Nmap done: 1 IP address (1 host up) scanned in 16.92 seconds
```

---

## **Open Ports**

| Port | State | Service | Notes |
|------|-------|---------|-------|
| `80/tcp` | Open | HTTP | **Unencrypted** web traffic |
| `443/tcp` | Open | HTTPS | Encrypted web traffic |
| `8080/tcp` | Open | HTTP Proxy | **Non-standard port** — may expose proxy service |

---

## **Observations**

- **Port 80 (HTTP)** is open — unencrypted traffic may expose sensitive data in transit.
- **Port 8080 (HTTP Proxy)** is open — should be reviewed for **unauthorized access or misconfiguration**.
- **997 ports** were filtered, indicating a **firewall is active**.
- No critical high-risk ports (e.g., `22`, `3306`, `3389`) were detected in this basic scan.

---

## **Recommendations**

- **Disable Port 80** or enforce a redirect to HTTPS (`443`).
- **Review Port 8080** — restrict access if not required publicly.
- Conduct a **full port scan** (`-p-`) for comprehensive coverage.
