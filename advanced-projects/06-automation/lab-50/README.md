## Advanced Automation Lab 50 – Automation Strategy and Skills Roadmap (Final Capstone)

### Scenario
Your organisation has decided that network automation is a strategic priority. You now have several concrete designs on the table:

- A configuration compliance checker.  
- Event-driven alerting and remediation.  
- API-driven change windows.  
- A self-service task portal.  
- An orchestration platform evaluation.

Leadership is asking a bigger question: **\"What is our five-step plan to become an automation-enabled network team over the next 12–24 months?\"** They want a strategy that balances technology, process, and skills, without putting the production network at unnecessary risk.

In this final capstone you will build an **automation strategy and skills roadmap** that ties all previous labs together and sets direction for the team.

### Project Objectives

By the end of this project you should be able to:

- Articulate a clear vision for how automation will change day-to-day network operations.  
- Prioritise automation initiatives based on value, risk, and readiness.  
- Define the skills, roles, and training your team needs at each stage.  
- Propose governance practices that keep automation safe, auditable, and maintainable.

### Technologies and Topics in Scope

This project draws from all elements of the Automation  (6.x), but the focus is on **planning and integration** rather than new tools:

- Python, JSON, and YANG as core building blocks.  
- APIs (controllers and device-level) as primary interfaces.  
- EEM and orchestration platforms as execution engines.  
- Documentation, version control, and testing as foundations for trust.

### Project Tasks

1. **State the current baseline**  
   - Describe your starting point in terms of:
     - How changes are performed today (manual CLI, scripts, some automation).  
     - What monitoring and logging exists.  
     - Current skill levels with Python, APIs, and automation tools.  
   - List key pain points that automation should help with (for example change errors, slow rollouts, lack of visibility).
2. **Define the target vision**  
   - In one or two pages, describe what \"automation-enabled networking\" looks like for you, for example:
     - Most routine checks and reports are automated.  
     - Standard changes are executed via APIs or orchestration tools with pre/post checks.  
     - Engineers use a shared automation repository with review and testing.  
   - Make sure this vision is realistic for a CCNA-level environment, not a full software development shop.
3. **Design a phased roadmap**  
   - Propose at least four phases, such as:
     - Phase 1: Read-only automation (inventory, compliance, reporting).  
     - Phase 2: Assisted change windows using APIs and scripts.  
     - Phase 3: Event-driven automation for a small set of well-understood incidents.  
     - Phase 4: Carefully scoped orchestration and self-service for selected tasks.  
   - For each phase, list:
     - Goals and success metrics.  
     - Prerequisite tools and skills.  
     - Clear \"do not automate yet\" boundaries.
4. **Create a skills and roles plan**  
   - Identify:
     - Which skills every network engineer should have (for example reading simple Python, understanding JSON and APIs).  
     - Which skills belong to a smaller group of automation champions (for example writing scripts, designing playbooks).  
     - How you will deliver training (internal sessions, labs, external courses).  
   - Suggest how responsibilities for maintaining automation content will be shared and reviewed.
5. **Define governance and safety practices**  
   - Document how you will:
     - Use version control for scripts and playbooks.  
     - Review and test automation before production use.  
     - Handle credentials and access rights securely.  
     - Respond when automation behaves unexpectedly (for example temporary rollback to manual processes).

### Design Diagram (Text Form)

Describe a high-level \"automation strategy\" diagram:

- A timeline with your roadmap phases.  
- A \"People and Skills\" layer showing how capability grows over time.  
- A \"Tools and Platforms\" layer showing when controllers, orchestration, and portals are introduced.  
- A \"Use Cases\" layer highlighting which problems are tackled in each phase.

Use this as a visual aid when presenting your plan to leadership or peers.

### Failure and What-If Analysis

Consider:

- The roadmap moves too fast and engineers feel overwhelmed or bypassed.  
- Automation projects stall because there is no dedicated time or ownership.  
- A high-profile automation error reduces trust in the whole programme.

For each case, describe:

- Early warning signs that the strategy needs adjustment.  
- Mitigations built into your plan (for example pilots, staged rollouts, clear fallback paths).  
- How you will communicate openly about risks and lessons learned.

### Expected Outcomes

After completing this project you should be able to:

- Present a coherent, phased automation strategy to technical and non-technical stakeholders.  
- Show how the individual labs and designs in this track support that strategy.  
- Give your team a concrete, realistic path from where they are today to an automation-enabled future.

### Reflection

Reflect on:

- What excites you most and what worries you most about this roadmap.  
- Which single next step would deliver the most value with the least risk.  
- How you will keep the roadmap alive as a living document rather than a one-time exercise.

