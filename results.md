# Results

## 1. Summary of Results
- The simulated DDoS attacks were automatically detected and blocked by pfSense.
- The internal target (Linux Mint) remained fully responsive with no packet reach.

## 2. Attack Outcomes

| Attack Type       | Blocked? | Detection Tool    | Notes                                  |
|-------------------|----------|-------------------|----------------------------------------|
| ICMP Flood        | Yes      | pfSense Firewall  | Block rule activated immediately       |
| TCP SYN Flood     | Yes      | Suricata (IPS)    | Alert shown; traffic dropped inline    |


## 3. Evidence & Visuals

**Figure 1:** pfSense alert showing ICMP flood blocked from source IP 10.0.2.15.  
[View Firewall Log Screenshot_ICMP](./FW_P_DDOS_Log.png)

**Figure 2:** pfSense alert showing TCP SYN flood blocked from source IP 10.0.2.15.  
[View Firewall Log Screenshot_TCP_SYN](./Tcp_syn_flood_Firewall_Block_logs.png)

## 4. Observations
- Firewall rules captured the ICMP and TCP SYN floods.
- No alerts or system load spikes detected on the target machine.

---



