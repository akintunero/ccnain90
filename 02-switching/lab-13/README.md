## Lab 13 – Spanning Tree Root and Topology Control

### Scenario – Choosing a Predictable STP Root
Random Spanning Tree elections are causing suboptimal paths in the campus. Your task is to select and document a primary and secondary STP root, adjust priorities, and confirm that the Layer 2 topology converges as intended.

### Network Architecture Overview
- **Topology type**: Small campus with one distribution switch and two access switches.
- **End hosts**: User PCs and a growing VoIP deployment on both floors.
- **Segmentation**: VLANs for users, voice, servers, guest, and management.
- **Redundancy**:
  - Dual uplinks from each access switch to the distribution layer.
  - Spanning Tree Protocol (STP) controls loops and elects a root bridge.

### Technical Requirements
- **VLANs (from master blueprint)**
  - VLAN 10 – Users
  - VLAN 20 – Voice
  - VLAN 30 – Servers
  - VLAN 40 – Guest
  - VLAN 99 – Management
- **Addressing**
  - Use `192.168.10.0/24`, `192.168.20.0/24`, `192.168.30.0/24`, and `192.168.99.0/24` for the respective VLANs.
  - Use `.1` as the default gateway for each VLAN (SVIs on the distribution switch).
- **Switching and redundancy**
  - Configure trunk links between access and distribution switches.
  - Enable and verify STP; ensure a deliberate root bridge is defined.
  - (Optional) Configure EtherChannel for uplink aggregation if supported.
- **Management and security**
  - Use VLAN 99 for switch management.
  - Harden basic switch access (passwords, SSH, disabling unused ports).

### Implementation Checklist
- **Planning**
  - Assign switch roles (distribution vs access) and host placement.
  - Decide which switch will be the STP root for user and voice VLANs.
- **VLAN and trunk configuration**
  - Create VLANs 10, 20, 30, 40, and 99 on all switches.
  - Configure uplink ports as 802.1Q trunks allowing the required VLANs.
  - Ensure access ports are assigned to the correct VLANs based on host role.
- **Layer 3 configuration**
  - On the distribution switch, configure SVIs:
    - `192.168.10.1/24` for VLAN 10
    - `192.168.20.1/24` for VLAN 20
    - `192.168.30.1/24` for VLAN 30
    - `192.168.99.1/24` for VLAN 99
  - Configure a static default route towards the WAN/ISP edge if present.
- **Redundancy and STP tuning**
  - Configure STP priority so that the distribution switch becomes root.
  - Verify root and non-root port roles on all switches.
  - (Optional) Configure EtherChannel for bundled uplinks.

### IP Addressing Table (Aligned to Master Blueprint)

| VLAN | Purpose      | Subnet            | Default Gateway     | Notes                             |
|------|--------------|-------------------|---------------------|-----------------------------------|
| 10   | Users        | 192.168.10.0/24   | 192.168.10.1        | User access on both floors        |
| 20   | Voice        | 192.168.20.0/24   | 192.168.20.1        | IP phones and voice gateways      |
| 30   | Servers      | 192.168.30.0/24   | 192.168.30.1        | Application and file servers      |
| 40   | Guest        | 192.168.40.0/24   | 192.168.40.1        | Guest Wi‑Fi or wired guest ports  |
| 99   | Management   | 192.168.99.0/24   | 192.168.99.1        | Switch and router management      |

This lab uses the **Small networks** blueprint for VLAN IPs and assumes external WAN connectivity will be added in later routing labs.

### Verification Commands
Capture and interpret the output of:

- **VLANs and trunks**
  - `show vlan brief`
  - `show interfaces trunk`
  - `show interfaces switchport`
- **Spanning Tree**
  - `show spanning-tree`
  - `show spanning-tree vlan 10`
  - `show spanning-tree vlan 20`
- **Layer 3 and reachability**
  - `show ip interface brief`
  - `show ip route`
  - `ping` between hosts on different VLANs and on different access switches.

### Failure Testing Requirements
- Intentionally misconfigure one uplink as an access port and observe STP behaviour and connectivity impact.
- Shut down one of the redundant uplinks and confirm that traffic converges to the remaining path without major disruption.
- Change the STP priority to force a different switch to become root and verify the port role changes.

Document each failure test in the dedicated `failure-testing.md` file for this lab.

### Expected Outcomes
- VLANs and trunk links operate correctly across the campus switches.
- The designated distribution switch is the STP root for the primary VLANs.
- Users maintain connectivity when an uplink fails, demonstrating basic redundancy.
- Learners can interpret STP output and predict port states in a simple redundant topology.

### Reflection
Use this section to reflect on:

- **Design decisions**: Why is it important to deliberately choose an STP root rather than relying on defaults?
- **Operational resilience**: How did redundancy change the impact of link failures compared to single-path topologies?
- **Next steps**: Which additional features (such as EtherChannel, portfast, BPDU guard) would you add in future labs to further harden the campus access layer?

Summarise key insights and how they apply to real campus networks with multiple wiring closets and floors.

