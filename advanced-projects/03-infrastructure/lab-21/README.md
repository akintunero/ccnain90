## Advanced Infrastructure Lab 21 – Wireless Design Choices in a Campus Network

### Scenario
Your wired campus design is stabilising, but the wireless environment has evolved without a clear plan:

- Some access points are autonomous, others are lightweight and controller-based.  
- Different SSIDs use different VLAN mappings and security models.  
- Roaming performance is inconsistent, especially between buildings.  

Application teams are complaining that Wi‑Fi performance and reliability lag behind wired connections. In this lab you will focus on **wireless design choices** — AP deployment models, VLAN and SSID design, and roaming behaviour — and how they integrate with the existing Layer 2 and Layer 3 campus infrastructure.

### Project Objectives

By the end of this project you should be able to:

- Choose an appropriate wireless deployment model (centralised, distributed, or mixed) for your campus.  
- Map SSIDs to VLANs and IP subnets in a way that supports security and scalability.  
- Describe how access points discover and join controllers.  
- Explain how client roaming works within and between subnets and how the wired design must support it.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, focusing on wireless within the broader infrastructure:

- **3.3 IP services and wireless context**
  - Wireless deployment models, RF basics, AP modes, roaming, and client troubleshooting (as part of the overall infrastructure story).  
  - Interaction between wireless VLANs, first-hop redundancy, and routing.

### Project Tasks

1. **Assess the current wireless landscape**
   - List existing SSIDs, their purposes (corporate, guest, BYOD, IoT), and which VLANs/subnets they use.  
   - Identify which APs are controller-based versus standalone and where controllers reside.  
   - Note any observed problems such as poor roaming or inconsistent IP addressing.
2. **Select a wireless deployment model**
   - Decide whether the campus should move toward a centralised, distributed, or hybrid controller model.  
   - Describe where controllers will sit in the topology and how APs reach them.  
   - Consider how branch or remote sites will participate in this design.
3. **Design SSID, VLAN, and IP segmentation**
   - Propose a simplified SSID set aligned to business needs.  
   - Map each SSID to appropriate VLANs and IP subnets, taking into account security zones (corporate, guest, IoT).  
   - Decide where DHCP, DNS, and gateway services will live for these subnets.
4. **Plan roaming behaviour and support**
   - Describe how clients will roam within a building and between buildings (Layer 2 vs Layer 3 roaming patterns).  
   - Identify any requirements for mobility groups, mobility controllers, or fast roaming features.  
   - Ensure the wired network (VLANs, routing, and redundancy) supports the chosen roaming model.
5. **Define operational and troubleshooting considerations**
   - List key metrics and logs for wireless health (AP join state, client counts, RF interference, DHCP failures).  
   - Outline a basic troubleshooting flow for a user reporting poor Wi‑Fi performance.  
   - Describe how changes to SSIDs or controllers will be coordinated with wired configuration.

### Design Diagram (Text Form)

Use this to sketch the wireless-related topology:

- **Access layer**
  - APs connected to access switches, indicating which VLANs/SSIDs they serve.  
- **Controller and core**
  - Wireless LAN controllers and their connections to the core/distribution layer.  
  - VLANs and IP subnets used for corporate, guest, and other SSIDs.
- **Roaming paths**
  - Example client movement from one AP to another, showing how IP addressing and gateway selection behave.

### Failure and What-If Analysis

Consider and document behaviour for these scenarios:

- A wireless controller fails or loses connectivity to a group of APs.  
- A misconfiguration maps a corporate SSID to the guest VLAN.  
- DHCP or DNS for wireless subnets becomes unavailable.  
- RF interference or coverage gaps appear in a busy area.

For each scenario, explain:

- The impact on wireless clients and applications.  
- How you would detect the issue using controller views, logs, or client reports.  
- What design or operational practices (for example, redundancy, change control, RF surveys) help reduce risk.

### Expected Outcomes

After completing this project you should be able to:

- Present a coherent wireless design that integrates with your existing campus infrastructure.  
- Justify your SSID, VLAN, and controller placement decisions.  
- Describe how roaming and resiliency requirements are met at both the wired and wireless layers.

### Reflection

Reflect on:

- How your wireless design balances simplicity, security, and user experience.  
- Which areas of RF design or wireless troubleshooting you would prioritise for further study.  
- How you would keep the wireless design documentation current as the environment evolves.


