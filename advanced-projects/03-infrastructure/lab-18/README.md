## Advanced Infrastructure Lab 18 – Choosing Between EIGRP and OSPF

### Scenario
Your enterprise network currently uses a mixture of EIGRP and OSPF inherited from previous mergers:

- The campus core and access use OSPF in a single area.  
- The datacentre team prefers EIGRP and runs it internally.  
- The DR site connects over a WAN that was built with EIGRP as the primary protocol.  

As the network grows, operational complexity and confusion are increasing. Different teams favour different protocols, and there is no clear rationale for where each belongs. Leadership has asked you to **compare EIGRP and OSPF in the context of your design** and recommend a protocol strategy for campus, datacentre, DR, and WAN.

### Project Objectives

By the end of this project you should be able to:

- Compare how EIGRP and OSPF behave in terms of convergence, load balancing, and scalability.  
- Decide which parts of the network should standardise on which protocol (if any mix remains).  
- Identify where redistribution between EIGRP and OSPF is required and what risks it introduces.  
- Explain your routing protocol decisions to both technical and non-technical stakeholders.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, with emphasis on Layer 3:

- **3.2 Layer 3**
  - 3.2.a Comparing routing concepts of EIGRP and OSPF (advanced distance vector vs link state, load balancing, path selection, metrics, and area types).  
  - 3.2.b Simple OSPFv2/v3 environments used as a reference when weighing protocol trade-offs.  

### Project Tasks

1. **Document the current protocol landscape**
   - Identify where OSPF is running today (areas, key routers, and major prefixes).  
   - Identify where EIGRP is running (autonomous systems, major route domains).  
   - Note any existing redistribution points and which routes are exchanged.
2. **Analyse design requirements per domain**
   - For the campus, list requirements such as fast convergence, support for multiple areas, and ease of operations.  
   - For the datacentre, consider multi-path capabilities, summarisation, and future overlay plans.  
   - For DR and WAN, consider link quality, bandwidth, and manageability.
3. **Compare EIGRP and OSPF against those requirements**
   - For each domain (campus, datacentre, DR/WAN), evaluate:
     - Convergence characteristics.  
     - Metric flexibility and path control.  
     - Operational familiarity of the team.  
   - Summarise pros and cons of using a single protocol everywhere versus a mixed approach.
4. **Propose a routing protocol strategy**
   - Decide if the network should converge on OSPF, converge on EIGRP, or retain a mix with clear boundaries.  
   - Define where any redistribution will occur and which direction(s) routes should flow.  
   - Outline summarisation points to keep routing tables manageable across protocol boundaries.
5. **Plan validation and transition**
   - Describe how you would test your proposed protocol strategy in a lab or pilot environment.  
   - Provide a high-level sequence of steps to migrate from the current state to your target design.  
   - Include checkpoints where you verify reachability and route correctness.

### Design Diagram (Text Form)

Use this to create a routing-protocol view of the network:

- **Campus block**
  - Core and distribution routers, showing which protocol they run and how they connect to the backbone.  
- **Datacentre block**
  - Internal routing domain and its connection(s) to the core.  
- **DR and WAN block**
  - Edge routers, WAN links, and which routing protocol runs over those links.  
- **Redistribution points**
  - Routers that exchange routes between EIGRP and OSPF, with notes on direction and summarisation.

### Failure and What-If Analysis

Consider these scenarios and describe the impact on your design:

- A redistribution router between EIGRP and OSPF fails.  
- A route leak occurs because redistribution was configured too broadly.  
- An OSPF area is added in the campus without updating the protocol strategy.  
- A new remote site is connected and engineers must decide which protocol to use.

For each case, explain:

- How routes will change and which parts of the network may be affected.  
- What metrics, tags, or summarisation techniques you would use to limit problems.  
- How your chosen strategy makes these issues easier or harder to manage.

### Expected Outcomes

After completing this project you should be able to:

- Clearly articulate why EIGRP, OSPF, or a specific combination is appropriate for each part of your network.  
- Identify and mitigate the main risks associated with protocol mixing and redistribution.  
- Provide a concise recommendation that network leadership can approve.

### Reflection

Reflect on:

- Whether your organisation benefits more from protocol diversity or from standardisation.  
- How you would document your routing protocol choices so that future engineers understand the rationale.  
- What additional labs or testing you would run before committing to a long-term protocol strategy.


