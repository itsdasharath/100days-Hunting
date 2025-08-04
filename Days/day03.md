# Bug Bounty Hunting – Day 3

## Race Conditions Vulnerability

## 🏁 Overview
Race conditions occur when multiple processes or threads access shared resources concurrently, and the final outcome depends on the timing of their execution. This can lead to unexpected behavior, data corruption, or security vulnerabilities. Attackers can exploit race conditions to gain unauthorized access, escalate privileges, or manipulate application logic.

## ⚙️ How It Works
Race conditions typically arise in scenarios where:
- Shared resources (e.g., files, databases) are not properly synchronized.
- Critical sections of code are not protected by locks or other synchronization mechanisms.
- User input is processed without adequate validation or sanitization.

In a race condition attack, an attacker may attempt to manipulate the timing of events to achieve a desired outcome, such as bypassing security controls or gaining access to restricted resources.

## 🛠 Tools & exploitation techniques

### [Detecting and exploiting limit overrun race conditions with Burp Repeater](https://portswigger.net/web-security/race-conditions#detecting-and-exploiting-limit-overrun-race-conditions-with-burp-repeater)
- Step 1: capture the request and send it to Burp Repeater.
- Step 2: modify the request to include a parameter that can be exploited (e.g., a file upload or transaction).
- Step 3: Duplicate the request using Ctrl+R to create multiple instances of the request.
- Step 4: Right-click on the request tab and select "Add tab to group -> Create a group" and select "single packet attack" .
- Step 5: Send the requests in quick succession.

### [Detecting and exploiting limit overrun race conditions with Turbo Intruder](https://portswigger.net/web-security/race-conditions#detecting-and-exploiting-limit-overrun-race-conditions-with-turbo-intruder)
- Step 1: Install Turbo Intruder from the BApp Store in Burp Suite.
- Step 2: Capture the request and send it to Turbo Intruder.
- Step 3: Modify the request to include a parameter that can be exploited (e.g., a file upload or transaction).
- Step 4: Select the "Single Packet Attack" option and modify the script in Turbo Intruder.
- Step 5: Run the attack to send multiple requests in quick succession.


## 🧪 Example Scenarios
1. **File Uploads**: An attacker uploads a malicious file while the application is processing a legitimate file, leading to code execution.
2. **Bank Transactions**: Two transactions are processed simultaneously, resulting in incorrect account balances.
3. **Session Fixation**: An attacker sets a user's session ID before the user logs in, allowing them to hijack the session.

## 🔐 Potential Impacts
- Unauthorized access to sensitive data or resources
- Data corruption or loss
- Privilege escalation
- Denial of service

## Articles
- **[Smashing the State Machine](https://portswigger.net/research/smashing-the-state-machine) - the true potential of web race conditions** ⚠️

## 📚 Practice & Learning Resources
- [PortSwigger - Race Conditions](https://portswigger.net/web-security/race-conditions)
- [OWASP - Race Conditions](https://owasp.org/www-community/attacks/Race_Condition)

## 🛡️ Prevention
To prevent race conditions:
1. **Use Proper Synchronization**: Implement locks, semaphores, or other synchronization mechanisms to protect shared resources.
2. **Validate User Input**: Ensure all user input is properly validated and sanitized before processing.
3. **Limit Concurrent Access**: Restrict access to critical sections of code to a single thread or process at a time.
4. **Implement Atomic Operations**: Use atomic operations for critical updates to shared resources.
5. **Monitor and Audit**: Regularly review code and system logs for signs of race condition vulnerabilities.

---

## 🎯 Happy Hunting! 👾
