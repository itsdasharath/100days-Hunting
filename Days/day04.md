# 🗓️ Bug Bounty Hunting – Day 4

Today marked a turning point in my bug bounty journey — I finally selected my target for hunting. This gave my efforts a sense of direction and allowed me to begin one of the most crucial steps: **reconnaissance and information gathering**. This phase is like the foundation of any good hunt — the better the recon, the better the chance to find something valuable.

# Reconnaissance/Information Gathering

## 🏁 Overview 

Reconnaissance is all about mapping the attack surface. Think of it as gathering every little breadcrumb related to your target before planning the actual attack. You want to understand the domains, subdomains, IP space, tech stack, leaked data, and more. Here's how I approached it:

---

## 🧰 Tools and Techniques Used

### 🔍 Subdomain Enumeration

- **Amass** – Automated OSINT-based tool for wide subdomain discovery.
- **Subfinder** – Fast passive subdomain enumerator using a variety of sources.
- **crt.sh** – Scraped certificate transparency logs to find domains.

### 🌐 Domain & DNS Recon

- **WHOIS Lookup** – To gather domain ownership, registration dates, and name servers.
- **DNSDumpster** – Visual DNS mapping.
- **dig** / **nslookup** – Manual inspection of DNS records (A, NS, MX, TXT, etc).
- **Examine ASN** – Analyzed Autonomous System Numbers to determine IP ranges used by the target.

### 📚 Open Source Intelligence (OSINT)

- **Google Dorking** – Used advanced search operators for sensitive file discovery and exposed endpoints.
- **Shodan** – Discovered internet-exposed services and open ports.
- **Censys** – Similar to Shodan, but with a focus on certificate data and metadata.
- **GitHub** – Searched for accidentally committed secrets, API keys, or config files.
- **Wayback Machine** – Fetched historical snapshots of the website to discover deprecated or hidden paths.

---

## 📂 Asset Discovery

- **Gobuster** – Performed directory brute-forcing using wordlists.
  - Found several **403 Forbidden** responses which may contain valuable content behind weak protection.
- **Assetfinder** – Used this tool to automate asset discovery and enumeration.

---

## 🚪 403 Bypass Attempts

- 🔄 **Burp Suite** – Modified request headers like `X-Original-URL`, `X-Forwarded-For`, `X-Rewrite-URL` to try bypassing.
- 🧩 **403bypasser** – Used this script: [iamj0ker/bypass-403](https://github.com/iamj0ker/bypass-403.git) for automated attempts.

---

## 🎯 Happy Hunting! 👾
