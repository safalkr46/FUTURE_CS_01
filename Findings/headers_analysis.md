# **HTTP Headers Analysis**

---

## **Target**

| Field | Details |
|-------|---------|
| **URL** | `http://demo.testfire.net` |
| **Date** | Sat, 23 May 2026 |
| **Tool Used** | `curl -I` |

---

## **Raw Response Headers**

```
HTTP/1.1 200 OK
Server: Apache-Coyote/1.1
Set-Cookie: JSESSIONID=22F662541337A6D4837EE979E136D3AD; Path=/; HttpOnly
Content-Type: text/html;charset=ISO-8859-1
Transfer-Encoding: chunked
Date: Sat, 23 May 2026 15:25:45 GMT
```

---

## **Header Analysis**

### **Present Headers**

| Header | Value | Notes |
|--------|-------|-------|
| `Server` | `Apache-Coyote/1.1` | **Information disclosure** — server version exposed |
| `Set-Cookie` | `JSESSIONID=...; Path=/; HttpOnly` | `HttpOnly` present, but **`Secure` and `SameSite` missing** |
| `Content-Type` | `text/html;charset=ISO-8859-1` | Standard content type |

---

### **Missing Security Headers**

| Missing Header | Risk |
|----------------|------|
| `Content-Security-Policy` | Exposure to **XSS** and script injection |
| `X-Frame-Options` | Vulnerable to **clickjacking** |
| `X-Content-Type-Options` | Vulnerable to **content-sniffing** |
| `Strict-Transport-Security` | No enforced **HTTPS** |

---

## **Observations**

- **`Secure` flag** is missing from the cookie — session ID may be transmitted over **HTTP**.
- **`SameSite` attribute** is absent — increases risk of **CSRF attacks**.
- **Server header** reveals `Apache-Coyote/1.1`, which aids **attacker reconnaissance**.
