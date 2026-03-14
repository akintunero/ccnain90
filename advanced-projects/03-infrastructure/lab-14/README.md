## Advanced Infrastructure Lab 14 – Layer 2 Stability and Trunking Audit

### Scenario
Your company has reported several short but disruptive outages in the main campus. Users on some VLANs briefly lose connectivity when uplinks are changed or when new access switches are added. A quick review shows:

- A mix of static and dynamic 802.1Q trunks.
- EtherChannels built with different hashing and negotiation settings.
- Spanning Tree roots that were elected by accident rather than design.

Routing, IP services, and wireless will be addressed in later labs. In this first Infrastructure project your goal is to **stabilise the Layer 2 foundation**: make trunks, EtherChannels, and STP predictable so that future changes are low risk.

### Project Objectives

By the end of this project you should be able to:

- Describe a deliberate Layer 2 topology for the campus access and distribution layers.  
- Standardise 802.1Q trunk and EtherChannel configuration across uplinks.  
- Select and justify an STP mode and root placement strategy.  
- Explain how your Layer 2 decisions set up later routing and services work.

### Technologies and Design Topics in Scope

This project draws primarily from the Infrastructure section, with emphasis on Layer 2:

- **3.1 Layer 2**
  - 3.1.a Troubleshooting static and dynamic 802.1Q trunking.
  - 3.1.b Troubleshooting static and dynamic EtherChannels.
  - 3.1.c Configuring and verifying common STP modes (RSTP, MST) and enhancements such as root guard and BPDU guard.
- **3.2 Layer 3 (context only)**
  - How downstream Layer 3 designs will depend on a stable Layer 2 core.
- **3.3 IP services (context only)**
  - Where first-hop redundancy and multicast will later rely on predictable VLAN and trunk design.

### Project Tasks

1. **Capture the current Layer 2 state**
   - List all access and distribution switches that participate in the campus.  
   - For each uplink, record whether it is a simple trunk or part of an EtherChannel.  
   - Identify which VLANs are intended to be present on each uplink.
2. **Analyse Spanning Tree behaviour**
   - Determine the current STP mode in use (for example PVST, RSTP, or MST).  
   - Use show commands to find the root bridge per VLAN or instance.  
   - Note any access-layer switches that have accidentally become root.
3. **Design the target Layer 2 topology**
   - Choose an STP mode that fits the campus size and vendor support.  
   - Select primary and secondary STP roots for user, server, and management VLANs.  
   - Define which links should be in EtherChannel bundles and which remain single trunks.
4. **Standardise trunk and EtherChannel policies**
   - Propose a standard trunk template (allowed VLANs, native VLAN, negotiation settings).  
   - Define a standard EtherChannel configuration for access-to-distribution links.  
   - Document how mis-matched channel settings will be detected and avoided.
5. **Plan a migration approach**
   - Describe the order in which you would change STP priorities and trunk settings.  
   - Identify any maintenance windows or risk-reduction techniques (for example, changing one link at a time).  
   - Prepare a short checklist to validate the campus after each step.

### Design Diagram (Text Form)

Use this description to build a logical Layer 2 diagram:

- **Distribution layer**
  - One or two core/distribution switches that will act as STP roots.  
  - Uplinks to each access switch, grouped into EtherChannels where appropriate.
- **Access layer**
  - Access switches with ports assigned to user, server, and management VLANs.  
  - Redundant uplinks back to the distribution layer, following the standard trunk template.
- **Spanning Tree view**
  - Highlight which switch is root for each VLAN or instance.  
  - Show which links are forwarding and which are blocking under normal operation.

### Failure and What-If Analysis

Consider and document the impact of the following events on your proposed design:

- A distribution switch that is the STP root fails unexpectedly.  
- One physical member of an uplink EtherChannel goes down.  
- A new access switch is accidentally connected with a default STP priority and all VLANs allowed on its uplink.  
- A trunk is misconfigured to drop a critical user VLAN.

For each event, describe:

- The expected Layer 2 convergence behaviour.  
- How user connectivity is affected and for how long.  
- Which design choices (for example, root guard, consistent trunk templates) help contain or prevent the issue.

### Expected Outcomes

After completing this project you should be able to:

- Explain and sketch a stable Layer 2 design for your campus access and distribution layers.  
- Justify your STP mode and root placement to another engineer.  
- Show how standardised trunk and EtherChannel policies reduce outage risk during change.  
- Identify remaining Layer 2 risks that should be addressed in later Infrastructure labs.

### Reflection

Reflect on:

- Which parts of the existing Layer 2 design were most fragile and why.  
- How your proposed changes improve operational predictability for future routing and services work.  
- What monitoring or alerting you would put in place to quickly detect Layer 2 issues after deployment.


