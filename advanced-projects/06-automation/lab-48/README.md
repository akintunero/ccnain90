## Advanced Automation Lab 48 – Automation Capstone: From Scripts to an Operations Runbook

### Scenario
Over the last automation labs you have designed specific use cases: configuration compliance checking, event-driven responses, API-assisted change windows, and even a self-service portal. Each design focuses on a single problem. Your operations leadership now wants to understand **how it all fits together** in day-to-day network operations.

You have been asked to produce an **automation-focused operations runbook** for the network team. This runbook should:

- Summarise the automation patterns you have designed so far.  
- Define when each pattern is appropriate and what its prerequisites are.  
- Show how incidents, changes, and routine checks can make use of automation safely.  
- Highlight where future investment in tooling or skills will have the most impact.

This is the capstone for the automation track: you move from individual tools to an integrated way of working.

### Project Objectives

By the end of this project you should be able to:

- Describe a small portfolio of automation use cases suitable for an enterprise network team.  
- Map each use case to the underlying technologies: Python, JSON, YANG, APIs, EEM, and orchestration tools.  
- Define clear entry points for automation in incident response, change management, and routine maintenance.  
- Propose a staged adoption plan that builds confidence and avoids over-automation.

### Technologies and Topics in Scope

This project draws on the full Automation  (6.x):

- **6.1 Python components and scripts** – as the glue for many workflows.  
- **6.2 JSON encoded data** – to describe intent, inventory, and requests.  
- **6.3 Data modelling with YANG** – to reason about configuration in a structured way.  
- **6.4 and 6.5 APIs and REST responses** – for controllers and device-level access.  
- **6.6 EEM applets** – for local event handling and data collection.  
- **6.7 Orchestration tools** – for larger, multi-device changes and integrations.

### Project Tasks

1. **Catalogue your automation use cases**  
   - List the concrete designs from earlier labs, for example:
     - Configuration compliance checker.  
     - Event-driven alerting and remediation.  
     - API-driven change windows.  
     - Self-service task portal.  
   - For each, summarise:
     - The problem it solves.  
     - The main technologies it uses.  
     - The current level of maturity (idea, prototype, or production-ready).
2. **Define when to use which pattern**  
   - Create guidance such as:
     - Use the compliance checker for regular drift reports and pre-change assessments.  
     - Use event-driven workflows for high-frequency, well-understood incidents.  
     - Use API-driven change windows for planned, repeatable changes across many devices.  
     - Use the self-service portal for low-risk tasks that benefit from delegation.  
   - Note risks and prerequisites for each pattern (for example API access, test environment, skills).
3. **Design the automation operations runbook**  
   - Outline sections of the runbook, such as:
     - \"Daily and weekly automated checks\".  
     - \"Using automation during incident response\".  
     - \"Planning changes with automation support\".  
     - \"Requesting and reviewing new automation use cases\".  
   - Describe what an on-call engineer should do with the outputs of each automated tool.
4. **Plan metrics and feedback loops**  
   - Decide how you will measure the impact of automation, for example:
     - Reduction in time to resolve certain incident types.  
     - Fewer configuration drift findings over time.  
     - Decrease in manual ticket work for repetitive tasks.  
   - Describe how engineers can propose improvements or report issues with automated workflows.
5. **Outline a staged adoption roadmap**  
   - Propose phases, such as:
     - Phase 1: Read-only and reporting tools (compliance checks, data collection).  
     - Phase 2: Limited, supervised write operations during change windows.  
     - Phase 3: Event-driven actions with clear safeguards.  
     - Phase 4: Carefully scoped self-service for selected teams.  
   - For each phase, note training, documentation, and communication activities required.

### Design Diagram (Text Form)

Describe a high-level diagram of your automation ecosystem:

- A \"Source of Events and Requests\" block (tickets, alerts, periodic schedules, self-service).  
- An \"Automation Services\" block that groups your scripts, EEM applets, and orchestration tools.  
- \"Controllers and Devices\" blocks where actual configuration and state live.  
- A \"Runbook and Metrics\" block that guides engineers and tracks outcomes.

Show how incidents, changes, and routine checks flow through this ecosystem.

### Failure and What-If Analysis

Consider:

- An automated tool produces incorrect or misleading results. How do you catch this and roll back trust in that tool until it is fixed.  
- A new team member overestimates what is automated and assumes tasks are covered when they are not. How does the runbook set expectations.  
- A critical dependency (for example a controller API or credentials store) is unavailable.

For each case, describe:

- The potential impact on operations.  
- How documentation, training, and design choices reduce the risk.  
- What immediate mitigation steps you would include in the runbook.

### Expected Outcomes

After completing this project you should be able to:

- Present an automation-focused operations runbook tailored to your environment.  
- Explain how individual automation projects support broader operational goals.  
- Guide your team through a realistic, low-risk journey from manual CLI to thoughtful automation.

### Reflection

Reflect on:

- Which parts of your current operations will benefit most from this integrated approach.  
- Where you still have gaps in skills, tooling, or trust that need to be addressed.  
- What your \"next three concrete steps\" are to move from design to implementation.

