## Advanced Network Assurance Lab 30 – Building a Reusable Network Troubleshooting Runbook

### Scenario
Your team has handled several recent incidents: a slow internal application, intermittent packet loss on a WAN link, and users at a branch unable to reach a SaaS service. Each time, different engineers followed slightly different troubleshooting approaches, and it was hard to compare notes or build on previous work.

Leadership has asked you to **standardise how network investigations are performed and documented**. In this lab you will design a reusable troubleshooting runbook that can be applied to a wide range of network issues, not just a single slow application.

### Project Objectives

By the end of this project you should be able to:

- Define a structured troubleshooting workflow for network incidents.  
- Map specific tools (ping, traceroute, debugs, SNMP, syslog, NetFlow, SPAN/RSPAN, IPSLA) to each step of that workflow.  
- Produce templates for capturing investigation data and conclusions.  
- Explain how controllers and APIs can enhance or automate parts of the process.

### Technologies and Topics in Scope

This project draws from the Network Assurance section:

- **4.1 Problem diagnosis tools** – Ping, traceroute, debugs, SNMP, and syslog in a repeatable sequence.  
- **4.2 Flexible NetFlow** – As a standard way to observe traffic patterns.  
- **4.3 Traffic mirroring** – SPAN, RSPAN, and ERSPAN for deeper packet-level analysis.  
- **4.4 IPSLA** – For synthetic testing and baseline measurements.  
- **4.5 Cisco Catalyst Center** – Example of a controller that can orchestrate and visualise checks.  
- **4.6 NETCONF/RESTCONF** – For programmatic data collection and verification.

### Project Tasks

1. **Design the troubleshooting flow**
   - Define the main phases of an investigation, for example:
     - Problem intake and scoping.  
     - Basic connectivity and path checks.  
     - Device health and interface validation.  
     - Traffic and flow analysis.  
     - Deep-dive packet analysis (when needed).  
   - For each phase, specify the questions to answer and the typical time budget.
2. **Map tools to each phase**
   - For each phase in your flow, list:
     - Which tools are mandatory (for example ping/traceroute for connectivity, SNMP/syslog for health).  
     - Which tools are optional or advanced (for example IPSLA, ERSPAN, NETCONF queries).  
   - Provide example command sets or API calls that would be used in a typical case.
3. **Create investigation templates**
   - Design a simple form or document structure that engineers must complete during an incident, including:
     - Problem statement and scope.  
     - Steps taken and data collected (with timestamps).  
     - Hypotheses considered and accepted/rejected.  
     - Final conclusion and recommended next actions.  
   - Ensure the template is concise enough to be practical but detailed enough to be useful later.
4. **Integrate controller and automation concepts**
   - Identify which steps could be automated or accelerated with a controller like Cisco Catalyst Center.  
   - Describe how NETCONF/RESTCONF or scripts could collect standard data across many devices at once.  
   - Note any prerequisites (inventory accuracy, device access, role-based permissions).
5. **Test the runbook against sample scenarios**
   - Apply your runbook to at least two previous or hypothetical incidents (for example slow app, WAN packet loss, branch outage).  
   - Record how well the flow fits each case and where adjustments are needed.  
   - Refine the runbook based on what you learn.

### Failure and What-If Analysis

Consider and document how your runbook would handle:

- A widespread but brief latency spike that resolves before deep analysis is possible.  
- An issue that only affects a single user or device.  
- A complex problem involving multiple domains (for example wireless, WAN, and security).  
- A case where initial evidence points away from the network but stakeholders insist “it must be the network”.

For each, explain:

- How your flow ensures a thorough but efficient investigation.  
- How you capture enough evidence to support your conclusions.  
- How you communicate findings clearly to non-network teams.

### Expected Outcomes

At the end of this lab you should be able to:

- Present a practical, step-by-step network troubleshooting runbook that your team can adopt.  
- Demonstrate how specific assurance tools plug into that runbook.  
- Improve consistency and quality of future network investigations.

### Reflection

Reflect on:

- Which parts of your runbook are most critical to follow strictly, and which can be flexible.  
- How you will train other engineers to use it effectively.  
- How you will evolve the runbook as new tools and network designs are introduced.


