## Advanced Network Assurance Lab 31 – Designing Always-On Visibility with NetFlow, SPAN, and IPSLA

### Scenario
Your organisation has historically relied on **ad-hoc troubleshooting** when network problems arise: engineers enable debug, SPAN, or packet captures only after users complain. This means that:

- Important evidence is often missing by the time you start investigating.  
- Performance trends are hard to see without historical baselines.  
- It is difficult to know whether a “fix” really solved the problem or if the issue simply disappeared.

Leadership wants a more proactive approach where the network continuously produces useful telemetry. In this lab you will design a set of **always-on visibility policies** using Flexible NetFlow, SPAN/RSPAN, and IPSLA so that you are better prepared for future incidents.

### Project Objectives

By the end of this project you should be able to:

- Identify which network segments and applications should be covered by baseline NetFlow export.  
- Decide where to configure SPAN/RSPAN for on-demand or limited continuous capture.  
- Design IPSLA tests that measure critical paths and applications over time.  
- Show how these telemetry sources combine into a practical visibility strategy.

### Technologies and Topics in Scope

This project draws from the Network Assurance section:

- **4.2 Flexible NetFlow** – Designing export points and record types for key services.  
- **4.3 Traffic mirroring** – SPAN, RSPAN, and ERSPAN usage for packet analysis.  
- **4.4 IPSLA** – Synthetic measurements to track performance trends.  
- **4.1, 4.5, 4.6** – How classic tools, controllers, and APIs consume this telemetry.

### Project Tasks

1. **Define visibility requirements**
   - List the top applications, services, or paths where you want ongoing visibility (for example internet edge, datacentre front-ends, critical WAN links).  
   - For each, decide what you need to know:
     - Traffic volume and patterns.  
     - Latency, loss, or jitter.  
     - Occurrence of specific events (for example retransmissions or resets).
2. **Plan Flexible NetFlow deployment**
   - Choose which interfaces or devices will export NetFlow records and to which collectors.  
   - Define record types (fields) that are most useful for performance and security analysis.  
   - Consider sampling vs full export and how much data your collectors can handle.
3. **Design SPAN/RSPAN strategy**
   - Identify a small number of strategic locations (for example core aggregation points) where SPAN or RSPAN can be configured quickly when deep packet analysis is needed.  
   - Decide whether any low-rate, continuous SPAN sessions are justified, or if all SPAN will be on-demand.  
   - Document how to avoid oversubscribing SPAN destinations or impacting production traffic.
4. **Define IPSLA test profiles**
   - Select critical paths (for example branch-to-datacentre, campus-to-internet edge) and configure or conceptualise IPSLA tests for them.  
   - Decide test frequency and thresholds for alerting.  
   - Plan how IPSLA results will be visualised (for example NMS graphs, controller dashboards).
5. **Integrate telemetry into operations**
   - Describe how NetFlow, SPAN, and IPSLA data will feed into your existing monitoring stack (NMS, SIEM, or controller).  
   - Define runbook entries: when an incident occurs, which telemetry sources should be checked first and how.  
   - Suggest periodic reviews of telemetry configuration to ensure it still matches business priorities.

### Failure and What-If Analysis

Consider these scenarios and describe how your telemetry design helps:

- Latency slowly increases on a key WAN link over several weeks.  
- A sudden spike in traffic saturates an internet edge link during business hours.  
- Users intermittently fail to connect to a SaaS application but internal metrics look normal.  
- A security team asks for historical information on traffic to a suspicious destination.

For each, explain:

- Which NetFlow, SPAN, or IPSLA data you would consult.  
- How having always-on visibility changes the speed and quality of your response.  
- Any gaps that still remain and how you might close them.

### Expected Outcomes

After completing this project you should be able to:

- Present a concrete plan for continuous network visibility using standard assurance tools.  
- Justify where and how telemetry is collected in terms of business value and operational cost.  
- Provide guidance on maintaining and evolving this visibility strategy over time.

### Reflection

Reflect on:

- How your proposed visibility design would have helped in past incidents you have experienced.  
- Which parts of the plan rely most on tooling versus process and discipline.  
- How you will measure whether your telemetry strategy is actually improving troubleshooting outcomes.


