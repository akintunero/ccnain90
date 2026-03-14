## Advanced Infrastructure Lab 26 – Multicast Design and RPF Considerations

### Scenario
Your organisation is planning to introduce multicast-based services such as:

- Live video streams for internal town halls.  
- Market data feeds for a trading or analytics team.  
- Multicast-based application updates or telemetry.  

Today the network primarily carries unicast traffic, and multicast is either disabled or inconsistently configured. There is concern about flooding, potential loops, and the impact on existing routing. In this lab you will design where and how multicast protocols such as PIM and IGMP should be used, and how Reverse Path Forwarding (RPF) checks will behave in your topology.

### Project Objectives

By the end of this project you should be able to:

- Decide which parts of the network should support multicast and which should remain unicast-only.  
- Select appropriate multicast routing modes (for example PIM Sparse Mode) and where to run them.  
- Explain how RPF checks work in your design and how routing choices affect multicast forwarding.  
- Identify potential risks and safeguards when enabling multicast in an existing network.

### Technologies and Design Topics in Scope

This project focuses on the multicast-related portion of the Infrastructure  (3.3):

- **3.3 IP services**
  - 3.3.d Describing multicast protocols such as RPF check, PIM SM, IGMP v2/v3, SSM, bidirectional PIM, and MSDP (at a design and behaviour level).  

### Project Tasks

1. **Identify multicast use cases and scope**
   - List the specific applications or services that will use multicast and where their sources and receivers sit (campus, datacentre, branches).  
   - Determine whether these use cases require enterprise-wide multicast or can be contained within certain segments.  
   - Decide which devices will act as multicast sources and which will act as receivers.
2. **Choose multicast routing modes**
   - Decide whether PIM Sparse Mode (PIM-SM), Source-Specific Multicast (SSM), or other modes are appropriate for each use case.  
   - Identify where Rendezvous Points (RPs) would be placed if PIM-SM is used.  
   - Consider whether MSDP is needed for multiple RPs or inter-domain scenarios.
3. **Plan RPF and routing interaction**
   - Describe how your unicast routing (OSPF/eBGP) will influence RPF checks for multicast sources.  
   - Identify any asymmetric routing paths that could cause RPF failures.  
   - Propose adjustments (for example summarisation boundaries or static RPF exceptions) if needed.
4. **Define edge behaviour and IGMP policy**
   - Decide where IGMP snooping and IGMP queriers are required in the campus.  
   - Plan how receivers (for example user VLANs) will signal interest in multicast groups.  
   - Consider controls to prevent unwanted or excessive multicast group joins.
5. **Document rollout and validation steps**
   - Outline a phased approach to enabling multicast in a lab, then limited production, then broader rollout.  
   - Define the key tests (for example end-to-end group join, failover, and source move) you will run.  
   - List the show commands and counters you will rely on to validate correct multicast forwarding.

### Design Diagram (Text Form)

Use this to sketch your multicast design:

- **Source locations**
  - Servers or devices that originate multicast traffic and their VLANs/subnets.  
- **Core and RPs**
  - Routers running PIM and, if applicable, acting as Rendezvous Points.  
- **Receiver segments**
  - VLANs and subnets where receivers join groups via IGMP, indicating which switches perform IGMP snooping.

### Failure and What-If Analysis

Consider and describe behaviour for these scenarios:

- A unicast routing change causes RPF checks to fail for a key multicast source.  
- An RP fails or becomes unreachable.  
- An access switch misconfiguration disables IGMP snooping, leading to multicast flooding.  
- A new application begins using multicast without prior design review.

For each, explain:

- How multicast traffic flow changes and what impact users may see.  
- Which logs, counters, or monitoring views would reveal the issue.  
- What design or operational measures mitigate the problem (for example secondary RPs, better routing design, or access controls).

### Expected Outcomes

After completing this project you should be able to:

- Present a multicast design that fits your enterprise’s actual needs without overcomplicating the network.  
- Show how RPF behaviour depends on unicast routing and why that matters.  
- Provide clear guidance for enabling, monitoring, and troubleshooting multicast services.

### Reflection

Reflect on:

- Whether multicast truly adds value for your environment compared to unicast alternatives.  
- How you would keep multicast configuration and documentation understandable for operations.  
- What additional lab work or training would be needed before rolling multicast into production.


