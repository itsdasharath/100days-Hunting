# Bug Bounty Hunting – Day 2

## Information Disclosure vulnerability

## 🕵️ Overview
Information disclosure vulnerabilities occur when an application unintentionally exposes sensitive information to unauthorized users. This can include configuration files, source code, database dumps, or any other data that should not be publicly accessible. Such vulnerabilities can lead to further attacks, including credential theft, system compromise, or data breaches.

## ⚙️ How It Works
Information disclosure often arises from:
- Misconfigurations
- Inadequate access controls
- Improperly sanitized user input
- Debugging features left enabled in production

These flaws allow attackers to access internal files, system behavior, or user-specific content that should remain hidden.

## 🧪 Example URLs
```
https://target.com/robots.txt
https://target.com/backup.zip
https://target.com/config.php
```

## 🗂️ Common Sources of Information Disclosure

- **Files for web crawlers** — e.g., `robots.txt`, `sitemap.xml`
- **Directory listings** — e.g., `https://target.com/uploads/` (when index browsing is enabled)
- **Developer comments in HTML** — e.g., `<!-- TODO: Remove debug credentials -->`
- **Verbose error messages** — Exposing stack traces or server info
- **Debugging pages** — `/debug`, `/phpinfo`, `/server-status`
- **User account pages** — IDOR or improper access control (e.g., `/user/profile?id=admin`)
- **Backup files** — e.g., `config.php~`, `db_backup.sql`, `site.zip`
- **Sensitive config files** — `.env`, `config.json`, `credentials.yml`
- **Insecure configuration files** — Open access to admin dashboards or internal APIs
- **Version control leaks** — `.git/`, `.svn/`, `.hg/`, containing full code history

## 🔐 Potential Impacts
- Disclosure of passwords, API keys, or database credentials
- Reconnaissance for further attacks (like LFI, SQLi, RCE)
- Exposure of business logic or application internals
- Full source code leakage

## 📚 Practice & Learning Resources
- [PortSwigger – Information Disclosure Vulnerabilities](https://portswigger.net/web-security/information-disclosure)

## 🛡️ Prevention

To prevent information disclosure vulnerabilities:

1. **Disable Directory Listings**
   - Ensure directory indexing is turned off on the web server (`Options -Indexes` in Apache or `autoindex off;` in Nginx).

2. **Restrict Access to Sensitive Files**
   - Use `.htaccess` or server config to block access to files like `.env`, `.git`, `config.php`, `backup.zip`.

3. **Sanitize and Validate Input**
   - Do not return file contents, debug data, or stack traces based on user input.
   - Ensure proper access control on user-specific resources.

4. **Remove Developer Artifacts**
   - Strip comments, test scripts, and backup/config files before deploying to production.
   - Remove `.git/`, `.svn/`, `.bak`, `.old`, and `.zip` files from publicly accessible directories.

5. **Disable Verbose Error Messages**
   - Show generic error messages to users; log detailed ones internally.
   - Turn off `display_errors` in PHP, and equivalent settings in other languages/frameworks.

6. **Secure Configuration**
   - Disable debug mode in production (e.g., `DEBUG=False` in Django).
   - Remove or protect access to debugging pages like `/phpinfo`, `/server-status`.

7. **Use Strong Access Controls**
   - Ensure proper authentication and authorization checks for all sensitive resources and endpoints.

8. **Monitor and Audit**
   - Use tools like Burp Suite, Nikto, or automated scanners to discover exposed files and information leaks.
   - Regularly audit your source and deployment files for accidentally exposed data.

---

## 🎯 Happy Hunting! 👾
