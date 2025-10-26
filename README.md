# 🧱 Firewall Configuration and Traffic Filtering  
**By:** Vivek Agrawal  
**Date:** October 26, 2025  
**Tool Used:** UFW (Uncomplicated Firewall), Netcat (nc)  
**Environment:** Kali Linux 2024.x  

---

## 🎯 Objective
To configure and test basic firewall rules on **Kali Linux** using **UFW (Uncomplicated Firewall)** and understand how inbound and outbound traffic can be filtered for better network security.

---

## 🧰 Tools Used
- **Kali Linux 2024.x**  
- **UFW (Uncomplicated Firewall)** — front-end for iptables  
- **Netcat (nc)** — used to verify whether specific ports are open or blocked  

---

## ⚙️ Steps & Commands Executed
```bash
# Enable and verify UFW
sudo ufw enable
sudo ufw status verbose

# Block insecure Telnet port (23)
sudo ufw deny 23/tcp

# Allow secure SSH port (22)
sudo ufw allow 22/tcp

# View all configured rules
sudo ufw status numbered

# Test connectivity
nc -zv 127.0.0.1 23    # Should show "Connection refused"
nc -zv 127.0.0.1 22    # Should show "Connection succeeded"

# Remove the test rule
sudo ufw delete deny 23/tcp
```

---

## 🧩 Findings

| Test Case            | Expected Behaviour     | Observed Result                 | Conclusion                  |
| -------------------- | ---------------------- | ------------------------------- | --------------------------- |
| Before enabling UFW  | All ports open locally | Connection on port 23 succeeded | Unfiltered traffic          |
| After `deny 23/tcp`  | Port 23 blocked        | `Connection refused`            | Telnet successfully blocked |
| After `allow 22/tcp` | SSH allowed            | `Connection succeeded`          | Selective allow verified    |
| After deleting rule  | Port 23 open again     | Connection restored             | Rule removal effective      |

---

## 📊 Summary of Findings
- UFW correctly blocked and allowed traffic based on defined rules.  
- Blocking port 23 prevented insecure Telnet connections.  
- Allowing port 22 enabled secure SSH access.  
- Demonstrated that UFW simplifies complex `iptables` rule management.  

---

## 🧠 Learnings
- Understood **inbound vs outbound** traffic control.  
- Practiced adding, deleting, and verifying firewall rules using UFW.  
- Observed the immediate impact of firewall policies on network behavior.  
- Reinforced the **principle of least privilege** for secure configurations.  

---

## 💬 Interview Prep – Quick Answers

| Question                                  | Answer                                                                                 |
| ----------------------------------------- | -------------------------------------------------------------------------------------- |
| **What is a firewall?**                   | A system that monitors and filters network traffic based on predefined security rules. |
| **Stateful vs Stateless firewall?**       | Stateful tracks connection states; Stateless inspects each packet individually.        |
| **Inbound vs Outbound rules?**            | Inbound = incoming traffic control; Outbound = outgoing traffic control.               |
| **How does UFW simplify management?**     | It provides an easy CLI for complex `iptables` syntax.                                 |
| **Why block port 23 (Telnet)?**           | Telnet transmits credentials in plain text; insecure.                                  |
| **Common firewall mistakes?**             | Leaving unnecessary ports open, no default deny policy, missing logging.               |
| **How does a firewall improve security?** | Limits attack surface and enforces access control.                                     |
| **What is NAT in firewalls?**             | Network Address Translation – rewrites IPs to hide internal network structure.         |

---

## 📁 Deliverables
- `Task4_Firewall_Findings.pdf` — detailed report  
- `/screenshots/` — outputs of `ufw status` and netcat tests  
- `README.md` — this summary documentation  

---

## 🏁 Outcome
Successfully configured and tested Linux firewall rules using **UFW**.  
The task provided practical understanding of **traffic filtering**, **access control**, and **firewall rule validation**, strengthening foundational network security concepts.  

---

> ✨ *Prepared by Vivek Agrawal as part of the Firewall Configuration & Traffic Filtering Project — October 2025.*
