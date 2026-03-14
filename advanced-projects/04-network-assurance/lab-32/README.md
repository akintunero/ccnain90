## Advanced Network Assurance Lab 32 – Automating Assurance with Controllers and APIs

### Scenario
Your network operations team spends a lot of time manually collecting data during incidents:

- Logging into multiple devices one by one to run show commands.  
- Exporting ad-hoc NetFlow or IPSLA data for analysis.  
- Manually building path diagrams to explain where traffic flows.  

As the network grows, this approach does not scale. Leadership is evaluating tools such as **Cisco Catalyst Center** and wants to understand how controller workflows and model-driven APIs (NETCONF/RESTCONF) can reduce manual effort and improve consistency. In this lab you will design how automation and controllers fit into your assurance strategy.

### Project Objectives

By the end of this project you should be able to:

- Identify assurance tasks that are good candidates for automation or controller workflows.  
- Describe how Cisco Catalyst Center-style tools can collect, visualise, and correlate network data.  
- Explain where NETCONF/RESTCONF APIs can be used to standardise data collection or checks.  
- Propose an initial automation roadmap focused on assurance, not full configuration management.

### Technologies and Topics in Scope

This project draws from the Network Assurance section:

- **4.5 Cisco Catalyst Center workflows** – Applying configuration, monitoring, and management using traditional and AI-powered workflows.  
- **4.6 Model-driven interfaces** – Configuring and verifying NETCONF and RESTCONF for programmatic monitoring and configuration.  
- **4.1–4.4** – How classic tools and telemetry feed into automated workflows.

### Project Tasks

1. **Catalogue assurance tasks**
   - List common tasks performed during monitoring and troubleshooting, for example:
     - Checking interface health across many devices.  
     - Validating that specific configuration snippets (for example NTP, NetFlow, IPSLA) are present.  
     - Tracing the path between two endpoints.  
   - For each task, rate how repetitive it is and how error-prone it is when done manually.
2. **Design controller-based workflows**
   - Describe how a tool like Cisco Catalyst Center could:
     - Provide topology and path visualisation.  
     - Surface health scores and anomalies.  
     - Run template-based checks for configuration and compliance.  
   - Identify which of your catalogue tasks would become one-click or dashboard-driven operations.
3. **Plan API-driven checks with NETCONF/RESTCONF**
   - Choose a few high-value checks (for example verifying NTP status, interface errors, or specific QoS policies).  
   - Conceptually design how a script using NETCONF/RESTCONF would:
     - Query multiple devices for the relevant data.  
     - Normalise and report the results.  
   - Consider how these scripts would be triggered (on-demand vs scheduled).
4. **Define data storage and correlation**
   - Decide where telemetry and API-collected data will be stored (for example NMS, time-series database, SIEM).  
   - Describe how correlation will happen across:
     - Device metrics.  
     - Flow data.  
     - Synthetic tests.  
     - Controller alerts.  
   - Note any data retention or privacy considerations.
5. **Outline an automation adoption plan**
   - Propose a phased approach:
     - Phase 1: read-only automation and dashboards.  
     - Phase 2: guided workflows that suggest actions.  
     - Phase 3: limited closed-loop remediation for clearly defined scenarios.  
   - Identify skills and process changes your team will need for each phase.

### Failure and What-If Analysis

Consider how your automation plan would cope with:

- Controller or API server outages (what assurance still works without them).  
- Incorrect or stale device inventory in the controller.  
- Misconfigured automation that collects the wrong data or runs at the wrong time.  
- Security or access concerns around centralised automation tools.

For each, explain:

- The impact on visibility and troubleshooting.  
- Safeguards you would put in place (for example change control, RBAC, logging, and approvals).  
- How you would fall back to manual methods if needed.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear vision for how controllers and APIs enhance network assurance.  
- Identify specific, realistic automation use cases that provide quick wins.  
- Help your team plan next steps toward more automated, data-driven operations.

### Reflection

Reflect on:

- Which assurance tasks you personally would automate first and why.  
- How you would balance automation with the need for human judgement.  
- What learning or experimentation you need to become comfortable with controller and API-driven workflows.


