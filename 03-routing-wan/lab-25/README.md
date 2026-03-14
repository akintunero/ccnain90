## Lab 25 – Summarisation and Route Filtering

### Scenario – Cleaning Up the Routing Table
As more VLANs are added at HQ, route tables are growing. Your task is to design simple IPv4 summarisation and, where appropriate, basic route filtering so branch routers see only the prefixes they need.

### Network Architecture Overview
- **Topology type**: Single-site headquarters with a dedicated WAN edge router.
- **Core components**:
  - One core/distribution switch performing inter-VLAN routing.
  - One WAN edge router connected to an ISP.
- **Segmentation**: Multiple VLANs mapped to `192.168.X.0/24` networks.
- **WAN**:
  - Point-to-point link using `10.255.X.0/30` from the WAN blueprint.
  - Upstream ISP network using `203.0.113.0/24`.

### Technical Requirements
- **VLANs and LAN subnets**
  - VLAN 10 – Users: `192.168.10.0/24`
  - VLAN 20 – Voice: `192.168.20.0/24`
  - VLAN 30 – Servers: `192.168.30.0/24`
  - VLAN 99 – Management: `192.168.99.0/24`
- **WAN link**
  - Use `10.255.21.0/30` for the point-to-point link between HQ edge router and ISP router.
- **Routing**
  - Configure inter-VLAN routing on the core switch or router-on-a-stick device.
  - Configure a static default route from the HQ edge router towards the ISP.
  - Configure return routes or a default route on the ISP towards HQ LAN networks.
- **IP services**
  - Ensure hosts can reach the ISP test IP (for example, `203.0.113.10`).

### Implementation Checklist
- **LAN routing**
  - Configure SVIs or routed subinterfaces for VLANs 10, 20, 30, and 99.
  - Verify intra-site connectivity between all VLANs.
- **WAN edge**
  - Configure the HQ router interface towards the ISP using `10.255.21.1/30`.
  - Configure the ISP-side router interface using `10.255.21.2/30`.
- **Routing configuration**
  - On HQ router:
    - Configure static routes for LAN subnets if the core is a separate device.
    - Configure `ip route 0.0.0.0 0.0.0.0 10.255.21.2`.
  - On ISP router:
    - Configure static route(s) for `192.168.10.0/24`, `192.168.20.0/24`, `192.168.30.0/24`, and `192.168.99.0/24` pointing to `10.255.21.1` **or** a single default route if simulating the internet in a larger topological context.

### IP Addressing Table (Aligned to Master Blueprint)

| Segment         | Purpose          | Subnet              | Example IPs                  |
|----------------|------------------|---------------------|------------------------------|
| VLAN 10        | Users            | 192.168.10.0/24     | 192.168.10.1 (GW), .50–.150  |
| VLAN 20        | Voice            | 192.168.20.0/24     | 192.168.20.1 (GW), .50–.150  |
| VLAN 30        | Servers          | 192.168.30.0/24     | 192.168.30.1 (GW), .10–.50   |
| VLAN 99        | Management       | 192.168.99.0/24     | 192.168.99.1 (GW), .11–.50   |
| WAN P2P        | HQ–ISP link      | 10.255.21.0/30      | 10.255.21.1 (HQ), .2 (ISP)   |
| ISP Core       | Upstream network | 203.0.113.0/24      | 203.0.113.10 (test host)     |

### Verification Commands
- **On HQ core/edge devices**
  - `show ip interface brief`
  - `show ip route`
  - `show vlan brief` (if using SVIs)
- **On ISP router**
  - `show ip interface brief`
  - `show ip route`
- **End-to-end tests**
  - `ping` between different VLANs within HQ.
  - `ping` from a user VLAN host to `203.0.113.10`.
  - `traceroute` from a user VLAN host towards the ISP test IP.

### Failure Testing Requirements
- Remove or misconfigure the static default route on the HQ router and observe loss of external reachability.
- Break the WAN link (administratively shut one side) and verify loss of connectivity to the ISP while local inter-VLAN routing remains functional.
- Misconfigure one LAN subnet mask and analyse routing-table and connectivity symptoms.

Document each test scenario and findings in the dedicated `failure-testing.md` file for this lab.

### Expected Outcomes
- Inter-VLAN routing operates correctly within HQ.
- The HQ site has working outbound connectivity to the simulated ISP network.
- Routing tables on HQ and ISP routers accurately reflect LAN and WAN prefixes.
- Learners can interpret static routes and understand the flow of traffic between LAN and WAN.

### Reflection
Use this section to reflect on:

- **Routing design choices**: Why use a /30 for the WAN link? What are the advantages of static routing at this scale?
- **Separation of roles**: How do you decide whether to route on a core switch vs. a separate WAN edge router?
- **Evolution path**: How might you migrate this design to dynamic routing protocols or dual-homed ISPs in future labs?

Capture your observations and design trade-offs as part of your learning portfolio.

