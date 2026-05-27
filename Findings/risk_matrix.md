# **Risk Classification Matrix**

---

## **Overview**

This matrix maps all identified findings to their **severity level** and corresponding **OWASP Top 10** category.

---

## **Risk Matrix**

| # | Finding | Severity | OWASP Mapping |
|---|---------|----------|---------------|
| 1 | Missing Content Security Policy (CSP) Header | **Medium** | A05: Security Misconfiguration |
| 2 | Missing Anti-Clickjacking Header | **Medium** | A05: Security Misconfiguration |
| 3 | Cookie Without SameSite Attribute | **Medium** | A07: Identification and Authentication Failures |
| 4 | Information Disclosure | **Low** | A05: Security Misconfiguration |
| 5 | Missing X-Content-Type-Options Header | **Low** | A05: Security Misconfiguration |

---

## **Severity Summary**

| Severity | Count |
|----------|-------|
| 🔴 High | 0 |
| 🟠 Medium | 3 |
| 🟡 Low | 2 |
| 🟢 Informational | 0 |

---

## **OWASP Category Breakdown**

| OWASP Category | Findings Mapped |
|----------------|-----------------|
| **A05: Security Misconfiguration** | Missing CSP Header, Missing Anti-Clickjacking Header, Information Disclosure, Missing X-Content-Type-Options |
| **A07: Identification and Authentication Failures** | Cookie Without SameSite Attribute |

---

## **Notes**

- The majority of findings fall under **A05: Security Misconfiguration**, indicating a need for **security hardening** of HTTP response headers.
- **A07** finding highlights a **session management weakness** that could facilitate session-based attacks.
- No **Critical** or **High** severity issues were identified in this assessment scope.
