## Lab 47 – Multi-Site Services and Shared Infrastructure

### Scenario – Designing Shared Services Across Sites
The enterprise wants to centralise services such as DNS, DHCP, and key applications. Your task is to describe how shared services will be made available across sites, how routing and security support this, and what trade‑offs exist.

### Network Architecture Overview
- **Scope**: Headquarters plus multiple branches and remote offices.
- **Technologies in use**:
  - VLAN-based segmentation using the standard VLAN ID plan.
  - Inter-VLAN routing and WAN connectivity using the established addressing blueprint.
  - Security controls (ACLs, basic device hardening, logging).
- **Design goals**:
  - Standardised IP addressing and VLAN usage across all sites.
  - Clear separation of roles (core, distribution, access, WAN edge).
  - A repeatable, automation-friendly configuration model with predictable convergence behaviour during failures.

### Technical Requirements
- **Addressing strategy**
  - Use `10.X.0.0/24` ranges for enterprise site LANs (HQ, branches, remote offices).
  - Reserve `192.168.X.0/24` ranges for lab, test, or small isolated networks.
  - Use `10.255.X.0/30` exclusively for WAN point-to-point links.
  - Use `203.0.113.0/24` and `198.51.100.0/24` for ISP simulation and multi-ISP scenarios.
- **Design documentation**
  - Define site types (HQ, large branch, small branch, remote worker hub).
  - For each site type, specify:
    - VLANs used.
    - Subnet allocations.
    - WAN connectivity model.
    - Security and monitoring requirements.
  - Capture expected convergence behaviour for:
    - Loss of a site WAN link.
    - Loss of a primary ISP connection at HQ.
- **Automation considerations**
  - Identify configuration elements suitable for templates (for example, VLAN definitions, interface roles, base routing and security policies).
  - Propose how tools such as Ansible, Python scripts, or controller-based solutions could push these templates.
  - Define how routing parameters (for example, administrative distance, default route origination) will be expressed in templates to achieve consistent convergence.

### Implementation Checklist
- **High-level design**
  - Create a site matrix showing each location, its role, and corresponding IP ranges.
  - Define a summarisation strategy for routing (for example, aggregating site subnets).
  - Describe which routing protocol(s) are used in the WAN and how default routes are handled.
- **Standard templates**
  - Draft a conceptual “access switch template”, “WAN edge template”, and “security template” at a documentation level.
  - Ensure all templates conform to the master addressing blueprint and VLAN plan.
  - Include standardised interface descriptions, IP addressing, and baseline routing/ACL constructs.
- **Convergence planning**
  - Document expected path selection for:
    - Normal operation (all links and ISPs up).
    - Primary ISP failure at HQ.
    - Single branch WAN link failure.
  - Define timer and failover expectations at a CCNA level (for example, using default OSPF/EIGRP timers).
- **Automation workflow (conceptual)**
  - Outline how configuration data (site codes, IP blocks, device roles) would be represented in data files (YAML/JSON).
  - Describe how an automation tool would render and deploy device configurations from these data sources and templates.
  - Include a high-level description of pre-deployment validation (for example, linting data files, dry-run modes).

### IP Addressing Table (Aligned to Master Blueprint)

| Site Role      | VLAN | Purpose      | Example Subnet       | Notes                                         |
|----------------|------|-------------|----------------------|-----------------------------------------------|
| HQ             | 10   | Users       | 10.10.0.0/24         | Core user subnet at HQ                        |
| HQ             | 30   | Servers     | 10.30.0.0/24         | Data centre servers                           |
| Branch (large) | 10   | Users       | 10.110.0.0/24        | Users at large branch                         |
| Branch (small) | 10   | Users       | 10.210.0.0/24        | Users at small branch                         |
| Any site       | 99   | Management  | 10.99.0.0/24 (HQ)    | Aggregated management core at HQ              |
| WAN P2P        | —    | Site links  | 10.255.X.0/30        | One /30 per point-to-point WAN connection     |
| ISP-1          | —    | Internet    | 203.0.113.0/24       | Primary simulated ISP                         |
| ISP-2          | —    | Internet    | 198.51.100.0/24      | Secondary simulated ISP                       |

### Verification Commands
Because this is a design and documentation lab, focus verification on:

