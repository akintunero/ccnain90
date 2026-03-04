## Topology Description – Lab 36 Security and Monitoring

### Physical Topology
- **Devices**
  - 1 × Branch edge router.
  - 1 × Branch access switch.
  - Branch end hosts in user, guest, and management VLANs.
  - 1 × Syslog/monitoring server in the servers VLAN.
  - WAN connection to HQ router.
- **Links**
  - Access links from hosts to the access switch.
  - Trunk or routed link from access switch to branch router.
  - P2P WAN link from branch router to HQ router.

### Logical Topology
- **LAN Segments**
  - VLAN 10 – Users: typical office clients.
  - VLAN 20 – Voice: IP phones.
  - VLAN 30 – Servers: includes the syslog/monitoring server.
  - VLAN 40 – Guest: restricted internet-only access.
  - VLAN 99 – Management: device administration.
- **WAN**
  - Branched router peers with HQ router over `10.255.36.0/30`.
- **Security Plane**
  - ACLs applied on the branch router to control:
    - What branch VLANs can reach HQ resources.
    - What guest users are permitted to access.
  - Logging/monitoring flows from network devices to the syslog server.

Use this description as a guide when drawing a topology diagram in your preferred tool or simulator.

