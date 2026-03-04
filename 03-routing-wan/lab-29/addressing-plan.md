## Addressing Plan – Lab 21 Routing and WAN Edge

This plan shows how to apply the **MASTER ADDRESSING BLUEPRINT** to an HQ LAN and a single ISP link.

### Blueprint Alignment
- **LAN subnets**: `192.168.X.0/24` for user, voice, server, and management VLANs.
- **WAN link**: `10.255.X.0/30` for point-to-point connections (here, `10.255.21.0/30`).
- **ISP core**: `203.0.113.0/24` for reachable external services.

### VLAN and Subnet Allocation

| VLAN | Name        | Subnet            | Gateway IP       | Notes                              |
|------|-------------|-------------------|------------------|------------------------------------|
| 10   | Users       | 192.168.10.0/24   | 192.168.10.1     | HQ user workstations               |
| 20   | Voice       | 192.168.20.0/24   | 192.168.20.1     | IP phones                          |
| 30   | Servers     | 192.168.30.0/24   | 192.168.30.1     | Application and data servers       |
| 99   | Management  | 192.168.99.0/24   | 192.168.99.1     | Management interfaces and tools    |

### WAN and ISP Allocation

| Link           | Subnet           | Device     | IP Address       |
|----------------|------------------|-----------|------------------|
| HQ–ISP P2P     | 10.255.21.0/30   | HQ Router | 10.255.21.1      |
| HQ–ISP P2P     | 10.255.21.0/30   | ISP Router| 10.255.21.2      |
| ISP Core LAN   | 203.0.113.0/24   | ISP Host  | 203.0.113.10     |

In future labs, `198.51.100.0/24` may be used to represent a secondary ISP.

### Example Host Assignments
- HQ user PCs: `192.168.10.50–192.168.10.150`.
- HQ servers: `192.168.30.10–192.168.30.50`.
- Management systems: `192.168.99.20–192.168.99.30`.

All addressing strictly follows the CCNA-aligned blueprint for small networks, WAN, and ISP simulation.

