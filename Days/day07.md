# 🗓️ Bug Bounty Hunting – Day 7

Today was fully dedicated to one core objective: **Subdomain Takeover**.

I discovered a subdomain that appeared vulnerable to takeover. I spent most of the day building a proper **Proof of Concept (PoC)** and documenting everything — including the DNS misconfiguration, service validation, and how the takeover could be exploited.

After thorough testing, I submitted the vulnerability to the responsible company via their disclosure program and am currently waiting for a response.

---

### 📚 Learning & Research

To solidify my understanding, I read real-world subdomain takeover reports and watched YouTube videos that explain various exploitation techniques and DNS behavior in practical scenarios.

#### HackerOne Reports I Studied:
- [Takeover via Azure (H1 Report #1474784)](https://hackerone.com/reports/1474784)
- [GitHub Pages Subdomain Takeover (H1 Report #1717626)](https://hackerone.com/reports/1717626)
- [Subdomain Takeover via Unclaimed S3 Bucket (H1 Report #202767)](https://hackerone.com/reports/202767)

#### Video Learning:
- Scrolled through multiple YouTube videos to understand how real researchers perform subdomain takeover in live bounty programs.
- Focused on PoC creation, DNS misconfig basics, service claim processes, and detection logic.

---

### ⏱️ Time Spent Today

- 📌 Exploitation + Reporting (Subdomain Takeover): **6 hours**
- 📚 Deep Learning (Reports + YouTube): **4 hours**

---

### 🧠 Reflection

Today felt productive and practical. Found a real subdomain takeover vulnerability, exploited it responsibly, and submitted a well-documented report. Reading past H1 writeups and watching videos added clarity and strengthened my workflow for similar bugs in the future.

---

## 🎯 Happy Hunting! 👾