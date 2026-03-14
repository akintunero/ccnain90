## Advanced Infrastructure Lab 20 – Policy-Based Routing for Special Traffic Flows

### Scenario
Most of your enterprise traffic should follow the normal routing policy based on destination IP and standard routing protocols. However, a few important use cases do not fit cleanly into that model, for example:

- A backup circuit that should only be used for a specific partner application.  
- Traffic from a test lab that must exit via a low-cost internet link instead of the primary edge.  
- A small set of remote branches that should reach a legacy datacentre through a different path.

Rather than redesigning your entire routing topology, you have been asked to **evaluate and design limited use of policy-based routing (PBR)** to handle these special cases, while keeping the rest of the network on standard OSPF/eBGP decision making.

### Project Objectives

By the end of this project you should be able to:

- Identify when PBR is appropriate versus when a routing redesign is preferable.  
- Propose a small set of PBR policies for specific traffic flows and locations.  
- Describe how PBR interacts with existing OSPF/eBGP routing decisions.  
- Plan how to monitor and troubleshoot PBR behaviour over time.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, particularly:

- **3.2 Layer 3**
  - 3.2.d Describing policy-based routing and when it is used.  
  - 3.2.a Understanding normal path selection so that PBR exceptions are clearly defined.  

### Project Tasks

1. **Clarify business and technical requirements**
   - List the specific traffic flows that currently require special handling (source subnets, destinations, applications).  
   - For each flow, document the business reason for treating it differently (cost, performance, compliance, or lab/testing).  
   - Confirm which parts of the network should remain on standard routing with no PBR.
2. **Select PBR enforcement points**
   - Decide which routers or multilayer switches are best positioned to apply PBR (for example campus core, WAN edge, or branch routers).  
   - Ensure that PBR is applied as close as practical to the traffic source to avoid asymmetric paths.  
   - Note any hardware limitations that might affect PBR scale or performance.
3. **Design PBR policies**
   - For each use case, define match conditions (source IP, destination IP, DSCP, or interface) and the desired next-hop or outgoing interface.  
   - Plan a default behaviour when no PBR conditions match (fall back to normal routing table).  
   - Consider how overlapping policies are resolved and how configuration will remain readable.
4. **Plan interaction with routing protocols**
   - Describe how PBR policies will coexist with OSPF and eBGP route selection on the same devices.  
   - Decide whether PBR will ever override a safer or more resilient path and how to minimise that risk.  
   - Document how route changes (for example a new default route) might affect your PBR design.
5. **Define verification and rollback procedures**
   - Specify the commands and tools you will use to confirm that only the intended traffic is affected by PBR.  
   - Plan how to quickly disable PBR for a single policy or interface if problems occur.  
   - Outline logging or NetFlow sampling you would use to track PBR usage over time.

### Design Diagram (Text Form)

Use this to sketch where PBR fits into your network:

- **Core/Edge topology**
  - Core and distribution routers with standard routing relationships.  
  - WAN edge and any secondary links where alternative paths exist.
- **PBR enforcement points**
  - Routers or interfaces where PBR is applied, annotated with which flows are affected.  
- **Normal vs PBR paths**
  - For at least one use case, draw both the default routed path and the PBR-modified path, indicating why the change is desirable.

### Failure and What-If Analysis

Consider these scenarios and document the impact:

- A PBR next-hop becomes unreachable but the normal routed path is still valid.  
- A misconfigured PBR policy accidentally captures more traffic than intended.  
- A new application is introduced that reuses the same ports or addresses as an existing PBR policy.  
- An engineer forgets to update PBR when a WAN link is repurposed or decommissioned.

For each, explain:

- How traffic flows change and what symptoms users might see.  
- How you would detect the issue using show commands, logs, or flow data.  
- What design or procedural safeguards (for example, time-limited policies, change checklists) help prevent similar problems.

### Expected Outcomes

After completing this project you should be able to:

- Recommend whether PBR is appropriate for a given special-case routing requirement.  
- Design small, targeted PBR policies that do not unnecessarily complicate the wider network.  
- Provide guidance to operations on how to maintain and troubleshoot those policies safely.

### Reflection

Reflect on:

- How easily PBR use could grow beyond the original intent and what controls you would put in place to avoid that.  
- Which stakeholders (for example application owners or branch managers) need to understand when PBR is in effect.  
- Whether future projects (such as SD-WAN) might offer cleaner ways to solve the same traffic-steering problems.


