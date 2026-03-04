## Addressing Plan – Lab 36 Security and Monitoring

This lab uses the **MASTER ADDRESSING BLUEPRINT** to define secure and well-documented segments at the branch office.

### Blueprint Alignment
- **LAN**: `192.168.X.0/24` ranges for all VLANs.
- **WAN**: `10.255.X.0/30` for the branch–HQ point-to-point link.
- **ISP/External**: `203.0.113.0/24` and `198.51.100.0/24` are available for upstream testing in expanded topologies.

### VLAN and Subnet Allocation

| VLAN | Name        | Subnet            | Gateway IP       | Notes                                  |
|------|-------------|-------------------|------------------|----------------------------------------|
| 10   | Users       | 192.168.10.0/24   | 192.168.10.1     | Branch user workstations               |
| 20   | Voice       | 192.168.20.0/24   | 192.168.20.1     | Branch IP phones                       |
| 30   | Servers     | 192.168.30.0/24   | 192.168.30.1     | Includes syslog/monitoring server      |
| 40   | Guest       | 192.168.40.0/24   | 192.168.40.1     | Internet-only guest access             |
| 99   | Management  | 192.168.99.0/24   | 192.168.99.1     | Out-of-band and in-band management     |

### WAN Allocation

| Link             | Subnet           | Device       | IP Address    |
|------------------|------------------|-------------|---------------|
| Branch–HQ P2P    | 10.255.36.0/30   | Branch Rtr  | 10.255.36.1   |
| Branch–HQ P2P    | 10.255.36.0/30   | HQ Rtr      | 10.255.36.2   |

### Security-Relevant Addressing
- Syslog/monitoring server: `192.168.30.10`.
- Branch router management: `192.168.99.21`.
- HQ security tools (if present): within relevant `10.X.0.0/24` or `192.168.X.0/24` ranges as per HQ design.

Use these addresses consistently when building ACLs, logging destinations, and monitoring policies.

