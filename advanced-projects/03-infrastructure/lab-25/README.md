## Advanced Infrastructure Lab 25 – First-Hop Redundancy and Gateway Failover Design

### Scenario
Your campus and datacentre rely heavily on default gateway availability for user and server VLANs. Recent incidents have shown that:

- When a distribution switch fails, some VLANs lose their default gateway entirely.  
- HSRP/VRRP priorities are inconsistent, leading to unexpected active gateways.  
- Operations staff are unsure how traffic flows change when a gateway fails over.

In this lab you will design a **first-hop redundancy strategy** using protocols such as HSRP or VRRP across key VLANs, and describe how failover affects traffic flows between users, servers, and the rest of the network.

### Project Objectives

By the end of this project you should be able to:

- Select appropriate first-hop redundancy protocols (for example HSRP or VRRP) for your environment.  
- Define active and standby gateway roles per VLAN or group of VLANs.  
- Explain how gateway failover interacts with routing and spanning-tree choices.  
- Document how users and applications experience gateway failures and recovery.

### Technologies and Design Topics in Scope

This project draws from the IP services part of the Infrastructure  (3.3):

- **3.3 IP services**
  - 3.3.c Configuring first-hop redundancy protocols such as HSRP and VRRP.  
- **Related context**
  - Interaction with STP root placement and Layer 3 routing at the distribution or core layer.

### Project Tasks

1. **Identify critical VLANs and gateways**
   - List user, server, management, and other key VLANs that require high gateway availability.  
   - Note which devices currently act as default gateways (for example distribution switches or core routers).  
   - Capture any existing HSRP/VRRP configurations and priorities.
2. **Design the first-hop redundancy model**
   - Decide which devices will participate in HSRP/VRRP groups for each VLAN.  
   - Define active and standby roles, including how priorities and pre-emption will be configured.  
   - Consider load-sharing strategies (for example different VLANs using different active gateways).
3. **Align FHRP with Layer 2 and routing design**
   - Ensure STP root placement and active gateways are aligned to avoid suboptimal traffic paths.  
   - Describe how routing protocols (for example OSPF) learn about the gateway IPs and next hops.  
   - Consider how FHRP behaves across multiple distribution blocks if applicable.
4. **Plan verification and monitoring**
   - Specify commands and tests to verify correct FHRP operation (for example active/standby status, timers, track objects).  
   - Define health checks or tracking (interfaces or routes) that will influence gateway priority.  
   - Identify logging and alerting you would want when a gateway changes state.
5. **Document failover behaviour**
   - For at least two representative VLANs, describe:
     - The normal traffic path when the primary gateway is up.  
     - What happens when the primary gateway fails (including ARP and routing updates).  
     - How quickly clients should recover and what they might observe during the event.

### Design Diagram (Text Form)

Use this to sketch the FHRP-related topology:

- **Distribution/core layer**
  - Two or more devices providing default gateways for multiple VLANs, with FHRP groups labelled.  
  - Links to access switches and upstream routing peers.
- **Access layer and VLANs**
  - Example user and server VLANs, showing which FHRP virtual IPs serve as gateways.  
  - Indication of how STP and FHRP roles align.

### Failure and What-If Analysis

Consider these scenarios and describe the outcomes:

- Failure of the primary FHRP router for a busy user VLAN.  
- Loss of an upstream WAN or core link on the device currently acting as active gateway.  
- Misconfigured FHRP priorities causing the wrong device to become active.  
- A new VLAN added without FHRP configured consistently across distribution switches.

For each, explain:

- How FHRP should react and which device becomes active.  
- How user and server traffic is affected and for how long.  
- What monitoring and documentation would help operations respond correctly.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear first-hop redundancy design for user and server VLANs.  
- Justify FHRP placement and configuration choices relative to STP and routing.  
- Provide operations with guidance on validating and troubleshooting gateway failover events.

### Reflection

Reflect on:

- How much complexity is appropriate in your FHRP design (for example load sharing vs simplicity).  
- Which parts of the design are most sensitive to configuration drift.  
- How you would ensure new VLANs and future sites consistently follow the FHRP strategy.


