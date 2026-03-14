## Advanced Infrastructure Lab 28 – Infrastructure Scalability, Failure Modes, and Migration Planning

### Scenario
Your enterprise leadership is planning for significant growth over the next three to five years:

- User counts may double as new teams and acquisitions are integrated.  
- Additional applications will be deployed in the datacentre and possibly the cloud.  
- More remote sites and partners will connect to the WAN edge.  

They want confidence that the infrastructure design you have built through earlier labs will **scale, fail gracefully, and be migratable** as new requirements emerge. In this lab you will analyse your current design from three angles: scalability, failure modes, and migration paths.

### Project Objectives

By the end of this project you should be able to:

- Assess how well your existing Layer 2, Layer 3, and IP services design scales with growth.  
- Describe the most important failure modes and how the design contains or exposes them.  
- Propose a phased migration plan for major future changes (for example more sites, cloud, or SD-WAN).  
- Communicate these findings in a concise, design-review friendly format.

### Technologies and Design Topics in Scope

This capstone Infrastructure project synthesises all of 3.x:

- **3.1 Layer 2** – STP, trunking, and EtherChannel limits and design boundaries.  
- **3.2 Layer 3** – OSPF/EIGRP, eBGP, and PBR design considerations at scale.  
- **3.3 IP services** – NTP, NAT/PAT, FHRP, and multicast implications for larger and more complex topologies.

### Project Tasks

1. **Scalability assessment**
   - For each major domain (Layer 2, routing, wireless, IP services), estimate how many:
     - VLANs, SSIDs, and subnets your design can realistically handle.  
     - OSPF areas, BGP neighbours, and routes are supportable without major redesign.  
     - NAT rules, FHRP groups, and multicast groups can be maintained operationally.  
   - Identify clear thresholds beyond which a redesign or new technology (for example SD-Access or SD-WAN) would be needed.
2. **Failure modes analysis**
   - List the top 5–10 failure scenarios from previous labs (for example core failure, edge failure, routing protocol issues, NTP drift, NAT misconfiguration).  
   - For each scenario, summarise:
     - Blast radius (which sites/services are impacted).  
     - Expected recovery time and complexity.  
     - How your current design helps or hinders containment.
3. **Migration planning**
   - Choose one or two plausible future initiatives, such as:
     - Moving some applications to the cloud.  
     - Adopting SD-WAN for branch connectivity.  
     - Introducing a campus fabric or new security segmentation.  
   - For each initiative, outline:
     - Which existing components can be reused as-is.  
     - Which must be upgraded or replaced.  
     - A high-level sequence of migration phases that minimises risk.
4. **Risk and technical debt review**
   - Identify any areas where short-term design decisions have created technical debt (for example legacy address plans, protocol mixes, or manual processes).  
   - Categorise risks (high/medium/low) based on business impact and likelihood.  
   - Suggest interim mitigations that can be implemented before a full redesign.
5. **Prepare an executive-friendly summary**
   - Draft a 1–2 page summary that:
     - States the current design’s strengths.  
     - Highlights key risks and limitations.  
     - Proposes a realistic roadmap for improvements.  
   - Ensure the language is understandable by non-network specialists while still accurate.

### Design Diagram (Text Form)

Use this to outline a “future-ready” view of the network:

- **Current state**
  - Core, datacentre, DR, and WAN edge as presently designed.  
- **Growth vectors**
  - Where additional sites, services, or cloud connectivity will attach.  
- **Potential future technologies**
  - Indicate where SD-WAN, SD-Access, or more advanced automation could slot into the design.

### Failure and What-If Analysis

Consider these bigger-picture questions and answer them based on your design:

- What happens if traffic volume doubles across the WAN and core?  
- How does the design cope if a whole building or site goes offline unexpectedly?  
- How easy is it to bring a new site online following your current standards?  
- What is the impact if a key IP service (for example NTP or DNS) is disrupted?

For each, explain:

- Whether the current design is adequate, marginal, or insufficient.  
- Which specific improvements would make the biggest difference.  
- How you would prioritise those improvements given limited time and budget.

### Expected Outcomes

After completing this project you should be able to:

- Critically evaluate your infrastructure design for scalability, resilience, and evolvability.  
- Provide leadership with an honest, structured view of where the network stands.  
- Offer a concrete improvement roadmap that fits within the broader enterprise strategy.

### Reflection

Reflect on:

- How your view of “good enough” infrastructure has changed after considering scale and failure.  
- Which skills (design, automation, troubleshooting, communication) you want to strengthen next.  
- How you will keep your design thinking aligned with evolving technologies and business needs.


