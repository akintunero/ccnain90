## Topology Description – Lab 21 Routing and WAN Edge

### Physical Topology
- **Devices**
  - 1 × Core/distribution switch (HQ-SW1).
  - 1 × HQ edge router (HQ-R1).
  - 1 × ISP router (ISP-R1).
  - Multiple HQ end hosts (PCs and servers).
- **Links**
  - Trunk or routed links between HQ-SW1 and HQ-R1 as required.
  - Point-to-point link between HQ-R1 and ISP-R1 using `10.255.21.0/30`.
  - Access links from HQ-SW1 to hosts in different VLANs.

### Logical Topology
- **LAN**
  - HQ-SW1 provides Layer 2 connectivity for VLANs 10, 20, 30, and 99.
  - Inter-VLAN routing provided by either:
    - SVIs on HQ-SW1, or
    - Subinterfaces on HQ-R1 (router-on-a-stick).
- **WAN**
  - HQ-R1 and ISP-R1 form a point-to-point routed link.
  - ISP-R1 provides access to a simulated external network (`203.0.113.0/24`).

### Traffic Flows
- VLAN hosts send traffic to their default gateway on HQ-SW1 or HQ-R1.
- HQ-R1 forwards internet-bound traffic via the `10.255.21.0/30` link to ISP-R1.
- ISP-R1 forwards traffic to a test host in `203.0.113.0/24`.

Use this document as a reference when drawing or building your own diagram in a network simulator.

