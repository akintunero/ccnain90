## Advanced Architecture Lab 6 – Dual Stack Campus and Branch Design

### Scenario
You are the lead network engineer for a fast growing company that has:

- A main campus with two buildings.
- A small branch office in another city.
- Plans to adopt SD-WAN and possibly SD-Access in the next 18 months.

The current network is a single Layer 2 domain with a basic router for internet access. There is no high availability on the core, no clear separation between user and server traffic, and wireless has grown organically with consumer grade access points. Leadership is asking for a new design that:

- Supports both IPv4 and IPv6.
- Improves availability for core services.
- Prepares the environment for QoS, SD-WAN, and eventual campus fabric.

Your task is to propose a realistic campus and WAN **architecture** that could be implemented over several phases.

This lab emphasises end-to-end QoS interpretation, from access through core to WAN edge, for voice and business-critical applications.


### Project Objectives

By the end of this project you should be able to:

- Describe a tier 2 or tier 3 campus design for the main site.
- Show how the branch connects today and how it could connect in a future SD-WAN model.
- Explain how high availability and FHRP will be used for critical VLAN gateways.
- Outline how wired and wireless QoS will be applied for voice and critical applications.
- Identify where SD-Access or similar fabric could fit into the long term plan.

### Technologies and Design Topics in Scope

This project draws from the Architecture section:

- **1.1 Enterprise design principles**
  - 1.1.a High-level enterprise designs: 2-tier, 3-tier, fabric, and cloud-connected campuses.
  - 1.1.b High availability techniques: redundancy, FHRP, and SSO in campus and WAN designs.
- **1.2 Cisco Catalyst SD-WAN working principles**
  - 1.2.a SD-WAN control and data plane elements and how they change WAN design.
  - 1.2.b Benefits and limitations of the Catalyst SD-WAN solution for different site types.
- **1.3 Cisco SD-Access working principles**
  - 1.3.a SD-Access control and data plane elements and fabric roles.
  - 1.3.b How a traditional campus interoperates with SD-Access during migration.
- **1.4 QoS interpretation**
  - Interpreting QoS configurations and policies as they apply across campus, WAN edge, and fabric.

### Project Tasks

Use these tasks to guide your work. You can complete them on paper, in a diagramming tool, or by building a partial version in a lab platform.

1. **Capture requirements and constraints**
   - List business critical applications and where they are hosted.  
   - Identify uptime expectations for internet access and internal services.  
   - Note any constraints such as existing hardware that must be reused.
2. **Draft the campus logical design**
   - Choose a tiered model (for example two core switches with multiple access switches).  
   - Decide which VLANs are needed (user, voice, server, guest, management, wireless).  
   - Show routing boundaries between core and distribution or access.
3. **Design high availability**
   - Decide where dual core or dual distribution devices are required.  
   - Select an FHRP for gateway redundancy and decide which device should be active for which VLANs.  
   - Plan link redundancy between layers, including EtherChannel if appropriate.
4. **Plan WAN and SD-WAN readiness**
   - Show how the branch connects to HQ and to the internet today.  
   - Identify where SD-WAN edge devices would sit in the future.  
   - Explain how control and data plane roles would shift when SD-WAN is introduced.
5. **Add wireless and QoS considerations**
   - Choose a wireless deployment model for the campus and the branch.  
   - Identify the main QoS classes (voice, video, mission critical, best effort).  
   - Decide where QoS markings and queuing will be enforced (access, core, WAN edge).
6. **Document assumptions and open questions**
   - Write down any design decisions that depend on information you do not yet have.  
   - Prepare questions you would ask stakeholders to validate your plan.

### Failure and What-If Analysis

For each of the following events, describe in writing:

- What fails.
- What continues to work.
- How users will experience the failure.
- How the design you proposed helps or hurts the outcome.

Events to analyse:

- Loss of a single core or distribution switch.  
- Loss of one uplink from an access switch to the core.  
- Failure of the primary internet or WAN circuit.  
- Controller failure in a centralised wireless design.

You do not need to configure anything to answer these questions, but you should be able to trace traffic flows and FHRP behaviour in your design.

### Expected Outcomes

When you finish this project you should be able to:

- Sketch and explain a dual stack campus and branch architecture that fits the scenario.  
- Justify your use of tiers, redundancy, VLAN boundaries, and FHRP.  
- Show how QoS and wireless design fit into the overall picture.  
- Describe how the current design can evolve into SD-WAN or SD-Access without a complete rebuild.

### Reflection

After completing your design, reflect on:

- Which trade-offs you made between simplicity, cost, and high availability.  
- Which parts of the design would be hardest to change later if requirements grow.  
- How you would explain this design to a non-technical stakeholder who only cares about reliability and user experience.

