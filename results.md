# Results

## 1. Summary of Results
- The simulated DDoS attacks were automatically detected and blocked by pfSense and Suricata.
- The internal target (Linux Mint) remained fully responsive with no packet reach.

## 2. Attack Outcomes

| Attack Type       | Blocked? | Detection Tool    | Notes                                  |
|-------------------|----------|-------------------|----------------------------------------|
| ICMP Flood        | Yes      | pfSense Firewall  | Block rule activated immediately       |
| TCP SYN Flood     | Yes      | Suricata (IPS)    | Alert shown; traffic dropped inline    |
| UDP Flood         | Yes      | pfSense Firewall  | UDP rule blocked the traffic           |

## 3. Evidence & Visuals

**Figure 1:** Suricata alert showing TCP SYN flood blocked from source IP 10.0.2.15.  
*(Insert screenshot)*

**Table 1:** Firewall log snippet showing blocked ICMP and UDP packets at timestamp 2025‑08‑31 14:05.

[View Firewall Log Screenshot](./FW_P_DDOS_Log.png)

## 4. Observations
- Firewall rules captured the ICMP and UDP floods before Suricata had a chance to evaluate.
- Suricata’s inline mode effectively intercepted the TCP SYN flood.
- No alerts or system load spikes detected on the target machine.

## 5. Appendices
- **Appendix A:** Full Suricata alert logs (`/logs/suricata_alerts.log`)
- **Appendix B:** Complete firewall logs (`/logs/pfsense_firewall.log`)
- **Appendix C:** Screenshots of pfSense UI configuration (`/screenshots/`)

---

### Why This Structure Works
- The **Results section** remains objective—just what happened and how you captured it.
- Visual aids help readers grasp outcomes at a glance.:contentReference[oaicite:1]{index=1}
- Linking to appendices keeps the main document clean, with detail available for deeper review.:contentReference[oaicite:2]{index=2}

