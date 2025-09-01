# Home Lab: DDoS Simulation and Defense

## Project Overview

This is a cybersecurity home lab where I simulated an ICMP flood (ping flood) attack using Kali Linux and defended it using pfSense and Suricata IDS.

## Lab Components

- **Attacker**: Kali Linux (hping3)
- **Victim**: Linux Mint (internal system)
- **Firewall**: pfSense (blocking rules + Suricata IPS)
- **Goal**: Detect and block DDoS (ICMP flood) attacks

## Documentation

- `configs/`: Suricata, pfSense rule exports
- `rules/`: Custom Suricata rules
- `logs/`: Attack and defense logs
- `screenshots/`: pfSense and Suricata screenshots
