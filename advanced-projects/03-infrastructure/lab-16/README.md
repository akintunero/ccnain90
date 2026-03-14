## Advanced Infrastructure Lab 16 – Spanning Tree Design and Failure Planning

### Scenario
Although trunks and EtherChannels are becoming more consistent, the campus still experiences occasional broadcast storms and unexpected topology changes when links are added or fail. A recent incident report shows:

- One access switch briefly became the root bridge for several VLANs after a reload.  
- A mis-cabled link between two access switches created a Layer 2 loop.  
- During maintenance, moving a single uplink caused multiple VLANs to reconverge slowly.

Your task in this lab is to **design and document a deliberate Spanning Tree strategy** for the campus so that root placement, convergence behaviour, and protection features are all clearly defined and understood.

### Project Objectives

By the end of this project you should be able to:

- Choose an STP mode (for example RSTP or MST) appropriate for the size and design of the campus.  
- Define root, secondary root, and edge roles for switches across key VLANs or MST instances.  
- Specify where to use STP enhancements such as root guard, BPDU guard, and portfast.  
- Explain how your STP design behaves during common failure and misconfiguration scenarios.

### Technologies and Design Topics in Scope

This project draws from the Infrastructure section, with strong focus on 3.1 Layer 2:

- **3.1 Layer 2**
  - 3.1.c Configuring and verifying common STP modes (RSTP, MST) and enhancements such as root guard and BPDU guard.  
- **Related context**
  - Interaction between STP, EtherChannels, and VLAN design.  
  - Impact of Layer 2 convergence on upstream routing and IP services.

### Project Tasks

1. **Assess current STP behaviour**
   - Identify which STP mode is in use on your campus today.  
   - For each major VLAN or instance, record the current root bridge and path cost to that root from several access switches.  
   - Note any switches that unexpectedly appear as root or which have many blocked ports.
2. **Select an STP mode and instance plan**
   - Decide whether you will standardise on per-VLAN STP, RSTP, or MST for the campus.  
   - If using MST, define at least two instances (for example user VLANs and server/management VLANs) and map VLANs accordingly.  
   - Document the reasons for your choice, including convergence time and scalability.
3. **Define root and secondary root placement**
   - Choose which distribution or core switches will be primary and secondary roots for each VLAN or MST instance.  
   - Decide how priorities will be set so that root roles are deterministic even after reboots or hardware changes.  
   - Show how root placement aligns with traffic patterns (for example keeping user traffic local when possible).
4. **Plan STP protection features**
   - Identify edge ports that should use portfast and BPDU guard to protect against accidental loops.  
   - Decide where root guard should be applied to prevent access switches from becoming root.  
   - Consider loop guard or similar mechanisms on redundant links where unidirectional failures are a risk.
5. **Document an implementation and validation plan**
   - Outline the sequence for changing priorities and enabling features to avoid large topology churn.  
   - Define the key verification checks before and after each change (for example root IDs, port roles, and blocked ports).  
   - Include rollback considerations if unexpected behaviour occurs.

### Design Diagram (Text Form)

Use this description to produce an STP-focused diagram:

- **Core/Distribution**
  - Mark which switches are primary and secondary roots for each VLAN or MST instance.  
  - Show redundant links to access switches and indicate expected forwarding vs blocking roles.
- **Access layer**
  - Highlight edge ports (to users, printers, APs) that will have portfast and BPDU guard.  
  - Indicate any cross-links between access switches and how STP will treat them.
- **Convergence paths**
  - For at least one VLAN, trace the path traffic takes from an access switch to the root, and how that path changes if a key link fails.

### Failure and What-If Analysis

Consider and describe the behaviour of your design under these conditions:

- The primary root distribution switch for user VLANs fails.  
- A new access switch is added with default STP priority and connected to the distribution layer.  
- A rogue or misconfigured device sends superior BPDUs on an edge port.  
- A redundant link between two switches becomes unidirectional (one direction fails).

For each scenario, explain:

- How STP reacts and how long convergence is expected to take.  
- Which ports move between forwarding and blocking states.  
- How user traffic is affected and which monitoring signals would reveal the issue.  
- Which STP enhancements specifically mitigate the risk.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear STP design for the campus, including mode, instances, and root placement.  
- Justify the use of protection features such as root guard and BPDU guard in specific locations.  
- Predict how the Layer 2 topology will change during common failures and maintenance events.

### Reflection

Reflect on:

- Which STP design choices offer the best balance between simplicity and fast convergence.  
- How your STP plan interacts with EtherChannel, VLAN extension, and redundancy requirements.  
- What training or documentation operations staff would need to safely maintain the STP design over time.


