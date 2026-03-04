## Addressing Plan – Lab 11 Switching and Redundancy

This addressing plan extends the **MASTER ADDRESSING BLUEPRINT** to a small campus with two access switches and one distribution switch.

### Addressing Blueprint Alignment
- **Small networks**: `192.168.X.0/24` per VLAN.
- **Enterprise LAN (future)**: `10.X.0.0/24` reserved for larger, multi-site deployments.
- **WAN**: `10.255.X.0/30` reserved for point-to-point links that will be introduced in routing/WAN labs.
- **ISP simulation**: `203.0.113.0/24` and `198.51.100.0/24` reserved for upstream connectivity and failover tests.

### VLAN and Subnet Allocation

| VLAN | Name        | Subnet            | Gateway IP       | Notes                                       |
|------|-------------|-------------------|------------------|---------------------------------------------|
| 10   | Users       | 192.168.10.0/24   | 192.168.10.1     | User PCs on both floors                     |
| 20   | Voice       | 192.168.20.0/24   | 192.168.20.1     | IP phones and voice gateways                |
| 30   | Servers     | 192.168.30.0/24   | 192.168.30.1     | Data centre / server room                   |
| 40   | Guest       | 192.168.40.0/24   | 192.168.40.1     | Guest internet-only access                  |
| 99   | Management  | 192.168.99.0/24   | 192.168.99.1     | Management SVIs and out-of-band devices     |

### Example IP Assignments

- **Distribution Switch (DSW1)**
  - VLAN 10 SVI: `192.168.10.1`
  - VLAN 20 SVI: `192.168.20.1`
  - VLAN 30 SVI: `192.168.30.1`
  - VLAN 40 SVI: `192.168.40.1`
  - VLAN 99 SVI: `192.168.99.1`
- **Access Switches (ASW1, ASW2)**
  - Management SVI (VLAN 99):
    - ASW1: `192.168.99.11`
    - ASW2: `192.168.99.12`
- **End Hosts**
  - Users: `192.168.10.50–192.168.10.150`
  - Voice endpoints: `192.168.20.50–192.168.20.150`
  - Servers: `192.168.30.10–192.168.30.50`

### ISP and Upstream Planning

Although not fully implemented in this switching-focused lab, plan for the following ranges:

- Primary ISP segment: `203.0.113.0/24`
- Secondary ISP segment: `198.51.100.0/24`

These networks will be used in later labs to validate end-to-end connectivity from campus VLANs to external services via a routed WAN edge.

