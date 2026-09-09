# 🛡️ Cybersecurity Lab Setup: VirtualBox & Kali Linux

## 📝 Project Overview
This repository details the foundational attack laboratory configured for the Networkwalks Cybersecurity Internship. It serves as a secure, isolated environment for penetration testing, network analysis, and vulnerability assessment, bridging practical ethical hacking techniques with advanced concepts in Cryptography and Information Security.

## 🛠️ Architecture & Network Design
The environment relies on a custom NAT Network to isolate traffic during security operations while maintaining internet connectivity for the attacker machine.
* **Hypervisor:** Oracle VirtualBox
* **Attacker OS:** Kali Linux 2026.2 (amd64)
* **Subnet:** `10.0.0.0/24`
* **Attacker IP:** `10.0.0.2` (Static)
`VBox.png`
---

## 🚀 Configuration Steps

### 1. Global NAT Network Setup
A dedicated NAT Network was established to host the attacker machine and future vulnerable targets on the same local subnet.
* **Name:** `NatNetwork`
* **IPv4 Prefix:** `10.0.0.0/24` with DHCP enabled.

> 📸 **Configuration:** `Nat.png`

### 2. Kali Linux VM Parameters
The pre-built Kali Linux virtual appliance was imported and optimized for performance, seamless host interaction, and network visibility:
* **System & Acceleration:** Allocated 2048 MB of RAM with hardware virtualization (Nested Paging) enabled to ensure smooth execution of heavy cryptographic and security tools.
* **Network Adapter:** Attached to `NatNetwork` with Promiscuous Mode set to `Allow All` for deep packet inspection and network sniffing.
* **Shared Folders:** Configured a bidirectional auto-mounted folder to the host's `Downloads` directory for efficient file transfers.

> 📸 **System Settings:** `kaliconfig2.png` & `kaliconfig3.png`
> 📸 **Network Adapter:** `kaliconfig1.png`
> 📸 **Host Integration:** `kaliconfig4.png`

### 3. Internal IP Configuration
Inside the Kali OS, the network interface was configured to maintain a persistent static IP, ensuring reliable connectivity to the gateway. 
* **IP Address:** `10.0.0.2`
* **Netmask:** `24`
* **Gateway:** `10.0.0.1`
* **DNS:** `8.8.8.8`

> 📸 **Kali Network Manager:** `Interkali.jpg`

### 4. Baseline Snapshot & Deployment
After successfully configuring the network and resolving VirtualBox NAT routing limitations by executing a clean re-import, the machine (`my noussakali`) is fully operational. A clean baseline snapshot was taken to allow instant restoration during destructive testing scenarios.

> 📸 **Running State:** `snapshot.png`
