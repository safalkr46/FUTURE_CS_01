# FUTURE_CS_01 – Security Assessment & Risk Analysis Report

This repository contains a passive vulnerability assessment conducted on the Altoro Mutual demo banking application as part of the **Future Interns Cyber Security Internship Program**.

---

## Internship Information

| Field | Details |
|-------|---------|
| **Internship Domain** | Cyber Security |
| **Organization** | Future Interns |
| **Task Code** | FUTURE_CS_01 |
| **Intern Name** | Safal Kumar Singh |

---

## Target Application

| Field | Details |
|-------|---------|
| **Application Name** | Altoro Mutual |
| **Target URL** | http://demo.testfire.net |
| **Assessment Type** | Passive Vulnerability Assessment |
| **Scope** | Read-Only / Non-Intrusive Testing |

---

## Tools Used

- OWASP ZAP
- Nmap
- Browser Developer Tools
- Curl
- SSLScan
- DNS Enumeration
- Canva

---

## Assessment Objectives

- Identify publicly observable security weaknesses
- Analyze HTTP security headers and configurations
- Classify vulnerabilities based on risk severity
- Provide remediation recommendations
- Develop professional cybersecurity reporting skills

---

## Key Findings

| Vulnerability | Severity |
|---------------|----------|
| Missing Content Security Policy Header | **Medium** |
| Missing Anti-Clickjacking Header | **Medium** |
| Cookie Without SameSite Attribute | **Medium** |
| Information Disclosure | **Low** |
| Missing X-Content-Type-Options Header | **Low** |

---

## Repository Structure

```
FUTURE_CS_01/
├── Findings/
│   ├── findings_summary.md
│   ├── risk_matrix.md
│   ├── headers.txt
│   └── sslscan.txt
├── Screenshots/
│   ├── zap-alerts.png
│   ├── finding-details.png
│   ├── curl-headers.png
│   └── sslscan.png
├── Report/
│   └── vulnerability-assessment-report.pdf
└── README.md
```

---

## Security Posture Score

| Category | Score |
|----------|-------|
| Security Headers | 5/10 |
| Cookie Security | 6/10 |
| Information Exposure | 7/10 |
| **Overall Security Posture** | **6/10** |

---

## Disclaimer

This assessment was conducted strictly for **educational and internship purposes** using passive and non-intrusive techniques only.

No exploitation, brute-force attacks, or destructive testing activities were performed during this assessment.

The target application is a publicly available demo application designed for cybersecurity learning and testing.

---

## Conclusion

The assessment identified several common web security misconfigurations related to HTTP security headers, cookie security, and information disclosure.

Although no critical vulnerabilities were identified during passive testing, implementing the recommended remediation measures would improve the application's overall security posture and resilience against common web-based attacks.
