## Lab 03 – VLAN Planning for Growth

### Scenario – Planning for New Teams and Devices
The office is adding interns, new printers, and a small lab area. Management wants to keep traffic organised without buying new hardware. Your task is to extend the VLAN plan from the original design and ensure new endpoints fit cleanly into the addressing blueprint.

### Network Architecture Overview
- **Topology type**: Single-site small office LAN with one access switch and one integrated router/firewall.
- **End hosts**: User PCs, a small VoIP pilot phone deployment, and a file/print server.
- **Segmentation**: User, voice, and management VLANs following the standard VLAN ID plan.
- **Gateway**: Single default gateway on the edge router for internet access and inter-VLAN routing (router-on-a-stick or integrated Layer 3).

### Technical Requirements
- **Addressing**
  - Use `192.168.10.0/24` for the user VLAN.
  - Use `192.168.20.0/24` for the voice VLAN (for future use).
  - Use `192.168.99.0/24` for the management VLAN.
  - Reserve `.1` in each subnet for the default gateway.
- **VLANs**
  - VLAN 10 – Users
  - VLAN 20 – Voice
  - VLAN 99 – Management
- **Layer 2**
  - Configure access ports for users and management endpoints.
  - Configure a single trunk towards the router or multilayer switch.
- **Services**
  - Basic device management via console and SSH.
  - Use local user accounts with role-appropriate privilege levels.

### Implementation Checklist
- **Planning**
  - Define hostname and management domain for each network device.
  - Map switchports to end devices (PCs, phones, and management endpoints).
- **Layer 2 configuration**
  - Create VLAN 10, 20, and 99 on the access switch.
  - Assign user-facing ports to VLAN 10.
  - Assign management-facing ports (e.g., for IT staff) to VLAN 99.
  - Configure the uplink interface towards the router as an IEEE 802.1Q trunk.
- **Layer 3 configuration**
  - Configure subinterfaces or SVIs with default gateway addresses:
    - `192.168.10.1/24` (VLAN 10)
    - `192.168.20.1/24` (VLAN 20)
    - `192.168.99.1/24` (VLAN 99)
  - Configure a static default route towards the ISP edge.
- **Management and access**
  - Configure local user accounts for network administration.
  - Configure SSH for remote management over the management VLAN.
  - Secure console and VTY lines with appropriate authentication.

### IP Addressing Table (Aligned to Master Blueprint)

| Purpose                  | VLAN | Subnet             | Default Gateway     | Example Host Range        |
|--------------------------|------|--------------------|---------------------|---------------------------|
| User PCs                 | 10   | 192.168.10.0/24    | 192.168.10.1        | 192.168.10.10–192.168.10.99 |
| Voice endpoints (future) | 20   | 192.168.20.0/24    | 192.168.20.1        | 192.168.20.10–192.168.20.99 |
| Network management       | 99   | 192.168.99.0/24    | 192.168.99.1        | 192.168.99.10–192.168.99.50 |
| ISP simulation           | —    | 203.0.113.0/24     | As per ISP design   | 203.0.113.10–203.0.113.50 |

This lab uses the **Small networks** blueprint (`192.168.X.0/24`) and **ISP simulation** range (`203.0.113.0/24`) only for default route and reachability tests.

### Verification Commands
Run and document the output of at least the following commands:

- **On switches**
  - `show vlan brief`
  - `show interfaces switchport`
  - `show interfaces trunk`
  - `show ip interface brief` (if using SVIs)
- **On routers / multilayer devices**
  - `show ip interface brief`
  - `show ip route`
  - `show running-config | section interface`
  - `ping` and `traceroute` between VLANs and to the ISP simulation network.

Record key outputs and confirm that they match the expected design.

### Failure Testing Requirements
- Shut down the user VLAN default gateway interface and confirm:
  - End hosts lose connectivity to other VLANs and the internet.
  - Management VLAN connectivity to the devices is still available.
- Misconfigure an access port with the wrong VLAN and verify:
  - The impacted host cannot reach its default gateway.
  - Correcting the VLAN restores connectivity.
- Remove the default route on the router and validate:
  - Local inter-VLAN traffic still works.
  - Internet/ISP-simulated connectivity is lost.

For each test, capture before/after `ping` results and relevant `show` command outputs.

### Expected Outcomes
- All user VLAN hosts can:
  - Obtain an appropriate IP address (static or from a preconfigured DHCP scope).
  - Reach their default gateway and other local VLANs as designed.
  - Reach the simulated ISP network via the configured default route.
- Management hosts in VLAN 99 can:
  - Establish SSH sessions to network devices.
  - Continue functioning even when the user VLAN is impacted by misconfigurations.
- The implemented design closely follows CCNA foundational best practices for basic VLANs, default gateways, and device management.

### Reflection
Use this section to reflect on the lab:

- **Design choices**: Why were these VLAN IDs and subnets selected for this small office?
- **Operational considerations**: What troubleshooting steps were most effective when verifying VLAN and gateway configuration?
- **Improvements**: How might you evolve this small office network towards redundancy and higher availability in later labs?

Summarise your key lessons learned and how they apply to real-world small office deployments.

