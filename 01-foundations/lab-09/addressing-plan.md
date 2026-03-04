## Addressing Plan – Lab 01 Foundations

This addressing plan follows the **MASTER ADDRESSING BLUEPRINT** for small networks and provides a consistent, repeatable structure for early CCNA labs.

### Addressing Blueprint Alignment
- **Small networks**: `192.168.X.0/24` used for LAN segments.
- **Enterprise LAN (future labs)**: `10.X.0.0/24` reserved for larger environments.
- **WAN**: `10.255.X.0/30` reserved for point-to-point links in later labs.
- **ISP simulation**: `203.0.113.0/24` and `198.51.100.0/24` reserved for upstream connectivity testing.

### VLAN and Subnet Allocation

| VLAN | Name        | Subnet            | Gateway IP       | Notes                                |
|------|-------------|-------------------|------------------|--------------------------------------|
| 10   | Users       | 192.168.10.0/24   | 192.168.10.1     | User workstations and laptops        |
| 20   | Voice       | 192.168.20.0/24   | 192.168.20.1     | IP phones (future expansion)         |
| 30   | Servers     | 192.168.30.0/24   | 192.168.30.1     | Reserved for server workloads        |
| 40   | Guest       | 192.168.40.0/24   | 192.168.40.1     | Reserved for guest internet access   |
| 50   | IoT         | 192.168.50.0/24   | 192.168.50.1     | Reserved for IoT devices             |
| 99   | Management  | 192.168.99.0/24   | 192.168.99.1     | Network device management            |

> Note: In this foundational lab, you may only implement VLANs 10, 20, and 99. Remaining VLANs and subnets are documented for future scalability and reuse across labs.

### Example IP Assignments

- **User VLAN 10 – 192.168.10.0/24**
  - Default gateway: `192.168.10.1`
  - Static host examples:
    - PC-1: `192.168.10.11`
    - PC-2: `192.168.10.12`
- **Voice VLAN 20 – 192.168.20.0/24**
  - Default gateway: `192.168.20.1`
  - Phone examples (future labs):
    - Phone-1: `192.168.20.21`
    - Phone-2: `192.168.20.22`
- **Management VLAN 99 – 192.168.99.0/24**
  - Default gateway: `192.168.99.1`
  - Device management:
    - SW1 SVI: `192.168.99.11`
    - R1 management: `192.168.99.254`

### ISP Simulation

For reachability tests towards an upstream network, use:

- `203.0.113.0/24` – Primary simulated ISP network
  - Example loopback or cloud object: `203.0.113.10`
- `198.51.100.0/24` – Secondary simulated ISP network (reserved for future multi-homing labs)

A single static default route on the customer edge device should point towards the ISP-facing next hop as defined in your topology.

