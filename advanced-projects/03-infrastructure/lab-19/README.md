## Advanced Infrastructure Lab 19 – Designing a Simple but Robust eBGP Edge

### Scenario
Your enterprise currently connects to a single ISP using static default routes on a WAN edge router. As the number of sites and services has grown, limitations of this approach are becoming clear:

- Failures at the ISP edge are hard to diagnose without visibility into BGP.  
- Engineers want the option to advertise specific prefixes in future (for example for VPNs or partner links).  
- There is interest in adding a second ISP for resilience, but the team has little eBGP experience.

In this lab you will design a **basic eBGP edge** between your network and one ISP that remains easy to operate and supports future growth. Internal routing should stay simple (for example OSPF inside, eBGP only at the edge).

### Project Objectives

By the end of this project you should be able to:

- Describe a simple eBGP design between a single enterprise edge and a directly connected ISP.  
- Decide which prefixes to advertise and how to control what you accept from the ISP.  
- Explain how internal routing (for example OSPF) and eBGP interact at the edge.  
- Outline how your design could evolve to support a second ISP later.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, especially:

- **3.2 Layer 3**
  - 3.2.c Configuring and verifying eBGP between directly connected neighbours (best-path selection algorithm and neighbour relationships).  
  - 3.2.b Use of OSPFv2/v3 internally as a reference internal protocol redistributing towards the edge.  
- **3.3 IP services (context)**
  - NAT/PAT and first-hop redundancy placement at or near the edge.

### Project Tasks

1. **Define edge roles and routing domains**
   - Identify which router(s) will run eBGP with the ISP.  
   - Decide where the boundary between internal routing (for example OSPF) and external eBGP will sit.  
   - List the internal prefixes that may need internet or partner connectivity.
2. **Design eBGP neighbour relationships**
   - Specify IP addressing for the link between your edge router and the ISP (for example a /30 or /31).  
   - Define eBGP neighbour configuration basics (ASN values, update-source, timers if needed).  
   - Decide what you will accept from the ISP (for example a default route only, or selected prefixes).
3. **Plan route advertisement and redistribution**
   - Choose which internal prefixes will be advertised to the ISP (for example an aggregate for all internal networks).  
   - Decide whether internal OSPF routes will be summarised before being redistributed into eBGP.  
   - Describe how the edge router will learn internal routes (for example via OSPF adjacency or static routes).
4. **Consider scale and second-ISP readiness**
   - Briefly discuss how a future second ISP would connect (for example second eBGP neighbour on another router).  
   - Outline how you might use local preference, AS-path prepending, or MED in a dual-ISP design.  
   - Note any additional monitoring or logging you would put in place at the edge.
5. **Document operational checks**
   - Create a short checklist of commands and metrics to verify that eBGP and internal routing are working:
     - BGP neighbour state.  
     - Received and advertised routes.  
     - Default route presence on key internal routers.  
   - Include guidance for what to check first if users report loss of internet connectivity.

### Design Diagram (Text Form)

Use this to sketch a routing and edge view:

- **Internal domain**
  - Core or distribution routers running OSPF, summarising towards the edge.  
- **Edge router**
  - Interfaces facing the internal core and the ISP.  
  - eBGP neighbour relationship to the ISP, with notes on ASN and key policies.  
- **ISP cloud**
  - A simple representation of the ISP network from which you receive a default or limited set of routes.

### Failure and What-If Analysis

Consider and describe behaviour under these conditions:

- The eBGP session to the ISP drops but the physical link stays up.  
- The edge router loses OSPF adjacency to the internal core but eBGP remains up.  
- A misconfiguration causes more specific internal prefixes to be advertised than intended.  
- The ISP begins advertising a full table unexpectedly instead of a default route.

For each scenario, explain:

- How routing changes on the edge and in the internal network.  
- Which alarms, logs, or metrics would reveal the issue.  
- What configuration safeguards (for example prefix-lists, max-prefix, or route-maps) you would use to reduce risk.

### Expected Outcomes

After completing this project you should be able to:

- Describe and justify a minimal yet robust eBGP edge design for a single ISP.  
- Explain how internal OSPF and external BGP work together without unnecessary complexity.  
- Identify key safeguards and checks that should be in place at any enterprise internet edge.

### Reflection

Reflect on:

- How much BGP complexity your environment actually needs today versus in the future.  
- Which aspects of BGP you would prioritise for deeper study based on this design.  
- How you would explain your edge routing approach to a security or operations team.


