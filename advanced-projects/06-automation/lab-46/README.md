## Advanced Automation Lab 46 – Using Controller and Device APIs for Change Windows

### Scenario
Your organisation has strict change windows for network modifications. Today, engineers build per-device CLI change plans and copy and paste commands during an evening or weekend window. This works, but it is slow and error-prone. A missed command on one switch or router can cause inconsistent behaviour that is only noticed days later.

Management is open to using **controller and device APIs** to make change windows safer and more predictable, but they want a clear design before investing in tooling. In this lab you will design an approach where:

- Planned changes are described in structured data (for example JSON).  
- A script or tool uses controller or device APIs to preview, apply, and verify changes.  
- The process fits into existing change management and rollback procedures.

You are not writing a full framework; you are designing how APIs will be used in a controlled, auditable way during scheduled changes.

### Project Objectives

By the end of this project you should be able to:

- Describe when to use a controller API versus direct device APIs (RESTCONF/NETCONF) during change windows.  
- Design a JSON-based representation of intended changes that a script can interpret.  
- Explain how to use API calls to perform pre-checks, apply changes, and run post-checks.  
- Interpret REST API responses in the context of success, partial success, or failure.  
- Show how this workflow integrates with existing approval, logging, and rollback processes.

### Technologies and Topics in Scope

This project emphasises the Automation section (6.x):

- **6.1 Python components and scripts** – for orchestrating pre-checks, changes, and post-checks.  
- **6.2 JSON encoded data** – for describing change intent in a machine-readable way.  
- **6.3 Data modelling with YANG** – for understanding how modelled configuration items are targeted.  
- **6.4 APIs for Cisco Catalyst Center and SD-WAN Manager** – as central control points for many devices.  
- **6.5 REST API responses** – including handling error codes and parsing payloads.  
- **6.6 EEM applets and 6.7 orchestration tools** – as complementary mechanisms where appropriate.

### Project Tasks

1. **Choose a repeatable change scenario**  
   - Examples:
     - Updating NTP and syslog settings across a set of access switches.  
     - Adding a new VLAN and associated SVI on distribution switches.  
     - Adjusting QoS policy on WAN edge devices for a new application.  
   - Write a short description of the change, including which devices and which configuration elements are affected.
2. **Define the intent data model**  
   - Design a JSON structure that represents:
     - Target devices or device groups.  
     - The specific configuration changes to make (at a high level).  
     - Any parameters, such as VLAN IDs, IP addresses, or policy names.  
   - Ensure the model can be versioned and stored alongside change tickets.
3. **Plan API-based pre-checks and post-checks**  
   - For each configuration element you plan to change, describe:
     - Which API calls or show-equivalent data you will collect before the change.  
     - Which data you will collect after the change to confirm success.  
   - Include how you will detect partial success (for example some devices updated, others failed).
4. **Outline the change execution script**  
   - Sketch the main steps of a Python script or similar tool:
     - Read the JSON intent and validate it.  
     - Fetch current state via controller or device APIs.  
     - Apply changes in a controlled order (for example core, then distribution, then access).  
     - Run post-checks and summarise results.  
   - Explain how the script logs actions and results for audit purposes.
5. **Integrate with change management and rollback**  
   - Describe how your approach:
     - Fits into existing approval workflows (for example attaching the JSON and script plan to a ticket).  
     - Supports rollback strategies (for example capturing pre-change config snippets or intent).  
     - Provides clear reporting for the change review meeting.

### Design Diagram (Text Form)

Describe a conceptual diagram of this API-driven change window:

- A "Change Intent" block that stores JSON definitions tied to tickets.  
- A "Change Orchestrator" block (your script or tool) that reads intent and talks to APIs.  
- "Controller" and "Devices" blocks that expose RESTCONF/NETCONF or controller APIs.  
- A "Change Management" block that represents approvals, logs, and reports.

Show the sequence from approved intent to orchestrated API calls, to verification, to reporting.

### Failure and What-If Analysis

Consider and document:

- What happens if an API call fails halfway through a multi-device change. How do you detect which devices were updated and which were not.  
- How you respond if the post-checks show degraded performance or incorrect configuration.  
- What you do if the controller itself is unavailable during the change window.

For each case, describe:

- The immediate action you would take.  
- How your design (for example logging, pre-checks, and rollback plans) helps limit impact.  
- What you would improve in the next iteration of the API-driven change process.

### Expected Outcomes

After completing this project you should be able to:

- Present a realistic plan for using controller and device APIs during scheduled change windows.  
- Walk through the flow of intent, API calls, and verification for a specific change scenario.  
- Explain how this approach reduces manual errors and improves auditability.

### Reflection

Reflect on:

- Which existing change types in your environment would benefit most from this structured, API-driven approach.  
- What skills your team would need to gain confidence in running changes this way.  
- How you could pilot this method on a low-risk change before expanding to critical services.

