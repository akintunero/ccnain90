## Advanced Infrastructure Lab 14 – End-to-End Enterprise Services Design

### Scenario
Your company is modernising its enterprise network. The environment includes:

- A main campus with several wiring closets.
- A datacentre hosting internal applications.
- A small disaster recovery site.
- A single ISP for internet and partner connectivity.

The current design has grown organically. There are inconsistent trunk configurations, spanning tree issues, and a mix of static and dynamic routing. Wireless has been added in a piecemeal way and IP services such as NTP and NAT are not centrally planned.

You have been asked to propose a cohesive **Layer 2, Layer 3, wireless, and IP services** infrastructure that aligns with best practices and prepares the network for future growth.

### Project Objectives

By the end of this project you should be able to:

- Describe a stable Layer 2 and Layer 3 design for the campus and datacentre.  
- Show how OSPF and eBGP will be used for internal and external routing.  
- Explain how wireless access points discover and join controllers and how clients roam.  
- Plan key IP services such as NTP, NAT/PAT, first hop redundancy, and multicast where appropriate.

### Technologies and Design Topics in Scope

This project draws from the ENCOR Infrastructure section:

- **Layer 2**
  - 802.1Q trunking, static and dynamic EtherChannel.
  - Spanning tree (RSTP and MST) for loop free redundancy.
- **Layer 3**
  - OSPF design for multiple areas, summarisation, and filtering.
  - Conceptual comparison with EIGRP.
  - Basic eBGP to an ISP using directly connected neighbours.
- **Wireless**
  - RF basics, AP modes, antenna types.
  - AP discovery and join process.
  - Layer 2 and Layer 3 roaming principles.
  - Troubleshooting client connectivity at a high level.
- **IP Services**
  - NTP design.
  - NAT/PAT for internet access.
  - First hop redundancy protocols such as HSRP or VRRP.
  - Multicast concepts (PIM and IGMP).

### Project Tasks

1. **Stabilise Layer 2**
   - Choose a spanning tree mode (for example RSTP or MST) for the campus.  
   - Define which switches act as primary and secondary roots for each VLAN or instance.  
   - Decide where EtherChannels are appropriate and how they will be configured.
2. **Design Layer 3 routing**
   - Plan OSPF areas for campus, datacentre, and DR site.  
   - Decide where summarisation will occur to reduce routing table size.  
   - Identify where eBGP will be used to connect to the ISP and how routes will be exchanged.
3. **Plan wireless infrastructure**
   - Select AP deployment model (centralised controller, distributed, or branch friendly).  
   - Describe how APs will discover and join controllers.  
   - Define roaming behaviour between access points and across subnets.
4. **Define IP services**
   - Choose authoritative NTP sources and describe the NTP hierarchy.  
   - Design NAT/PAT at the edge, including which internal ranges will be translated.  
   - Decide which VLANs will use first hop redundancy and where the active gateways will live.  
   - Identify any multicast use cases and where PIM or IGMP would be required.
5. **Document the end-to-end flow**
   - For a typical user, describe the full path of traffic from wireless or wired access through the campus, to datacentre applications, and out to the internet.

### Design Diagram (Text Form)

Use this to build a logical diagram:

- **Campus**  
  - Access switches connecting wired users and APs.  
  - Distribution or core switches providing routing, with redundant links.  
  - VLANs and SVIs for different user and server segments.
- **Datacentre and DR**
  - Routers or layer 3 switches connecting into the OSPF domain.  
  - Optional separate area numbers and summarisation boundaries.
- **Edge and ISP**
  - WAN edge router(s) that run eBGP with the ISP.  
  - NAT and first hop redundancy located here or on the core, depending on your design.

### Failure and What-If Analysis

Consider:

- Spanning tree root failure in the main campus.  
- Loss of an EtherChannel link bundle.  
- OSPF adjacency failure between campus and datacentre.  
- eBGP neighbour failure to the ISP.

For each, describe:

- Expected network behaviour.  
- How users are impacted.  
- Which design choices help contain or minimise the issue.

### Expected Outcomes

After completing this project you should be able to:

- Explain your Layer 2 and Layer 3 design decisions to another engineer.  
- Show how wireless, IP services, and routing work together to support applications.  
- Identify where further improvements such as additional redundancy or better summarisation might be useful.

### Reflection

Reflect on:

- Which parts of the infrastructure design were most constrained by existing hardware or topology.  
- How you could phase the migration from the current state to your target design with minimal downtime.  
- Which assurance and monitoring tools you would rely on during and after the migration.

