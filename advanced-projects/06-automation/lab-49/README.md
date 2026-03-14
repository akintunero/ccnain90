## Advanced Automation Lab 49 – Selecting and Introducing a Network Orchestration Platform

### Scenario
Your organisation has experimented with individual scripts and small automation tools. These have helped in specific areas, but they are hard to share, maintain, and govern. Different engineers keep their own copies, and it is not always clear which script is current or tested.

Senior leadership is considering adopting a **network orchestration platform** (for example Ansible, or another agentless or agent-based tool) as a standard way to automate changes and checks. Before committing, they want a structured comparison and an initial onboarding plan tailored to your environment.

In this lab you will not write playbooks; instead, you will **evaluate orchestration options** and design how one of them would be introduced safely alongside existing processes.

### Project Objectives

By the end of this project you should be able to:

- Compare agent-based and agentless orchestration approaches for network automation.  
- Define selection criteria that matter for your organisation (skills, security, scale, integrations).  
- Propose a reference architecture for an orchestration platform in your network.  
- Design a small pilot project and onboarding plan that reduces risk and builds confidence.

### Technologies and Topics in Scope

This project emphasises part of the Automation  (6.7) while tying in earlier topics:

- **6.7 Orchestration tools** – comparing and positioning tools such as Ansible, Chef, Puppet, and SaltStack.  
- **6.1 Python components and scripts** – as building blocks that may be reused within orchestration workflows.  
- **6.2 JSON encoded data and 6.3 YANG models** – for describing inventory, intent, and configuration.  
- **6.4 and 6.5 APIs and REST responses** – as key interfaces that orchestration tools will call.  
- **6.6 EEM applets** – as complementary local automation that remains device-centric.

### Project Tasks

1. **Define selection criteria for orchestration tools**  
   - List factors that matter in your environment, such as:
     - Support for network devices and vendors you use.  
     - Learning curve for your current team.  
     - Security model (keys, credentials, role-based access).  
     - Integration with existing CI/CD, ticketing, or inventory systems.  
   - Prioritise these criteria and note any non-negotiable requirements.
2. **Compare at least two orchestration options**  
   - Choose two or three candidate tools (for example Ansible and one agent-based alternative).  
   - For each, describe:
     - How it connects to network devices (SSH, API, agents).  
     - How state and inventory are managed.  
     - Strengths and weaknesses for your use cases (compliance, change windows, self-service).
3. **Design a reference architecture**  
   - Sketch how a chosen orchestration tool would fit into your network:
     - Where the control node(s) or servers live.  
     - How they reach devices, controllers, and inventory sources.  
     - How authentication and authorisation are handled.  
   - Include logging, backup, and disaster recovery considerations for the orchestration platform itself.
4. **Plan a pilot project**  
   - Select a narrow but valuable use case from earlier labs (for example configuration compliance checks or a standard change template).  
   - Define:
     - Scope (which devices and locations).  
     - Success criteria (for example manual effort saved, errors reduced).  
     - Rollback and fallback procedures if the orchestration tool is unavailable.
5. **Create an onboarding and governance outline**  
   - Describe:
     - How engineers will be trained and granted access to the orchestration platform.  
     - How playbooks or equivalent workflows are reviewed, tested, and approved before production use.  
     - How you will track versions and ownership of automation content over time.

### Design Diagram (Text Form)

Describe a conceptual diagram of your orchestration platform:

- An \"Orchestration Controller\" block at the centre.  
- \"Inventory and Source of Truth\" blocks feeding device lists and intent.  
- \"Network Devices and Controllers\" blocks that receive changes and checks.  
- \"Users and Processes\" blocks representing engineers, change management, and CI/CD.

Show the flow from intent and requests, through orchestration logic, to executed changes and feedback.

### Failure and What-If Analysis

Consider:

- The orchestration controller is unavailable during a planned change window. How do you proceed.  
- A playbook has an error that affects more devices than intended. How will you detect, stop, and roll back.  
- A security audit questions how credentials and access rights are managed within the orchestration platform.

For each case, describe:

- The potential impact and who is affected.  
- Controls and practices you would put in place (for example staged rollouts, approvals, credential vaults).  
- How those controls align with your earlier automation designs.

### Expected Outcomes

After completing this project you should be able to:

- Present a reasoned recommendation for a network orchestration platform.  
- Explain how it will integrate with your existing automation tools and processes.  
- Outline a practical, low-risk path from evaluation to initial production use.

### Reflection

Reflect on:

- Which orchestration features are genuinely valuable for your environment versus \"nice to have\".  
- Where you might start too big and how to keep the initial scope focused.  
- How you will keep orchestration content maintainable as the network and team evolve.

