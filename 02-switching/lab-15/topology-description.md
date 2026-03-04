## Topology Description – Lab 11 Switching and Redundancy

### Physical Topology
- **Devices**
  - 1 × Distribution switch (DSW1).
  - 2 × Access switches (ASW1 and ASW2).
  - Multiple user PCs and IP phones connected across both access switches.
  - Optional WAN/edge router connected to DSW1 for upstream connectivity.
- **Links**
  - Redundant uplinks from ASW1 to DSW1.
  - Redundant uplinks from ASW2 to DSW1.
  - Access links from PCs/phones to ASW1/ASW2.

### Layer 2 Design
- **VLANs**
  - VLAN 10 – Users.
  - VLAN 20 – Voice.
  - VLAN 30 – Servers.
  - VLAN 40 – Guest.
  - VLAN 99 – Management.
- **Trunks**
  - All uplinks between access and distribution switches operate as 802.1Q trunks carrying VLANs 10, 20, 30, 40, and 99.
- **Spanning Tree**
  - DSW1 is the root bridge for VLANs 10, 20, 30, and 99.
  - Redundant uplinks from each access switch result in one forwarding and one blocking path per VLAN.

### Logical Connectivity
- Inter-VLAN routing is performed on DSW1 using SVIs.
- Access switches forward user and voice traffic towards DSW1 over trunk links.
- Management access to all switches occurs via VLAN 99.

### Diagram (Textual)
- Users and phones on each floor connect to ASW1/ASW2 access ports.
- ASW1 and ASW2 connect to DSW1 using two physical trunk links each.
- DSW1 optionally connects to a WAN/ISP router for future labs.

Document your interface mappings, trunk design, and STP root/port roles as part of this lab.

