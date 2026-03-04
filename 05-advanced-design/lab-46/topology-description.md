## Topology Description – Lab 46 Advanced Design and Automation

### Multi-Site Logical Topology
- **Sites**
  - Headquarters (HQ) with core, distribution, and access layers.
  - One or more large branches (B1, Bx).
  - One or more small branches (B2, By).
- **Connectivity**
  - Each site connects into the enterprise WAN via a point-to-point `10.255.X.0/30` link.
  - HQ peers with one or two simulated ISPs using `203.0.113.0/24` and `198.51.100.0/24`.

### Layered Design
- **Core**
  - Located at HQ; aggregates all site connections.
  - Maintains summarised routing towards the WAN and ISPs.
- **Distribution/Access**
  - Implement VLANs and SVIs using the standard VLAN ID and subnet plan.
- **WAN Edge**
  - At each site, a WAN router connects to HQ or provider edge.
  - Uses `10.255.X.0/30` addressing with clear documentation.

### Automation Angle
This lab assumes that much of the configuration is generated from templates. The topology description should therefore explicitly link:

- Device roles (core, distribution, access, WAN edge).
- Site codes.
- Interface roles (user access, trunk, WAN, ISP).

Use this document to maintain a clear mapping between the physical layout of your simulated environment and the logical design you intend to automate.

