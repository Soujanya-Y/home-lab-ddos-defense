# pfSense Configuration for DDoS Mitigation

## Overview

This document describes how pfSense was configured to detect and block simulated DDoS attacks in a home lab environment using:

- Firewall rules
- Suricata IDS/IPS

---

## Network Setup Recap

| Role              | IP Address     | Description              |
|-------------------|----------------|--------------------------|
| Attacker (Kali)   | 10.0.2.15      | External source of attack traffic |
| pfSense WAN       | 10.0.2.1       | External interface (connected to attacker) |
| pfSense LAN       | 192.168.1.1    | Internal interface (connected to target) |
| Target (Linux Mint)| 192.168.1.100 | Internal victim machine |

---

## 1. pfSense Interface Configuration

- **WAN interface** connected to the attacker network (`10.0.2.0/24`)
- **LAN interface** connected to the internal network (`192.168.1.0/24`)

---

## 2. Firewall Rules

### 🛡️ WAN Interface Rules (Inbound)

| Action | Protocol | Source        | Destination       | Description               |
|--------|----------|---------------|-------------------|---------------------------|
| Block  | ICMP     | 10.0.2.15     | 192.168.1.100     | Block ICMP flood attacks  |
| Block  | TCP      | 10.0.2.15     | 192.168.1.100:80  | Block TCP SYN floods on port 80 |
| Block  | UDP      | 10.0.2.15     | 192.168.1.100     | Block UDP floods          |

> These rules were created under **Firewall > Rules > WAN** and placed at the **top** of the rule list to take priority.

---

## 3. Suricata IDS/IPS Setup

### 📦 Installation

- Installed Suricata via **pfSense Package Manager**

### 🔧 Interface Configuration

- Enabled Suricata on the **WAN interface** (where attacker traffic enters)
- Mode: **Inline (IPS)** — to allow automatic blocking

### 📘 Rule Categories Enabled

- `emerging-ddos.rules`
- `emerging-attack_response.rules`
- `emerging-trojan.rules`
- `suricata-deleted.rules` (optional)

You can find these in **Services > Suricata > WAN > Categories**

### 🛠️ Thresholding & Suppression

- Custom threshold settings were used to avoid false positives
- Example: Alert if more than 10 packets per second from a single IP

### ✅ Blocking Settings

- **"Block offenders"** enabled
- **"Kill states"** enabled to immediately drop matching connections
- Set to **drop** traffic instead of just alerting

---

## 4. Logs & Monitoring

- **Alerts** tab used to monitor triggered Suricata rules
- **Firewall Logs** showed blocked traffic from attacker IP `10.0.2.15`
- Blocking was confirmed by running attack tools (e.g., `hping3`) and observing dropped packets

---

## 5. Test Example

Simulated TCP SYN flood from Kali:

```bash
hping3 --flood --syn -p 80 192.168.1.100
