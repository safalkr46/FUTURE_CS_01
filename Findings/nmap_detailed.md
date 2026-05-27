# **Nmap Detailed Scan Report**

---

## **Scan Details**

| Field | Details |
|-------|---------|
| **Target** | `demo.testfire.net` |
| **Resolved IP** | `65.61.137.117` |
| **Tool** | Nmap 7.95 |
| **Flags Used** | `-sV -A` (Service & Version Detection + Aggressive Scan) |
| **Date & Time** | 2026-05-23 at 21:02 IST |
| **Host Status** | **Up** (latency: 0.092s) |
| **Scan Duration** | 255.20 seconds |
| **Network Distance** | 2 hops |

---

## **Raw Scan Output**

```
nmap -sV -A demo.testfire.net
Starting Nmap 7.95 (https://nmap.org) at 2026-05-23 21:02 IST
Nmap scan report for demo.testfire.net (65.61.137.117)
Host is up (0.092s latency).
Not shown: 997 filtered top ports (no-response)

PORT      STATE  SERVICE   VERSION
80/tcp    open   http      Apache Tomcat/Coyote JSP engine 1.1
443/tcp   open   ssl/https?
8080/tcp  open   http      Apache Tomcat/Coyote JSP engine 1.1

Warning: OSScan results may be unreliable because we could not find
at least 1 open and 1 closed port.
OS fingerprint not ideal because: Missing a closed TCP port so results incomplete
No OS matches for host

Network Distance: 2 hops

TRACEROUTE (using port 80/tcp)
HOP  RTT       ADDRESS
1    -
2    15.47 ms  65.61.137.117

Nmap done: 1 IP address (1 host up) scanned in 255.20 seconds
```

---

## **Open Ports & Services**

| Port | State | Service | Version | Notes |
|------|-------|---------|---------|-------|
| `80/tcp` | Open | HTTP | Apache Tomcat/Coyote JSP 1.1 | **Unencrypted** — plaintext traffic |
| `443/tcp` | Open | SSL/HTTPS | Unknown | SSL service detected; version unclear |
| `8080/tcp` | Open | HTTP | Apache Tomcat/Coyote JSP 1.1 | **Non-standard port** — proxy/alternate HTTP |

---

## **Service & Version Findings**

### **Apache Tomcat / Coyote JSP Engine 1.1**

- Identified on **ports 80 and 8080**.
- `Apache Tomcat/Coyote JSP engine 1.1` is an **outdated version** — known to have multiple CVEs.
- Version disclosure through service banners is an **information exposure risk**.

---

## **OS Detection**

| Field | Result |
|-------|--------|
| OS Fingerprint | **Inconclusive** |
| Reason | Missing a closed TCP port — results incomplete |
| OS Match | **None found** |

---

## **Traceroute**

| Hop | RTT | Address |
|-----|-----|---------|
| 1 | — | (filtered / no response) |
| 2 | 15.47 ms | `65.61.137.117` |

---

## **Observations**

- **Port 80** is open and serving unencrypted HTTP — sensitive data may be exposed in transit.
- **Port 8080** is publicly accessible — should be reviewed for necessity and access controls.
- **Apache Tomcat version 1.1** is outdated and may be vulnerable to known exploits.
- **Banner grabbing** succeeded — server version is visible to attackers, aiding reconnaissance.
- **SSL on port 443** could not be fully fingerprinted — further SSL testing recommended.

---

## **Recommendations**

- **Disable Port 80** or enforce an HTTP → HTTPS redirect.
- **Restrict Port 8080** — limit access via firewall rules if not required publicly.
- **Update Apache Tomcat** to the latest stable version to patch known vulnerabilities.
- **Suppress server banners** to prevent version disclosure (`ServerTokens Prod` in config).
- Perform a **targeted SSL/TLS scan** on port 443 for cipher and certificate analysis.
