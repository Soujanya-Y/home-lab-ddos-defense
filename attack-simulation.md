# Attack Simulation

## Objective

To simulate a basic Distributed Denial of Service (DDoS) attack from an external network (Kali Linux) targeting an internal host (Linux Mint) through the pfSense firewall. This helps evaluate the firewall and Suricata’s ability to detect and block malicious traffic.

---

## Lab Environment Recap

| Component       | Role          | IP Address     |
|----------------|---------------|----------------|
| Kali Linux      | Attacker      | 192.168.1.10   |
| pfSense WAN     | Gateway (ext) | 192.168.1.1    |
| pfSense LAN     | Gateway (int) | 10.0.0.1       |
| Linux Mint      | Target        | 10.0.0.10      |

---

## Attack Types Simulated

### 1. **ICMP Flood (Ping Flood)**

This attack floods the target with ICMP Echo Request packets (ping), consuming network resources.

**Command used:**

```bash

hping3 --icmp --flood -d 120 10.0.0.10
