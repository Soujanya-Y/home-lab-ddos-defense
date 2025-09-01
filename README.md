# Home Lab DDoS Simulation and Mitigation

## Overview

This project documents a home lab environment simulating a Distributed Denial of Service (DDoS) attack and its mitigation using pfSense firewall and Suricata IDS/IPS.

- **Kali Linux** as attacker on external network
- **pfSense Firewall** as gateway and protective barrier
- **Suricata IDS/IPS** for intrusion detection and blocking
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
2. Install Suricata package on pfSense and enable blocking.
3. Configure firewall rules to mitigate DDoS traffic.
4. Use Kali Linux to simulate attacks (see Attack Simulation doc).
5. Monitor Suricata alerts and firewall logs.

## References

- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [Suricata Documentation](https://suricata.readthedocs.io/en/latest/)
- [hping3 Manual](http://www.hping.org/manpage.php)
