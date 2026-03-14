## Lab 33 – WAN Edge Policy and Basic QoS Planning

### Scenario – Planning for Application‑Aware Routing
Voice and critical applications now share the WAN. Your task is to outline how simple policy‑based decisions and QoS markings at the edge could protect important traffic, without implementing full QoS configs.

### Network Architecture Overview
- **Topology type**: HQ and single branch, each with a dedicated WAN edge router.
- **Core components**:
  - One HQ core/distribution switch performing inter-VLAN routing.
  - One HQ WAN edge router connected to both branch and ISP.
  - One branch router with a smaller LAN behind it.
- **Segmentation**: Multiple VLANs at HQ mapped to `192.168.X.0/24` networks; a smaller user subnet at the branch.
- **WAN**:
  - HQ–Branch point-to-point link using `10.255.30.0/30` from the WAN blueprint.
  - HQ–ISP point-to-point link using `10.255.21.0/30`.
  - Upstream ISP network using `203.0.113.0/24`.

### Technical Requirements
- **HQ VLANs and LAN subnets**
  - VLAN 10 – HQ Users: `192.168.10.0/24`
  - VLAN 20 – HQ Voice: `192.168.20.0/24`
  - VLAN 30 – HQ Servers: `192.168.30.0/24`
  - VLAN 99 – HQ Management: `192.168.99.0/24`
- **Branch LAN subnet**
  - Branch Users: `192.168.110.0/24` (single user VLAN at the branch).
- **WAN links**
  - Use `10.255.21.0/30` for HQ–ISP.
  - Use `10.255.30.0/30` for HQ–Branch.
- **Routing**
  - Configure inter-VLAN routing on the HQ core switch or router-on-a-stick device.
  - Use a dynamic routing protocol (such as single-area OSPF) between HQ and Branch to advertise:
    - HQ LAN prefixes.
    - Branch LAN prefix.
  - Configure a static default route from HQ towards the ISP and redistribute it into the dynamic routing domain, or use a default-information originate mechanism.
  - Configure return routes or a default route on the ISP towards HQ/Branch as appropriate for your simulator.
- **IP services**
  - Ensure HQ and branch hosts can reach the ISP test IP (for example, `203.0.113.10`).

### Implementation Checklist
- **LAN routing**
  - Configure SVIs or routed subinterfaces for VLANs 10, 20, 30, and 99 at HQ.
  - Configure a routed interface or SVI for `192.168.110.0/24` at the branch.
  - Verify intra-site connectivity between all VLANs at HQ and all hosts at the branch.
- **WAN edge**
  - Configure the HQ router interface towards the ISP using `10.255.21.1/30`.
  - Configure the ISP-side router interface using `10.255.21.2/30`.
  - Configure the HQ–Branch link interfaces using `10.255.30.1/30` (HQ) and `10.255.30.2/30` (Branch).
- **Routing configuration**
  - On HQ and Branch routers:
    - Enable OSPF in a single area.
    - Advertise all LAN interfaces and the HQ–Branch WAN link.
  - On HQ router:
    - Configure `ip route 0.0.0.0 0.0.0.0 10.255.21.2`.
    - Advertise a default route into OSPF towards the branch.
  - On ISP router:
    - Configure static route(s) for HQ and branch LANs pointing to `10.255.21.1`, or a single default towards a larger simulated internet as appropriate.

### IP Addressing Table (Aligned to Master Blueprint)

| Segment          | Purpose             | Subnet              | Example IPs                      |
|-----------------|---------------------|---------------------|----------------------------------|
| HQ VLAN 10      | HQ Users            | 192.168.10.0/24     | 192.168.10.1 (GW), .50–.150      |
| HQ VLAN 20      | HQ Voice            | 192.168.20.0/24     | 192.168.20.1 (GW), .50–.150      |
| HQ VLAN 30      | HQ Servers          | 192.168.30.0/24     | 192.168.30.1 (GW), .10–.50       |
| HQ VLAN 99      | HQ Management       | 192.168.99.0/24     | 192.168.99.1 (GW), .11–.50       |
| Branch Users    | Branch user LAN     | 192.168.110.0/24    | 192.168.110.1 (GW), .50–.150     |
| WAN P2P         | HQ–ISP link         | 10.255.21.0/30      | 10.255.21.1 (HQ), .2 (ISP)       |
| WAN P2P         | HQ–Branch link      | 10.255.30.0/30      | 10.255.30.1 (HQ), .2 (Branch)    |
| ISP Core        | Upstream network    | 203.0.113.0/24      | 203.0.113.10 (test host)         |

### Verification Commands
- **On HQ core/edge devices**
  - `show ip interface brief`
  - `show ip route`
  - `show vlan brief` (if using SVIs)
- **On Branch router**
  - `show ip interface brief`
  - `show ip route`
  - `show ip ospf neighbor` (or equivalent for your chosen protocol)
- **On ISP router**
  - `show ip interface brief`
  - `show ip route`
