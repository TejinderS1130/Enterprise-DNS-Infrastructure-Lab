# 🖥️ Enterprise DNS Infrastructure Lab

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-blue?style=for-the-badge\&logo=windows)
![DNS](https://img.shields.io/badge/Service-DNS-critical?style=for-the-badge)
![Networking](https://img.shields.io/badge/Focus-Networking-informational?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

---

## 📌 Overview

This project demonstrates the design and implementation of a **DNS infrastructure in a Windows-based environment**, including cross-network communication between two isolated environments.

The lab replicates real-world administrative tasks such as DNS configuration, routing, and multi-network name resolution.

---

## 🧠 Architecture Diagram

```
🌐 NETWORK 1 (192.168.1.0/24)
┌──────────────────────────────┐
│ Windows Server 2022 (DNS)    │
│ ─ Primary DNS Server         │
└─────────────┬────────────────┘
              │
        ┌─────▼─────┐
        │ Windows 10 │
        │ Client     │
        └────────────┘


🌐 NETWORK 2 (192.168.2.0/24)
┌──────────────────────────────┐
│ Windows Server 2022 (DNS)    │
│ ─ Secondary / Forwarding     │
└─────────────┬────────────────┘
              │
        ┌─────▼─────┐
        │ Windows 11 │
        │ Client     │
        └────────────┘


🔀 Static Routing + DNS Resolution (Cross-Network)
```

---

## ⚙️ Infrastructure Setup

### 🖥️ Systems Configured

* Windows Server 2022 (Primary DNS Servers)
* Windows 10 Client
* Windows 11 Client

---

### 🔧 Core Configuration

* Renamed systems for structured environment
* Configured **Static IP addressing**
* Assigned DNS roles to servers
* Disabled IPv6 for controlled lab testing
* Adjusted firewall settings for connectivity

📸 **System Setup**

![Server Setup](screenshots/01-server-setup.png)
![Client Setup](screenshots/02-client-setup.png)

---

## 🌐 Network Connectivity

📸 **Ping Verification**

![Ping Test](screenshots/03-ping-test.png)
![Reverse Ping](screenshots/04-reverse-ping.png)

---

## 📡 DNS Deployment

* Installed DNS Server Role
* Configured DNS Manager
* Validated service functionality

📸 **DNS Installation**

![DNS Install](screenshots/05-dns-install.png)

---

## 🧩 DNS Configuration

### 🔹 Forward Lookup Zone

* Created Primary Zone
* Configured:

  * A Records
  * NS Record
  * SOA Record

📸 **Forward Lookup Zone**

![Forward Zone](screenshots/06-forward-zone.png)

---

### 🔹 Reverse Lookup Zone

* Implemented reverse resolution
* Configured PTR Records

📸 **Reverse Lookup Zone**

![Reverse Zone](screenshots/11-reverse-zone.png)

---

## 🧾 DNS Records Implemented

| Record Type | Purpose       |
| ----------- | ------------- |
| A Record    | Hostname → IP |
| PTR Record  | IP → Hostname |
| CNAME       | Alias mapping |
| MX          | Mail routing  |

📸 **DNS Records**

![CNAME](screenshots/09-cname.png)
![MX Record](screenshots/10-mx.png)

---

## 🔁 DNS Operations

Used built-in tools for validation and troubleshooting:

```bash
ipconfig /registerdns
ipconfig /flushdns
ipconfig /displaydns
nslookup
```

📸 **DNS Registration & Visibility**

![DNS Register](screenshots/07-dns-register.png)
![DNS Client Visible](screenshots/08-dns-client.png)

---

## 🧪 Testing & Validation

* ✔ Forward lookup (hostname → IP)
* ✔ Reverse lookup (IP → hostname)
* ✔ DNS cache verification
* ✔ Cross-network resolution

📸 **Testing**

![NSLOOKUP](screenshots/12-nslookup.png)

---

# 🏢 Multi-Network DNS Communication

## 🎯 Goal

Enable communication between two independent network environments.

---

## 🔀 Routing Configuration

* Implemented static routes between networks
* Verified using:

```bash
route print
ping
```

📸 **Routing**

![Route Add](screenshots/13-routing.png)
![Route Print](screenshots/14-route-print.png)

---

## 🌐 Cross-Network Connectivity

📸 **Cross Network Ping**

![Cross Ping](screenshots/15-cross-ping.png)

---

## 🔁 DNS Communication Methods

### 🔹 Secondary Zones

* Enabled zone transfers between servers

⚠️ Limitation:
Full DNS visibility across environments

📸 **Secondary Zone**

![Secondary Zone](screenshots/16-secondary-zone.png)

---

### 🔹 Stub Zones

* Configured partial DNS data sharing
* Improved security over secondary zones

📸 **Stub Zone**

![Stub Zone](screenshots/17-stub-zone.png)

---

### 🔹 Conditional Forwarders (Production Approach)

* Configured domain-based query forwarding
* Enabled efficient and secure name resolution

✅ Most practical real-world solution

📸 **Conditional Forwarder**

![Conditional Forwarder](screenshots/18-conditional-forwarder.png)

---

## 🧪 Final Results

* Successful communication between both networks
* DNS resolution verified across environments
* End-to-end validation using `ping` and `nslookup`

---

## 🧠 Key Concepts Demonstrated

* DNS architecture & resolution process
* Forward vs Reverse Lookup Zones
* DNS record management
* Multi-network communication
* Routing between isolated environments

---

## 📂 Project Structure

```
/screenshots
   ├── 01-system-setup/
   ├── 02-dns-installation/
   ├── 03-dns-records/
   ├── 04-testing/
   └── 05-multi-network/
```

---

## 🚀 What This Project Demonstrates

* Real-world DNS deployment and management
* Practical networking and routing skills
* Hands-on troubleshooting and validation
* Infrastructure-level system administration

---

## 👤 Author

**Tejinder Singh**
