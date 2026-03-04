## Topology Description – Lab 01 Foundations

### Physical and Logical Topology
- **Sites**: Single site – Small Office.
- **Devices** (minimum)
  - 1 × Layer 2 access switch (SW1).
  - 1 × router or Layer 3 switch acting as the default gateway (R1).
  - 2–4 × end hosts (PCs) in the user VLAN.
  - 1 × management workstation in the management VLAN (optional but recommended).
- **Links**
  - One access link per end host to SW1.
  - One 802.1Q trunk link between SW1 and R1 (or between SW1 and a multilayer switch).
  - One uplink from R1 to the simulated ISP/cloud device.

### VLAN and Layer 2 Layout
- **VLAN 10 – Users**
  - Assigned to user-facing access ports.
  - Carries user workstation traffic.
- **VLAN 20 – Voice (Future)**
  - Reserved for IP phones and voice traffic.
- **VLAN 99 – Management**
  - Used for switch and router management access.
- **Trunk Link**
  - Between SW1 and R1 (or L3 switch), carrying VLANs 10, 20, and 99.

### Layer 3 and Routing
- **Default Gateways**
  - `192.168.10.1/24` for VLAN 10.
  - `192.168.20.1/24` for VLAN 20.
  - `192.168.99.1/24` for VLAN 99.
- **Routing**
  - Inter-VLAN routing performed on R1 or a multilayer switch.
  - Static default route pointing to the ISP-facing next hop.

### ISP / Cloud Representation
- Simulate an ISP using a cloud object, loopback interface, or dedicated router using:
  - `203.0.113.0/24` as the primary ISP network.
- Establish connectivity from the customer edge router (R1) towards the ISP network for basic reachability and default route validation.

### Logical Diagram (Textual)
- **User segment**
  - `PC1`, `PC2` → Access ports on `SW1` (VLAN 10).
- **Management segment**
  - `Mgmt-PC` → Access port on `SW1` (VLAN 99).
- **Network core**
  - `SW1` ↔ `R1` via trunk link carrying VLANs 10, 20, 99.
  - `R1` ↔ `ISP` via routed link for default route testing.

Document your exact port mappings, device names, and any deviations from this baseline in your lab notes.