- **End-to-end tests**
  - `ping` between different VLANs within HQ.
  - `ping` from a branch user to HQ servers.
  - `ping` from both HQ and branch user VLAN hosts to `203.0.113.10`.
  - `traceroute` from HQ and branch towards the ISP test IP to confirm path selection.

### Convergence Analysis
- Measure and document:
  - How long it takes for routes to be withdrawn and re-learned when you fail the HQ–Branch or HQ–ISP links.
  - The impact on user application connectivity during these events.
- Use protocol-specific commands (for example, `debug ip ospf events`, where supported by your simulator) to:
  - Observe adjacency changes.
  - Track when new routes become active.
- Compare convergence behaviour between:
  - Static-only designs.
  - Designs that introduce a simple dynamic routing protocol.

Summarise your findings in terms of CCNA-level expectations for small enterprise deployments.

### Routing Design Diagram (Textual)

Use this text-based routing diagram as a reference when building your own drawings:

- **HQ Site**
  - `HQ-SW1` (core/distribution)
    - VLAN 10 SVI – `192.168.10.1/24`
    - VLAN 20 SVI – `192.168.20.1/24`
    - VLAN 30 SVI – `192.168.30.1/24`
    - VLAN 99 SVI – `192.168.99.1/24`
  - `HQ-R1` (WAN edge)
    - LAN-facing interface toward `HQ-SW1`.
    - WAN interface to ISP – `10.255.21.1/30`.
    - WAN interface to Branch – `10.255.30.1/30`.
- **Branch Site**
  - `BR-R1`
    - LAN interface – `192.168.110.1/24`.
    - WAN interface to HQ – `10.255.30.2/30`.
- **ISP**
  - `ISP-R1`
    - WAN interface to HQ – `10.255.21.2/30`.
    - Loopback or LAN – `203.0.113.10/24` (test host).

All routers participate in a simple dynamic routing domain between HQ and Branch, while the ISP uses static routes for lab simplicity.

### Failure Testing Requirements
- Remove or misconfigure the static default route on the HQ router and observe loss of external reachability from both HQ and Branch.
- Break the HQ–Branch link (administratively shut one side) and verify:
  - Loss of reachability between HQ and Branch user networks.
  - That local internet access from HQ still works.
- Break the HQ–ISP link and verify:
  - Loss of internet connectivity from both HQ and Branch.
  - That intra-enterprise routing between HQ and Branch remains operational.
- Misconfigure one LAN subnet mask or routing advertisement and analyse routing-table and connectivity symptoms.

Document each test scenario and findings in the dedicated `failure-testing.md` file for this lab.

### Troubleshooting Challenge Scenarios
Use the following challenge prompts to practise CCNA-level troubleshooting:

1. **Branch can reach HQ but not the ISP**
   - Hypothesise at least three possible root causes (for example, missing default route, incorrect redistribution, ACL on the HQ–ISP link).
   - Use a structured approach: check routing tables, interface status, and ACL counters.
2. **Intermittent loss of reachability after link flaps**
   - Investigate whether routing protocol timers or flapping interfaces are responsible.
   - Capture successive `show ip route` and `show ip ospf neighbor` outputs.
3. **Asymmetric routing through HQ**
   - Identify any paths where traffic to the branch returns via an unexpected route.
   - Discuss how this could impact stateful devices such as firewalls (conceptually).

For each scenario, record:
- Symptoms as seen from user endpoints.
- Supporting CLI outputs.
- Final root cause and corrective action.

### Operational Documentation Requirements
Produce brief but professional operational documentation for this lab, including:

- **Network overview**: One-paragraph summary of HQ–Branch–ISP connectivity.
- **Addressing reference**: Finalised table of subnets and key device IPs (aligned to the master blueprint).
- **Change and rollback plan**: High-level description of how routing changes would be deployed and backed out.
- **Monitoring and alerting**: What key metrics or events (interface down, adjacency loss, route changes) should be monitored in a real environment.

This documentation should be written so that a different engineer could operate and support the lab network without re-reading the full lab guide.

### Expected Outcomes
- Inter-VLAN routing operates correctly within HQ.
- HQ and Branch sites exchange routes and can reach each other’s user and server networks.
- Both sites have working outbound connectivity to the simulated ISP network.
- Routing tables on HQ, Branch, and ISP routers accurately reflect LAN and WAN prefixes.
- Learners can interpret static and dynamic routes, understand convergence behaviour, and reason about end-to-end path selection in a dual-site design.

### Reflection
Use this section to reflect on:

- **Routing design choices**: Why did you introduce a dynamic routing protocol between HQ and Branch? How does this impact convergence compared to static-only designs?
- **Failure domains**: Which failures affected only local connectivity, and which impacted the entire enterprise’s internet access?
- **Operational readiness**: How would you explain this design, including convergence characteristics, to an operations team taking over day-to-day support?

Capture your observations and design trade-offs as part of your learning portfolio.

