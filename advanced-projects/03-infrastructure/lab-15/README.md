## Advanced Infrastructure Lab 15 – Campus EtherChannel and Trunk Troubleshooting Runbook

### Scenario
Intermittent connectivity issues continue to appear in the campus even after you stabilised basic Spanning Tree behaviour in a previous project. Users report that:

- Some VLANs go down when a single uplink in a bundle fails.
- New access switches occasionally cause black holes for specific VLANs.
- EtherChannel bundles flap when interfaces are moved or replaced.

An internal audit shows inconsistent trunk allowed-vlan lists and a mixture of manual and protocol-negotiated EtherChannels. In this lab your goal is to **design a troubleshooting and hardening runbook** specifically for trunks and EtherChannels so that future incidents can be resolved quickly and configuration drift is reduced.

### Project Objectives

By the end of this project you should be able to:

- Identify common misconfigurations in 802.1Q trunks and EtherChannels that lead to outages.  
- Define a standard approach for building, verifying, and documenting campus uplink bundles.  
- Create a troubleshooting flow that junior engineers can follow during EtherChannel or trunk incidents.  
- Explain how these practices relate to the  topics for Layer 2 infrastructure.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, focusing on Layer 2 fault isolation:

- **3.1 Layer 2**
  - 3.1.a Troubleshooting static and dynamic 802.1Q trunking.  
  - 3.1.b Troubleshooting static and dynamic EtherChannels.  
  - 3.1.c Verifying STP behaviour in the presence of trunk and bundle changes.  
- **3.2 Layer 3 (context only)**
  - How Layer 3 reachability is affected when Layer 2 trunks or bundles fail.  

### Project Tasks

1. **Catalogue current uplink designs**
   - List all access-to-distribution and distribution-to-core uplinks.  
   - For each uplink, record:
     - Whether it is a single trunk or part of an EtherChannel.  
     - The negotiation protocol in use (for example static, PAgP, LACP).  
     - The allowed VLAN list and native VLAN.  
   - Note any deviations from your intended design pattern.
2. **Define a standard EtherChannel and trunk template**
   - Choose a default negotiation strategy (for example LACP active/active).  
   - Specify a standard allowed-vlan policy and native VLAN handling.  
   - Decide how port-channel numbering and descriptions will be allocated.  
   - Document the exact CLI or configuration snippets that implement this standard.
3. **Design a troubleshooting flow**
   - Create a step-by-step checklist for diagnosing a broken EtherChannel or trunk, including:
     - Status of physical members and port-channel interfaces.  
     - Verification of negotiation status and bundle consistency.  
     - Checks for mismatched VLAN lists or native VLANs.  
   - Include which show commands to run and what output a healthy link should produce.
4. **Plan validation tests**
   - Describe how you would deliberately:
     - Remove one member from an EtherChannel.  
     - Introduce a VLAN mismatch on one side of a trunk.  
     - Change negotiation settings on one end only.  
   - For each test, state:
     - The expected device behaviour and logs.  
     - The impact on user traffic.  
     - How your runbook would guide someone to the root cause.
5. **Produce an operations-facing runbook**
   - Summarise your standards and troubleshooting flow in a short document structure:
     - Purpose and scope.  
     - When to use this runbook.  
     - Quick checks vs deep-dive diagnostics.  
   - Make sure the language is clear enough for a Tier-1 or Tier-2 engineer.

### Design Diagram (Text Form)

Use this to sketch a logical view that supports your runbook:

- **Core/Distribution**
  - Port-channels connecting core and distribution switches with clearly labelled member interfaces.  
  - Notes indicating standard VLANs carried on these bundles.
- **Access layer**
  - Access switches with dual uplinks in EtherChannels to distribution.  
  - Highlight where trunk-only links still exist and why.
- **Troubleshooting overlays**
  - For at least one bundle, annotate where to check:
    - Physical status (interfaces).  
    - Logical status (port-channel summary).  
    - VLAN presence (show interfaces trunk or equivalent).

### Failure and What-If Analysis

Consider these scenarios and describe how your runbook and standards respond:

- An engineer replaces an access switch uplink module and forgets to reapply the EtherChannel configuration.  
- A trunk between two distribution switches has a different allowed VLAN list on each side.  
- LACP is disabled on one side of a previously healthy bundle.  
- A new VLAN is added to the campus but is not added to all required trunk ports.

For each case, explain:

- Likely user-visible symptoms.  
- Key indicators in logs or show commands.  
- The sequence of checks from your runbook that lead to resolution.  
- Any long-term design adjustments that would prevent recurrence.

### Expected Outcomes

After completing this project you should be able to:

- Demonstrate a clear, repeatable method for diagnosing trunk and EtherChannel problems.  
- Justify your chosen EtherChannel and trunk standards in terms of reliability and simplicity.  
- Provide operations with documentation that shortens the time to repair Layer 2 incidents.

### Reflection

Reflect on:

- Which types of trunk or EtherChannel issues were hardest to detect quickly.  
- How much standardisation is realistic in your environment versus ideal.  
- How you would measure whether your runbook actually reduces incident duration over time.


