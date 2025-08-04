# 🗓️ Bug Bounty Hunting – Day 5

Did some more reconnaissance on my current bug bounty target and found a few important things that will help narrow down the attack surface in the coming days.

After finishing recon, I shifted my focus to learning and spent the rest of the day working on authentication-related vulnerabilities using PortSwigger Web Security Academy. These hands-on labs helped me understand how login systems can be broken, bypassed, or abused through weak logic.

---

### ⏱️ Time Spent Today

- 🔍 Hunting (Recon): **1 hour**
- 📚 Learning (Auth Vulns via PortSwigger): **8 hours**

---

# 🔐 Authentication Vulnerabilities – Lab Summaries

These are the labs I completed today. This section serves as a personal reference in case I need to revisit the techniques or scenarios in the future.

---

###  Username Enumeration via Different Responses (Apprentice)

**Scenario:**  
The login form returns noticeably different responses depending on whether the username is valid or not.

**Technique:**  
- Submitted usernames via Burp Repeater.
- Compared response content and status codes.
- Valid usernames returned a different message or redirect behavior.

---

###  2FA Simple Bypass (Apprentice)

**Scenario:**  
There is a two-factor authentication step after login, but it's not properly enforced for all users.

**Technique:**  
- Logged in with a known user (`wiener`) and captured the request flow.
- Found that logging in as `carlos` skipped the 2FA step.
- Manually manipulated the session to access the target account without the second factor.

---

###  Password Reset Broken Logic (Apprentice)

**Scenario:**  
Password reset functionality doesn’t validate the reset token against the requesting user.

**Technique:**  
- Requested password reset for my own user and captured the token.
- Used that same token to reset the password for another user (`carlos`).
- Successfully gained access to the target account.

---

###  Username Enumeration via Subtly Different Responses (Practitioner)

**Scenario:**  
The application attempts to hide username validity, but small variations in responses reveal user existence.

**Technique:**  
- Used Burp Intruder with a list of usernames.
- Looked for differences in grammar, response length, or phrasing.
- Identified valid usernames by analyzing these subtle variations.

---

###  Username Enumeration via Response Timing (Practitioner)

**Scenario:**  
Login response times differ slightly for valid vs invalid usernames.

**Technique:**  
- Sent multiple login attempts while monitoring response time.
- Valid usernames took noticeably longer to respond (~100ms+ delay).
- Used this timing to identify valid accounts.

---

###  Broken Brute-Force Protection: IP Block (Practitioner)

**Scenario:**  
The system blocks brute-force attempts from the same IP address.

**Technique:**  
- Brute-forced until IP block occurred.
- Bypassed rate limiting using the `X-Forwarded-For` header to spoof IPs.
- Continued brute-forcing without triggering detection.

---

###  Username Enumeration via Account Lock (Practitioner)

**Scenario:**  
Accounts get locked only when valid usernames are used with repeated incorrect passwords.

**Technique:**  
- Sent multiple failed login attempts for different usernames.
- Only valid accounts showed an “account locked” message.
- Used this difference to enumerate existing users.

---

### 🧠 Reflection

Today was more about leveling up knowledge than actively hunting. Understanding authentication flaws like 2FA bypass, account lock misuse, and response-based enumeration is vital. These are common in real-world apps, and I feel more confident tackling them on live targets now.

---

## 🎯 Happy Hunting! 👾
