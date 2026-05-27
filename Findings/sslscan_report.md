# **SSLScan Report**

---

## **Scan Details**

| Field | Details |
|-------|---------|
| **Target** | `demo.testfire.net` |
| **IP Address** | `65.61.137.117` |
| **Port** | `443` |
| **SNI Name** | `demo.testfire.net` |
| **Tool** | SSLScan v2.1.5 |
| **OpenSSL Version** | OpenSSL 3.5.4 (30 Sep 2025) |
| **Connection Status** | **Connected** |

---

## **Raw Scan Output**

```
sslscan demo.testfire.net
Version: 2.1.5
OpenSSL 3.5.4 30 Sep 2025

Connected to 65.61.137.117

Testing SSL server demo.testfire.net on port 443 using SNI name demo.testfire.net

SSL/TLS Protocols:
  SSLv2      disabled
  SSLv3      disabled
  TLSv1.0    disabled
  TLSv1.1    disabled
  TLSv1.2    disabled
  TLSv1.3    disabled

TLS Fallback SCSV:
  Connection failed - unable to determine TLS Fallback SCSV support

TLS Renegotiation:
  Session renegotiation not supported

TLS Compression:
  Compression disabled

Heartbleed:
  (no result returned)

Supported Server Cipher(s):
  Unable to parse certificate
  Unable to parse certificate
  Unable to parse certificate
  Unable to parse certificate

Certificate Information:
  Cannot be retrieved.
```

---

## **SSL/TLS Protocol Support**

| Protocol | Status | Security |
|----------|--------|----------|
| `SSLv2` | Disabled | ✅ Secure |
| `SSLv3` | Disabled | ✅ Secure |
| `TLSv1.0` | Disabled | ✅ Secure |
| `TLSv1.1` | Disabled | ✅ Secure |
| `TLSv1.2` | Disabled | ⚠️ Unexpected |
| `TLSv1.3` | Disabled | ⚠️ Unexpected |

---

## **Additional TLS Checks**

| Check | Result | Notes |
|-------|--------|-------|
| **TLS Fallback SCSV** | ⚠️ Unable to determine | Connection failed during test |
| **TLS Renegotiation** | Not supported | Reduces renegotiation attack risk |
| **TLS Compression** | Disabled | ✅ Protects against CRIME attack |
| **Heartbleed** | No result | Could not be confirmed or ruled out |

---

## **Certificate Information**

| Field | Status |
|-------|--------|
| Certificate Parsing | **Failed** — unable to parse |
| Certificate Details | **Cannot be retrieved** |
| Cipher Suites | **Unable to enumerate** |

---

## **Observations**

- **All SSL/TLS protocols are reported as disabled**, including `TLSv1.2` and `TLSv1.3` — this is **abnormal** and may indicate a **misconfigured SSL implementation** or scanning interference.
- **Certificate could not be parsed** — this prevents validation of expiry, issuer, CN, and trust chain.
- **Cipher suites could not be enumerated** — security of encryption in use is **unknown**.
- **Heartbleed status is inconclusive** — a manual verification is recommended.
- **TLS Fallback SCSV** support could not be determined — downgrade attack protection is unconfirmed.

---

## **Recommendations**

- **Investigate SSL/TLS configuration** — ensure at minimum `TLSv1.2` and `TLSv1.3` are enabled.
- **Resolve certificate parsing issues** — verify the certificate is valid, properly chained, and not expired.
- **Re-run SSLScan** after confirming port 443 is fully operational to obtain cipher suite details.
- **Manually verify Heartbleed** (`CVE-2014-0160`) using an alternative tool such as `testssl.sh`.
- **Disable weak cipher suites** once enumeration is possible and enforce strong ciphers only.
