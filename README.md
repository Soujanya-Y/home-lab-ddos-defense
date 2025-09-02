# Home Lab DDoS Simulation and Mitigation

## Overview

This project documents a home lab environment simulating a Distributed Denial of Service (DDoS) attack and its mitigation using pfSense firewall.

- **Kali Linux** as attacker on external network
- **pfSense Firewall** as gateway and protective barrier
- **Linux Mint** as the internal target machine

## Lab Components

- Kali Linux (attacker)
- pfSense firewall with Suricata package
- Linux Mint (target)

## Documentation

- [Network Architecture](network-architecture.md)
- [Attack Simulation](attack-simulation.md)
- [pfSense Configuration](pfsense-configuration.md)
- [Results and Analysis](results.md)

## Quick Start

1. Set up pfSense firewall with WAN and LAN interfaces.
2. Configure firewall rules to mitigate DDoS traffic.
3. Use Kali Linux to simulate attacks (see Attack Simulation doc).
4. Monitor alerts and firewall logs.

## References

- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [hping3 Manual](http://www.hping.org/manpage.php)
