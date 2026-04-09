# 🖥️ Enterprise DNS Infrastructure Lab

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-blue?style=for-the-badge\&logo=windows)
![DNS](https://img.shields.io/badge/Service-DNS-critical?style=for-the-badge)
![Networking](https://img.shields.io/badge/Focus-Networking-informational?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

---

## Overview

This project demonstrates the design and implementation of a **DNS infrastructure in a Windows-based environment**, including cross-network communication between two isolated environments.

---

## Architecture

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
                                                
                                                
                                         Static Routing + DNS Resolution (Cross-Network)
```

---

## Infrastructure Setup

### Systems Configured

* Windows Server 2022 (Primary DNS Servers)
* Windows 10 Client
* Windows 11 Client

---

### Core Configuration

* Renamed systems for structured environment
* Configured **Static IP addressing**
* Assigned DNS roles to servers
* Disabled IPv6 for controlled lab testing
* Adjusted firewall settings for connectivity

<p align="center">
  <img src="screenshots/01-server-setup.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/02-client-setup.png" width="550"/>
</p>

---

## DNS Deployment

* Installed DNS Server Role
* Configured DNS Manager
* Validated service functionality

<p align="center">
  <img src="screenshots/05-dns-install.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/06-dns-installed.png" width="550"/>
</p>

---

## DNS Configuration

### Forward Lookup Zone

* Created Primary Zone
* Configured:

  * A Records
  * NS Record
  * SOA Record

<p align="center">
  <img src="screenshots/07-forward-zone.png" width="650"/>
</p>

---

### Reverse Lookup Zone

* Implemented reverse resolution
* Configured PTR Records

<p align="center">
  <img src="screenshots/11-reverse-zone.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/12-ptr-record.png" width="550"/>
</p>

---

## DNS Records Implemented

| Record Type | Purpose       |
| ----------- | ------------- |
| A Record    | Hostname → IP |
| PTR Record  | IP → Hostname |
| CNAME       | Alias mapping |
| MX          | Mail routing  |

<p align="center">
  <img src="screenshots/09-cname.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/10-mx.png" width="550"/>
</p>

---

## DNS Operations

Used built-in tools for validation and troubleshooting:

```bash
ipconfig /registerdns
ipconfig /flushdns
ipconfig /displaydns
nslookup
```

<p align="center">
  <img src="screenshots/08-dns-client.png" width="600"/>
</p>

---

## Testing & Validation

* ✔ Forward lookup (hostname → IP)
* ✔ Reverse lookup (IP → hostname)
* ✔ DNS cache verification
* ✔ Cross-network resolution

<p align="center">
  <img src="screenshots/03-ping-test.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/04-reverse-ping.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/13-nslookup.png" width="600"/>
</p>

---

# Multi-Network DNS Communication

## Goal

Enable communication between two independent network environments.

---

## Routing Configuration

* Implemented static routes between networks
* Verified using:

```bash
route print
ping
```

<p align="center">
  <img src="screenshots/14-add-routing.png" width="550"/>
</p>

<p align="center">
  <img src="screenshots/15-route-print.png" width="550"/>
</p>

---

## DNS Communication Methods

### Secondary Zones

* Enabled zone transfers between servers

Limitation:
Full DNS visibility across environments

<p align="center">
  <img src="screenshots/17-secondary-zone.png" width="600"/>
</p>

---

### Stub Zones

* Configured partial DNS data sharing
* Improved security over secondary zones

<p align="center">
  <img src="screenshots/18-stub-zone.png" width="600"/>
</p>

---

### Conditional Forwarders (Production Approach)

* Configured domain-based query forwarding
* Enabled efficient and secure name resolution

Most practical real-world solution

<p align="center">
  <img src="screenshots/19-conditional-forwarder.png" width="650"/>
</p>

---

## Final Results

* Successful communication between both networks
* DNS resolution verified across environments
* End-to-end validation using `ping` and `nslookup`

<p align="center">
  <img src="screenshots/16-cross-ping.png" width="650"/>
</p>

---

## Key Concepts Demonstrated

* DNS architecture & resolution process
* Forward vs Reverse Lookup Zones
* DNS record management
* Multi-network communication
* Routing between isolated environments

---

## Screenshots

> Stored inside `/screenshots` folder

---

## What This Project Demonstrates

* Real-world DNS deployment and management
* Practical networking and routing skills
* Hands-on troubleshooting and validation
* Infrastructure-level system administration

---

## 👤 Author

**Tejinder Singh**
