## Advanced Automation Lab 47 – Building a Simple Self-Service Network Task Portal

### Scenario
Your network team is frequently interrupted by small, repetitive requests from other teams:

- \"Can you add this MAC address to the wired allow-list.\"  
- \"Can you open this port to a test server for two hours.\"  
- \"Can you move this access port into the guest VLAN for a workshop.\"  

Each request is handled manually through tickets and ad-hoc CLI changes. Nothing prevents mistakes, and there is no easy way to expire temporary changes automatically.

Management wants you to explore the idea of a **self-service network task portal** that exposes a few tightly controlled operations to other teams. In this lab you will design the backend automation for such a portal, with a focus on **safety, approvals, and auditability**, not front-end code.

### Project Objectives

By the end of this project you should be able to:

- Identify one or two narrow network tasks that are safe to expose as self-service.  
- Describe how those tasks can be implemented using Python, JSON, and APIs or orchestration tools.  
- Define guardrails: validation, approvals, and automatic expiry of temporary changes.  
- Explain how requests, actions, and results are logged for audit and troubleshooting.

### Technologies and Topics in Scope

This project is rooted in the Automation  (6.x):

- **6.1 Python components and scripts** – to implement the backend logic for self-service tasks.  
- **6.2 JSON encoded data** – to represent requests, parameters, and results.  
- **6.3 YANG and models** – to understand what objects your portal is allowed to touch.  
- **6.4 and 6.5 APIs and REST responses** – to apply changes via controllers or RESTCONF.  
- **6.6 EEM applets** – optionally to enforce local safeguards or time-based actions.  
- **6.7 Orchestration tools** – as an alternative engine behind the portal for more complex tasks.

### Project Tasks

1. **Select candidate self-service tasks**  
   - Choose one or two operations that:
     - Are frequent and well-understood.  
     - Have clear boundaries (for example only a specific VLAN or ACL).  
     - Can be reversed without major impact.  
   - Examples:
     - Assigning a port to a pre-approved guest VLAN.  
     - Creating a temporary ACL entry for a specific source and destination.  
2. **Define the request and approval model**  
   - Design a JSON structure for a self-service request, including:
     - Requester identity and team.  
     - Task type (for example \"guest-port\" or \"temporary-acl\").  
     - Parameters (for example port ID, MAC address, IPs, ports, duration).  
   - Decide which requests require explicit approval and who approves them.
3. **Design the automation backend**  
   - Describe how a Python script or orchestration playbook will:
     - Validate the request against allowed ranges and policies.  
     - Call controller or device APIs to implement the change.  
     - Schedule or trigger expiry actions if the change is temporary.  
   - Include how REST API responses are checked and how errors are surfaced back to the requester.
4. **Plan logging and audit trails**  
   - Specify what must be logged for each request:
     - Who asked for the change and when.  
     - What was changed and on which devices.  
     - When the change was reverted (if temporary).  
   - Decide where logs are stored (for example syslog, SIEM, or a simple database) and how they are searched during investigations.
5. **Outline a user-facing workflow**  
   - Without writing UI code, describe:
     - How a user submits a request (for example web form, chat bot, or ticket integration).  
     - How they see whether their request is pending, approved, or completed.  
     - What feedback they get if validation fails or the action cannot be completed.

### Design Diagram (Text Form)

Describe an architectural view of the self-service portal:

- A \"User\" block representing requesters in other teams.  
- A \"Request API\" block that accepts JSON payloads from a simple UI or integration.  
- An \"Approval\" block where requests are reviewed if needed.  
- An \"Automation Engine\" block running Python or orchestration playbooks.  
- \"Network\" blocks (controllers and devices) where changes are applied.  
- A \"Logging and Audit\" block that records all actions and outcomes.

Show the flow from request to approval, to automation action, to confirmation and expiry.

### Failure and What-If Analysis

Consider:

- A request is malformed or outside allowed policy (for example a port outside the permitted range). How is this rejected and reported.  
- The automation engine partially applies a change before an error occurs. How do you detect and correct this.  
- A temporary change is not reverted on time because of a failure in the expiry mechanism.

For each case, describe:

- The impact on users and on the network.  
- How your design detects the issue and what automated or manual recovery steps exist.  
- What additional safeguards you might add before going into production.

### Expected Outcomes

After completing this project you should be able to:

- Present a realistic design for a small self-service network task portal.  
- Explain how automation, approvals, and logging work together to keep it safe.  
- Identify which tasks in your own environment could be on-boarded first.

### Reflection

Reflect on:

- How comfortable your organisation is with delegating limited control to other teams.  
- What cultural or process changes are needed to support self-service safely.  
- How you would pilot this idea with a small group of users before scaling up.

