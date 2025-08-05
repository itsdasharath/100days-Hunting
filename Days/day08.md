# 🗓️ Bug Bounty Hunting – Day 8

Focused entirely on recon and active testing today.

While enumerating IPs, I discovered one exposing an API endpoint. After probing it, I realized it didn’t return any meaningful data — likely an old or abandoned integration with a third-party service previously used by the target. Still, it was worth exploring for potential leftovers or indirect attack surfaces.

I also went deeper into reconnaissance using several tools to expand my understanding of the environment and find more entry points.

---

### 🧰 Tools Used

- **ffuf** – For content discovery on identified hosts and subdomains  
- **nmap** – For port scanning and service fingerprinting  
- **nuclei** – For quick vulnerability scanning using community templates  
- **gobuster** – For brute-forcing directories and virtual hosts  
- **whatweb** – For identifying technologies used on web servers

---

### 📚 Notable Find

🧠 GitHub Repo: [GrrrDog/weird_proxies](https://github.com/GrrrDog/weird_proxies/tree/master?tab=readme-ov-file)  
This repo showcases unconventional proxy headers and WAF bypass tricks. A great resource for creative thinking when dealing with filtered endpoints, CDN protections, or reverse proxies.

---

### ⏱️ Time Spent Today

- 🔍 Hunting & Recon: **8 hours**
- 📚 Learning (weird_proxies repo): **30 minutes**

---

### 🧠 Reflection

Even though the API turned out to be inactive, it revealed how old integrations or third-party services can expand a target’s footprint. Combined with active tool-based recon and discovering the proxy tricks repo, today felt productive from a recon strategy standpoint.

---

## 🎯 Happy Hunting! 👾