- Validating that your addressing plan can be summarised effectively for routing.
- Ensuring that no address ranges overlap across sites.
- Confirming that proposed templates align with CCNA-level device capabilities.

Example commands you might plan to use in real deployments:
- `show ip route` and `show ip route summary` for route aggregation.
- `show vlan brief` and `show ip interface brief` to ensure consistent templates.

### Convergence Analysis

At a design-documentation level, describe:

- How routing should converge when:
  - A branch loses its single WAN link.
  - HQ loses its primary ISP but retains a secondary ISP (using `203.0.113.0/24` and `198.51.100.0/24`).
- Which devices originate default routes and under what conditions.
- How summarisation at HQ affects failure visibility and troubleshooting at branches.

If you later build this design in a simulator, plan to measure:

- Time from link failure to restored connectivity via backup paths.
- Impact on existing flows (for example, brief packet loss vs. sustained outage).

Capture these expectations in your design so that operations teams know what “normal” convergence looks like.

### Routing Design Diagram (Textual)

Use the following logical diagram as a reference:

- **HQ Core**
  - `HQ-CORE` with VLANs 10 (users), 30 (servers), 99 (management).
  - Connects to `HQ-WAN1` (primary WAN edge) and optionally `HQ-WAN2` (secondary ISP edge).
- **Branches**
  - `BR1-R1`, `BR2-R1`, etc., each with:
    - User VLAN 10 at the site (`10.110.0.0/24`, `10.210.0.0/24`, and so on).
    - Point-to-point WAN link to HQ core or WAN edge using `10.255.X.0/30`.
- **ISPs**
  - `ISP1-R` with subnet `203.0.113.0/24`.
  - `ISP2-R` with subnet `198.51.100.0/24`.

All site WAN routers participate in a simple dynamic routing domain with summarisation at HQ towards the core and controlled default route origination towards branches.

### Failure Testing Requirements
Conceptually plan for:

- Overlapping IP allocations between two sites and how this would be detected and resolved.
- Misaligned WAN addressing (incorrect /30 usage) and impact on routing.
- Template errors that push incorrect VLAN or IP assignments to multiple devices.
- Failure of a primary ISP at HQ and how branches should continue to operate (for example, via secondary ISP or reduced-services mode).
- Loss of a single branch’s WAN link and how local services should continue while WAN-dependent services fail.

Describe how monitoring, change control, and automation testing (for example, dry-run modes and staged rollouts) would reduce these risks.

### Troubleshooting Challenge Scenarios

1. **Branch reachable, but internet unreachable after a change**
   - Hypothesise template or routing changes that might cause this.
   - Identify what monitoring and documentation would help quickly isolate the issue.
2. **Multiple branches reporting slow failover to backup ISP**
   - Discuss which routing protocol or design parameter might be responsible (for example, default timers, missing tracking).
3. **Unplanned overlap between a lab subnet and a production site subnet**
   - Explore how this could be detected (for example, via IPAM tools, route tables, or monitoring alerts).

For each scenario, design a high-level troubleshooting workflow that a CCNA-level engineer could follow using your documentation and templates.

### Operational Documentation Requirements

Produce design-focused operational documentation including:

- **Site catalogue** – list of sites, roles, and key subnets.
- **Routing and failover behaviour** – description of normal and degraded-state paths.
- **Template ownership and change process** – who owns each template and how changes are approved, tested, and rolled back.
- **Monitoring and alerting requirements** – which events (route changes, link flaps, failover activations) must generate alerts.

The goal is to make your design supportable by an operations team with upper-bound CCNA skills.

### Expected Outcomes
- A coherent, CCNA-aligned multi-site addressing and VLAN plan.
- Clear documentation of reusable configuration patterns.
- Documented convergence expectations and failover behaviour for key failure modes.
- An automation-friendly conceptual model that could be implemented with tools of your choice and safely operated by a CCNA-level team.

### Reflection
Reflect on:

- **Scalability**: How does the proposed addressing and VLAN plan scale as sites are added?
- **Operational simplicity**: How do templates reduce configuration drift between sites?
- **Convergence and resilience**: Are your documented failover behaviours realistic and supportable at CCNA level?
- **Automation readiness**: What additional information (inventory, metadata, version control, testing) would be required to safely automate changes?

These reflections will prepare you for the remaining advanced design and automation labs (47–50).

