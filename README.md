# 🛡️ Introduction to Active Directory

A foundational guide covering the core architecture, components, and security realities of Microsoft Active Directory (AD).

---

## 📖 Why Active Directory?

**Active Directory (AD)** is a centralized, hierarchical directory service used to manage resources—such as users, computers, groups, policies, and trusts—across Windows network environments. Built for scale, AD handles authentication and authorization while supporting millions of objects as an organization grows.
<img width="942" height="679" alt="image" src="https://github.com/user-attachments/assets/52883405-ae5c-4602-9972-6d93bb74559f" />

### The Security Challenge
Despite its administrative convenience, AD is a prime target for attackers due to several architectural realities:
* **Legacy by Design:** Built for backward compatibility, many AD features are not secure by default and are prone to misconfiguration.
* **Open Enumeration:** By default, AD acts like a massive read-only database. Any standard, unprivileged domain user can query and enumerate most objects in the directory to map out the network and hunt for flaws.
* **Low-Privilege Exploitation:** Attackers do not need admin rights to begin compromising an environment. A basic domain account is often enough to execute lateral movement, privilege escalation, and high-impact exploits (such as the **noPac** vulnerability disclosed in December 2021).

### The Takeaway
Because any compromised user account can serve as a foothold for domain-wide enumeration, securing Active Directory requires proactive hardening, strict adherence to the principle of least privilege, network segmentation, and a robust defense-in-depth strategy.

---

## 🏗️ Core Components of Active Directory

To understand how AD operates and how to secure it, it helps to break it down into its primary building blocks:

| Component | Description |
| :--- | :--- |
| **Domain** | The core administrative and security boundary containing objects (users, computers, groups) that share a common database. |
| **Tree** | A collection of one or more domains grouped together in a contiguous namespace (e.g., `corp.local` and `sales.corp.local`). |
| **Forest** | The top-level container and ultimate security boundary in AD, consisting of one or more domain trees that share a common schema and Global Catalog. |
| **Domain Controller (DC)** | A server hosting the AD database (`NTDS.dit`) that processes authentication requests (Kerberos/NTLM) and enforces security policies. |
| **Organizational Unit (OU)** | Containers within a domain used to organize objects logically and apply Group Policy Objects (GPOs) or delegate administrative control. |
| **Group Policy Object (GPO)** | Collections of configuration and security settings pushed down to users and computers across a domain or OU. |

---

## 🔐 Key Protocols & Services

* **LDAP (Lightweight Directory Access Protocol):** The protocol used to query and modify directory information.
* **Kerberos:** The default ticket-based authentication protocol used in modern Windows domains.
* **NTLM:** A legacy challenge-response authentication protocol still supported for backward compatibility (and a frequent target for relay attacks).
* **DNS (Domain Name System):** Essential for locating Domain Controllers and resolving hostnames within the AD environment.

---

## 📂 Repository Contents

* `01-architecture/` — Notes and diagrams on Forests, Trees, Domains, and OUs.
* `02-authentication/` — Overview of Kerberos, NTLM, and LDAP workflows.
* `03-security-basics/` — Common misconfigurations, enumeration concepts, and hardening baselines.
* `lab-setup/` — Guides for building a local Active Directory home lab.

---

## ⚠️ Disclaimer
> **Note:** This repository is for educational and defensive learning purposes only. Always obtain explicit authorization before testing or enumerating any network environment.

---

## 📚 Further Reading
* [Microsoft Docs: Active Directory Domain Services Overview](https://microsoft.com)
* [Microsoft Docs: Best Practices for Securing Active Directory](https://microsoft.com)
