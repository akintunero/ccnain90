## Advanced Infrastructure Lab 27 – End-to-End Infrastructure Review and Design Narrative

### Scenario
You have now worked through multiple focused infrastructure projects: Layer 2 stability, OSPF design, eBGP edge, wireless integration, NTP, NAT/PAT, first-hop redundancy, and multicast. Leadership is preparing for a strategy review and wants a **single, coherent narrative** that explains how all of these pieces fit together into one enterprise network design.

In this capstone infrastructure lab, you will consolidate your previous decisions into an end-to-end story that a senior technical audience can follow. The goal is not to repeat every detail, but to show how Layer 2, Layer 3, and IP services combine to support the organisation’s applications and growth plans.

### Project Objectives

By the end of this project you should be able to:

- Summarise your campus, datacentre, and edge infrastructure design in clear, structured language.  
- Explain how routing, switching, and IP services support availability, performance, and security requirements.  
- Highlight key trade-offs you made (simplicity vs flexibility, cost vs resilience).  
- Identify areas where further work or future projects are recommended.

### Technologies and Design Topics in Scope

This project touches on all parts of the Infrastructure  (3.x):

- **3.1 Layer 2** – Overall VLAN, trunking, EtherChannel, and STP approach.  
- **3.2 Layer 3** – OSPF/EIGRP decisions, area structure, eBGP edge, and any PBR considerations.  
- **3.3 IP services** – NTP, NAT/PAT, first-hop redundancy, and multicast design decisions.

### Project Tasks

1. **Create a high-level design summary**
   - Write a short overview (1–2 pages) describing:
     - The role of the campus, datacentre, DR site, and WAN edge.  
     - The main technologies used at each layer (L2, L3, and IP services).  
     - How the design supports the organisation’s core applications.
2. **Describe key design domains**
   - For each of the following, summarise your chosen approach and rationale:
     - Layer 2 topology and redundancy.  
     - Internal routing (OSPF/EIGRP) and external connectivity (eBGP).  
     - Wireless topology and integration with wired infrastructure.  
     - NTP and time synchronisation.  
     - NAT/PAT and internet/partner connectivity.  
     - First-hop redundancy.  
     - Multicast (if applicable).
3. **Map design to requirements**
   - Revisit original business and technical requirements (availability targets, performance expectations, security posture).  
   - Show explicitly how your design addresses each requirement or where compromises were made.  
   - Identify any requirements that remain partially or fully unmet and why.
4. **Outline operations and assurance considerations**
   - Summarise how the network will be monitored and supported (telemetry, logs, controller views, periodic audits).  
   - Describe how configuration consistency will be maintained (templates, change control, automation plans).  
   - Note how troubleshooting workflows will leverage the design (for example clear demarcation points, summarisation boundaries).
5. **Propose a roadmap for future improvements**
   - List potential future projects that build on this infrastructure (for example SD-WAN, SD-Access, deeper automation).  
   - Prioritise them based on risk reduction or business value.  
   - Indicate dependencies between projects (for example multicast readiness before certain applications can launch).

### Design Diagram (Text Form)

Use this to outline a single consolidated diagram:

- **Core view**
  - Campus core/distribution, datacentre core, DR connections, and WAN edge, with major routing domains labelled.  
- **Service overlays**
  - Indicate VLAN/SSID groupings, NTP hierarchy, NAT/PAT points, FHRP gateways, and multicast regions.  
- **External connections**
  - Internet and partner links, with key security or policy enforcement points highlighted.

### Failure and What-If Analysis

Consider the following broader scenarios and explain how your overall design responds:

- Loss of a major distribution or core device.  
- Loss of a WAN edge or ISP connection.  
- Significant configuration error in one design domain (for example NTP, NAT, or FHRP).  
- Rapid business growth that doubles user or application load.

For each, discuss:

- The expected impact on users and services.  
- Which design features limit or localise the impact.  
- What operational actions would be taken in response.

### Expected Outcomes

After completing this project you should be able to:

- Present your infrastructure design to senior engineers or architects in a structured way.  
- Demonstrate how individual technology decisions combine into a coherent whole.  
- Provide a baseline document that future projects and reviews can build upon.

### Reflection

Reflect on:

- Which parts of the design you are most confident in, and which feel more fragile or complex.  
- How your thinking about enterprise infrastructure has changed over the course of these labs.  
- What additional hands-on or design work you would pursue to deepen your expertise.


