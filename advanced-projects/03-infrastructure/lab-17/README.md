## Advanced Infrastructure Lab 17 – OSPFv2/v3 Area and Summarisation Strategy

### Scenario
The enterprise has grown from a single-campus OSPF design into a network that now includes:

- A main campus with multiple distribution blocks.  
- A datacentre with its own routing domain.  
- A small DR site connected over a WAN link.  

OSPF has been extended incrementally without a clear area plan. Some links run in area 0, others in arbitrary non-backbone areas, and summarisation is inconsistent. Troubleshooting routes between sites is becoming difficult and route tables are larger than necessary.

In this lab you will design a **clean OSPFv2/v3 area structure and summarisation strategy** that supports campus, datacentre, and DR connectivity while remaining easy to operate and extend.

### Project Objectives

By the end of this project you should be able to:

- Propose an OSPF area design that separates campus, datacentre, and DR while respecting backbone rules.  
- Identify where summarisation should occur to keep routing tables manageable.  
- Explain how OSPFv2 and OSPFv3 can be used together for dual-stack deployments.  
- Describe how your OSPF design handles link failures and maintains stable paths.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, focusing on Layer 3:

- **3.2 Layer 3**
  - 3.2.a Comparing routing concepts of EIGRP and OSPF (advanced distance vector vs link state, load balancing, path selection, metrics, and area types).  
  - 3.2.b Configuring simple OSPFv2/v3 environments with multiple normal areas, summarisation, and filtering (including neighbour adjacency, point-to-point and broadcast network types, and passive-interface).  

### Project Tasks

1. **Map the current OSPF topology**
   - Draw a high-level view of routers in the campus, datacentre, and DR sites.  
   - Note which interfaces and links currently belong to area 0 and which belong to other areas.  
   - Identify any non-backbone areas that are not directly connected to area 0.
2. **Design the target area structure**
   - Decide which routers will form the backbone (area 0).  
   - Assign campus, datacentre, and DR segments to appropriate normal areas.  
   - Determine where ABRs will sit and document their roles.  
   - Consider whether any stub or NSSA areas would be useful and justify your decision.
3. **Plan summarisation and filtering**
   - Choose summarisation points at ABRs to reduce the number of prefixes advertised between areas.  
   - Decide which internal routes should be summarised and which should remain specific.  
   - Document any simple prefix filtering that might be needed to prevent unnecessary routes from crossing areas.
4. **Define adjacency and network type considerations**
   - For each OSPF link (campus, datacentre, DR, WAN), decide whether it should run as broadcast, point-to-point, or NBMA.  
   - Note where passive-interface should be used (for example on user-facing interfaces).  
   - Ensure that adjacency formation remains predictable and avoids unnecessary DR/BDR elections on point-to-point links.
5. **Document migration and validation steps**
   - Outline a phased plan to transition from the current ad-hoc area layout to your target design.  
   - List the key verification steps at each phase (for example route counts on core routers, end-to-end reachability between sites).  
   - Include rollback considerations if unexpected reachability issues occur.

### Design Diagram (Text Form)

Use this description to produce a routing-focused diagram:

- **Area 0 (Backbone)**
  - Core routers connecting campus, datacentre, and DR ABRs.  
  - Links and subnets that should always remain in the backbone.
- **Campus area(s)**
  - Distribution routers acting as ABRs between area 0 and campus access segments.  
  - Summaries advertised from campus into area 0.
- **Datacentre and DR areas**
  - Routers and subnets grouped into dedicated areas for server and DR infrastructure.  
  - Summarisation boundaries and any special area types (for example stub or NSSA).

### Failure and What-If Analysis

Consider these scenarios and describe how your OSPF design behaves:

- A backbone link between two core routers fails, splitting area 0 into two parts.  
- An ABR between the campus area and area 0 fails.  
- A misconfiguration assigns an access router interface to the wrong OSPF area.  
- A summarisation change accidentally hides a more specific route needed for reachability.

For each scenario, explain:

- How OSPF recalculates paths and what routes remain in the table.  
- Which parts of the network lose connectivity, if any.  
- What monitoring indicators (for example adjacency state, LSA changes, route counts) would highlight the problem.  
- How your design choices minimise impact or make troubleshooting easier.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear OSPFv2/v3 area and summarisation design for a multi-site enterprise.  
- Justify your backbone and area placement decisions with respect to scalability and resilience.  
- Predict how changes in one area affect route visibility and path selection elsewhere.

### Reflection

Reflect on:

- Which aspects of OSPF area design are most likely to cause operational issues if not documented.  
- How you would teach a junior engineer to read and understand your OSPF design.  
- What tooling or visualisations would help maintain confidence in the routing design as the network grows.


