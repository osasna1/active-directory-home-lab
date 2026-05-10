# 🖥️ Active Directory Home Lab

> Enterprise-grade Active Directory environment built on VirtualBox — simulating a real corporate IT infrastructure

---

## 🎯 Objective

Design and deploy a fully functional Active Directory domain environment from scratch, simulating the kind of infrastructure found in enterprise IT environments. This lab demonstrates hands-on skills in Windows Server administration, Active Directory management, Group Policy, and network configuration.

---

## 🏗️ Infrastructure

| Component | Details |
|---|---|
| Host Machine | HP Laptop, Windows 11, Intel i7 13th Gen, 16GB RAM |
| Hypervisor | Oracle VirtualBox 7.1.10 |
| Domain Controller | Windows Server 2022 (FreshCorp-DC01) |
| Client Machine | Windows 10 Pro (FreshCorp-PC01) |
| Network Type | Internal Network (FreshCorpNet) |
| DC IP Address | 192.168.10.1 (Static) |
| Client IP Address | 192.168.10.10 (Static) |
| Domain | freshcorp.local |
| NetBIOS Name | FRESHCORP |

---

## ✅ What Was Built

### 1. Domain Controller (FreshCorp-DC01)
- Installed and configured **Windows Server 2022**
- Promoted server to **Domain Controller**
- Created domain: `freshcorp.local`
- Configured **static IP** (192.168.10.1) with DNS pointing to localhost

### 2. Active Directory Structure
- Created **4 Organisational Units (OUs):** HR, IT, Finance, Management
- Created **15 domain user accounts** distributed across all OUs
- Configured user passwords and account settings

### 3. Group Policy
- Created **FreshCorp Security Policy** GPO with:
  - Minimum password length: 8 characters
  - Password complexity: Enabled
  - Maximum password age: 91 days
  - Account lockout threshold: 5 failed attempts
  - Account lockout duration: 30 minutes

### 4. Network Configuration
- Configured both VMs on **VirtualBox Internal Network** (FreshCorpNet)
- Used **VBoxManage CLI** to set internal network (workaround for VirtualBox 7.1.10 UI bug)
- Set static IPs on both DC and client machines

### 5. Client Machine (FreshCorp-PC01)
- Installed **Windows 10 Pro**
- Configured static IP: `192.168.10.10`
- Set DNS to point to DC: `192.168.10.1`
- Successfully **joined freshcorp.local domain**
- Verified domain join via **Active Directory Users and Computers**

---

## 📸 Screenshots

### Active Directory Users and Computers — OUs and Users
![AD Users and Computers](screenshots/ad-users-computers.png)

### Group Policy Management — FreshCorp Security Policy
![Group Policy](screenshots/group-policy.png)

### DC01 Static IP Configuration
![DC01 Static IP](screenshots/dc01-static-ip.png)

### Welcome to freshcorp.local Domain
![Domain Join Success](screenshots/domain-join-success.png)

### PC01 Visible in AD Computers Container
![PC01 in AD](screenshots/pc01-in-ad.png)

---

## 🔍 Verification

- ✅ PC01 appeared under **Computers** container in Active Directory
- ✅ Ping test: 4/4 packets received between PC01 and DC01 (0% loss)
- ✅ Domain join confirmed with "Welcome to the freshcorp.local domain" message
- ✅ Group Policy applied successfully

---

## 🛠️ Tools & Technologies

`Windows Server 2022` `Windows 10 Pro` `Active Directory Domain Services` `Group Policy Management` `DNS` `TCP/IP` `VirtualBox 7.1.10` `VBoxManage CLI` `Active Directory Users and Computers`

---

## 💡 Key Troubleshooting Performed

- **VirtualBox UI bug:** Internal Network option missing from dropdown in v7.1.10 — resolved using `VBoxManage` command line to set network adapter
- **NAT vs Internal Network:** Original NAT configuration prevented VM-to-VM communication — resolved by switching both VMs to Internal Network
- **DNS configuration:** PC01 DNS must point to DC IP for domain discovery to work

---

## 👨‍💻 Author

**Mathew Idemudia** — IT Support, Help Desk Professional & Full-Stack Developer
[GitHub](https://github.com/osasna1) | [LinkedIn](https://www.linkedin.com/in/idemudia-mathew-10b3b5302/) | [id.mathew@outlook.com](mailto:id.mathew@outlook.com)
