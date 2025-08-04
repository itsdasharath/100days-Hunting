# 🗓️ Bug Bounty Hunting – Day 6

Today’s recon led me to an old, forgotten server that wasn’t listed in the official scope of my target. While I couldn’t report the issues due to scope limitations, I still spent a few hours testing it and uncovered multiple interesting vulnerabilities — including ways to bypass the Web Application Firewall (WAF).

Although out of scope, it turned into a solid hands-on session and gave me good practice in real-world bypass techniques.

Later, I dedicated time to learning about **Subdomain Takeover** — focusing on how misconfigured DNS records and abandoned services can be exploited. This is an area I definitely want to get more proficient in.

📖 Reference:  
[👉 A Guide to Subdomain Takeovers – HackerOne](https://www.hackerone.com/blog/guide-subdomain-takeovers-20)

---

### ⏱️ Time Spent Today

- 🔍 Hunting (Recon + Testing): **4 hours**
- 📚 Learning (Subdomain Takeover): **3 hours**

---

### 🧠 Reflection

Even though today’s target wasn’t in scope, it was a valuable learning experience. Practicing WAF bypass and deepening my knowledge in subdomain takeover is going to pay off when I encounter these scenarios on valid targets.

---

### 🛡️ Notes on WAF Bypass

The WAF in front of the forgotten server was blocking direct access to several interesting endpoints. I used the following techniques to bypass it:

- Modified headers like `X-Original-URL`, `X-Forwarded-For`, `X-Real-IP`
- Played with HTTP verb tampering (`GET`, `POST`, `HEAD`)
- Added unconventional paths and encodings (`..;/`, `%2e`, double slashes `//`)
- Used IP-based access via internal subdomains

Although the bypass worked and led to useful information, the server was not in scope — so no report was filed. Still, this gave me hands-on insight into bypassing layered defenses.

---

## 🎯 Happy Hunting! 👾