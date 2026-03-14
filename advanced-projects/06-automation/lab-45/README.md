## Advanced Automation Lab 45 – Designing an Event-Driven Alerting and Remediation Workflow

### Scenario
Your operations team spends a lot of time reacting to repeated issues: interfaces that flap at the same site every week, high CPU on a core switch during backups, or access points that regularly lose connectivity. Today, most of the response is manual. Someone notices a syslog message or an email alert and then logs in to run a few show commands.

In this lab you will design an **event-driven automation workflow** that reacts to well understood triggers. Instead of trying to automate everything, you will:

- Identify a small number of repeatable network events worth automating.  
- Decide which of them can be handled locally with EEM applets.  
- Decide which require centralised workflows using APIs or orchestration tools.  
- Define how alerts, scripts, and human runbooks fit together.

The goal is to reduce time to detection and time to basic triage without losing human oversight.

### Project Objectives

By the end of this project you should be able to:

- Describe how EEM can react to device events such as interface flaps or syslog messages.  
- Explain how Python scripts or controller APIs can be triggered as part of a workflow.  
- Compare when to use local event handlers versus central automation or orchestration.  
- Sketch an end-to-end flow from event to alert, automated action, and human follow-up.

### Technologies and Topics in Scope

This project focuses on the automation  (6.x), especially:

- **6.1 Python components and scripts** – used for simple remediation or data collection.  
- **6.2 JSON encoded data** – for passing structured information between tools.  
- **6.3 YANG and models** – as a way to target specific state or configuration.  
- **6.4 and 6.5 APIs and REST responses** – when calling controllers or RESTCONF endpoints.  
- **6.6 EEM applets** – as local event-driven automation on network devices.  
- **6.7 Orchestration tools** – to coordinate multi-device responses when needed.

### Project Tasks

1. **Select one or two high-value events**  
   - Examples:
     - An access switch uplink that flaps more than three times in ten minutes.  
     - CPU on a core switch exceeding a defined threshold for more than five minutes.  
     - Repeated authentication failures on a management interface.  
   - For each event, describe why it matters and what a human normally does in response.
2. **Decide what can be automated locally**  
   - For each event, ask:
     - Can an EEM applet on the device safely collect extra information (for example show commands) or take a simple action (for example temporarily shut a non-critical interface).  
     - What data should be logged or sent to a central system when the event fires.  
   - Write a short description of at least one EEM-based response.
3. **Design a central workflow**  
   - For events that require a broader view (for example cross-device correlation), describe:
     - Which system receives the initial alert (for example SIEM, NMS, controller).  
     - How a Python script or orchestration tool might query APIs to gather more context.  
     - What automated steps are safe to take, and where a human must approve changes.
4. **Define data formats and interfaces**  
   - Decide how information flows between components:
     - What JSON payloads or fields are passed from EEM to a webhook or from a controller API to your script.  
     - How REST API response codes influence the next step in the workflow.  
   - Document the minimum fields needed for an engineer to understand what happened.
5. **Document the full runbook**  
   - For your main example event, write a step-by-step runbook that includes:
     - The original trigger and how it is detected.  
     - Any local EEM actions and what they record.  
     - Any central automation steps and the data they gather.  
     - The point where a human engineer reviews the situation and decides on final remediation.

### Design Diagram (Text Form)

Describe a logical diagram for your event-driven workflow:

- A "Device" block where the event occurs and where EEM may run.  
- An "Event Bus or Alerting" block that receives syslog or SNMP traps.  
- An "Automation" block that runs Python scripts or orchestration playbooks using APIs.  
- An "Engineer" block that receives summarised alerts and decides on final action.

Show arrows that indicate the sequence from event to EEM, to central automation, to human review.

### Failure and What-If Analysis

Consider and document:

- What happens if an EEM applet misfires or takes an action on the wrong interface. How would you limit the scope of automated actions.  
- What if the central automation platform is unavailable when an event occurs. How should devices behave in that case.  
- How you avoid "alert storms" by consolidating events or applying rate limits.

For each scenario, describe the risk, detection method, and design choices that reduce impact.

### Expected Outcomes

After completing this project you should be able to:

- Explain an event-driven automation design that balances speed and safety.  
- Show how EEM, APIs, and orchestration tools can work together rather than in isolation.  
- Provide a clear runbook that operations teams can use to adopt this workflow.

### Reflection

Reflect on:

- Which current alerts in your environment would most benefit from basic automation.  
- Where you are comfortable allowing automated actions and where you insist on human approval.  
- How you would introduce this workflow in stages to build trust with the operations team.

