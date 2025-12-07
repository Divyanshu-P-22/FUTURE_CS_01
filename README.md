# OWASP Juice Shop - Web Application Security Assessment

![Security Assessment](https://img.shields.io/badge/Security-Assessment-red)
![OWASP](https://img.shields.io/badge/OWASP-Juice%20Shop-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📋 Project Overview

This repository contains the complete security assessment documentation for the **OWASP Juice Shop** web application. As part of a hands-on cybersecurity internship project, I performed comprehensive vulnerability assessment and penetration testing to identify critical security flaws using ethical hacking tools and OWASP standards.

**Assessment Date:** December 1-4, 2025  
**Target Application:** https://juice-shop.herokuapp.com  
**Assessed by:** Divyanshu Prajapat
**Overall Risk Rating:** CRITICAL ⚠️

---

## 🎯 Project Objectives

✅ Identify and document real-world web application vulnerabilities  
✅ Test for OWASP Top 10 security threats  
✅ Use industry-standard penetration testing tools  
✅ Create professional security documentation  
✅ Provide actionable remediation recommendations  

---

## 📁 Repository Contents

This repository includes three comprehensive documents:

### 1️⃣ Security Assessment Report
**File:** `OWASP Juice Shop - Security Assessment Report - Dec 2025.pdf`

**Description:**  
Complete penetration testing report with detailed findings, impact analysis, and remediation strategies.

**Contents:**
- Executive Summary
- 5 Critical Vulnerabilities Identified:
  - SQL Injection (CVSS 9.8)
  - Cross-Site Scripting - XSS (CVSS 7.3)
  - Broken Access Control (CVSS 9.1)
  - Sensitive Data Exposure (CVSS 8.2)
  - Security Misconfiguration (CVSS 6.5)
- Proof of Concept with Screenshots
- Impact Assessment
- Detailed Remediation Steps
- Code Fix Examples

**Key Findings:**
- Authentication bypass via SQL injection
- XSS vulnerability in search function
- Admin panel accessible without authentication
- Sensitive files exposed through FTP directory
- Error messages revealing system information

---

### 2️⃣ OWASP Top 10 Compliance Checklist
**File:** `OWASP Top 10 Compliance Checklist - Juice Shop.pdf`

**Description:**  
Comprehensive compliance assessment mapping all discovered vulnerabilities to the OWASP Top 10 (2021) framework.

**Contents:**
- A01:2021 - Broken Access Control ✓
- A02:2021 - Cryptographic Failures ✓
- A03:2021 - Injection ✓
- A04:2021 - Insecure Design ✓
- A05:2021 - Security Misconfiguration ✓
- A06:2021 - Vulnerable and Outdated Components
- A07:2021 - Identification and Authentication Failures ✓
- A08:2021 - Software and Data Integrity Failures
- A09:2021 - Security Logging and Monitoring Failures ✓
- A10:2021 - Server-Side Request Forgery (SSRF)

**Compliance Summary:**
- **Critical Issues:** 2 vulnerabilities
- **High Risk Issues:** 2 vulnerabilities  
- **Medium Risk Issues:** 1 vulnerability

---

### 3️⃣ Security Testing Tools & Logs
**File:** `OWASP Juice Shop - Security Testing Tools & Logs.pdf`

**Description:**  
Detailed logs from all security testing tools used during the assessment, including configurations, commands, and raw output.

**Tools Used:**

1. **Burp Suite Professional**
   - Web vulnerability scanner
   - SQL injection and XSS testing
   - Request/Response logs
   - Scanner findings

2. **OWASP ZAP (Zed Attack Proxy)**
   - Automated security scanning
   - Active scan results
   - 23 total alerts (High: 5, Medium: 8, Low: 10)

3. **SQLMap**
   - Automated SQL injection testing
   - Database enumeration
   - Schema extraction

4. **Nikto**
   - Web server vulnerability scanner
   - Security header analysis
   - Directory exposure detection

5. **Nmap**
   - Port scanning
   - Service detection
   - Version identification

6. **Gobuster/Dirb**
   - Directory brute forcing
   - Hidden endpoint discovery

7. **Browser Developer Tools**
   - Client-side analysis
   - JavaScript inspection
   - Local storage examination

8. **Postman**
   - API security testing
   - Authentication bypass testing
   - Rate limiting analysis

---

## 🛡️ Key Vulnerabilities Discovered

### Critical Severity

#### 1. SQL Injection - Authentication Bypass
- **CVSS Score:** 9.8
- **Location:** Login form (/rest/user/login)
- **Payload:** `admin@juice-sh.op' OR 1=1--`
- **Impact:** Complete authentication bypass, unauthorized admin access

#### 2. Broken Access Control
- **CVSS Score:** 9.1
- **Location:** Admin panel (/administration)
- **Impact:** Direct access to admin functionality without authentication

#### 3. Sensitive Data Exposure
- **CVSS Score:** 8.2
- **Location:** FTP directory (/ftp)
- **Impact:** Access to confidential files and system information

### High Severity

#### 4. Cross-Site Scripting (XSS)
- **CVSS Score:** 7.3
- **Location:** Search function (/rest/products/search)
- **Payload:** `<iframe src="javascript:alert('XSS')">`
- **Impact:** Cookie theft, session hijacking, client-side attacks

### Medium Severity

#### 5. Security Misconfiguration
- **CVSS Score:** 6.5
- **Location:** Error handling
- **Impact:** Information disclosure through detailed error messages

---

## 🔧 Tools & Technologies

**Testing Environment:**
- Target: OWASP Juice Shop (Node.js application)
- Testing OS: Kali Linux / Windows
- Browser: Chrome with Developer Tools

**Security Tools:**
- Burp Suite Professional
- OWASP ZAP 2.14.0
- SQLMap
- Nikto v2.5.0
- Nmap 7.94
- Gobuster v3.6
- Postman

**Documentation:**
- Google Docs
- Markdown
- Screenshot tools

---

## 📊 Risk Assessment Summary

| Severity | Count | Percentage |
|----------|-------|------------|
| 🔴 Critical | 3 | 60% |
| 🟠 High | 2 | 40% |
| 🟡 Medium | 0 | 0% |
| **Total** | **5** | **100%** |

**Risk Rating:** CRITICAL

**Recommendation:** Immediate remediation of all CRITICAL and HIGH severity vulnerabilities is strongly recommended before the application handles production data or customer information.

---

## 🎓 Skills Demonstrated

✅ Web Application Vulnerability Scanning  
✅ Penetration Testing Methodologies  
✅ OWASP Top 10 Knowledge  
✅ Security Tool Proficiency  
✅ Vulnerability Documentation  
✅ Risk Assessment & Analysis  
✅ Technical Report Writing  
✅ Ethical Hacking Techniques  

---

## 🔒 Remediation Recommendations

### Immediate Actions (Priority 1)

1. **SQL Injection Prevention**
   - Implement parameterized queries/prepared statements
   - Use ORM frameworks (Sequelize, TypeORM)
   - Apply input validation and sanitization

2. **Access Control**
   - Implement proper authentication checks on admin routes
   - Apply role-based access control (RBAC)
   - Verify user permissions on every request

3. **XSS Protection**
   - Implement output encoding
   - Add Content Security Policy (CSP) headers
   - Sanitize all user inputs

### Security Hardening (Priority 2)

4. **Security Headers**
   ```
   X-XSS-Protection: 1; mode=block
   X-Content-Type-Options: nosniff
   Content-Security-Policy: default-src 'self'
   Strict-Transport-Security: max-age=31536000
   ```

5. **Session Management**
   - Store tokens in httpOnly, secure cookies
   - Implement token expiration
   - Add refresh token mechanism

6. **Additional Controls**
   - Implement rate limiting
   - Add account lockout after failed attempts
   - Enable comprehensive logging and monitoring

---

## 📚 Learning Resources

- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [OWASP Top 10 - 2021](https://owasp.org/Top10/)
- [Web Security Academy](https://portswigger.net/web-security)
- [Burp Suite Documentation](https://portswigger.net/burp/documentation)
- [OWASP ZAP User Guide](https://www.zaproxy.org/docs/)

---

## 🤝 About This Project

This security assessment was conducted as part of a cybersecurity internship project to develop practical penetration testing skills and understand real-world web application vulnerabilities. The project demonstrates:

- Professional security assessment methodologies
- Industry-standard tool usage
- Comprehensive documentation practices
- Understanding of OWASP security standards
- Ethical hacking and responsible disclosure

---

## 📝 Disclaimer

⚠️ **Important:** This security assessment was conducted on OWASP Juice Shop, an intentionally vulnerable application designed for security training purposes. All testing was performed in a legal and ethical manner on a publicly available training application.

**DO NOT** attempt these techniques on:
- Production systems
- Applications you don't have permission to test
- Any system without proper authorization

Unauthorized penetration testing is illegal and unethical.

---

## 📬 Contact

**Divyanshu Prajapat**  
Cybersecurity Student | Third Year  
GitHub: [@Divyanshu-P-22](https://github.com/Divyanshu-P-22)

---

## 📄 License

This documentation is provided for educational purposes. Please respect intellectual property and use responsibly.

---

⭐ **If you found this security assessment helpful, please consider giving it a star!**

---
