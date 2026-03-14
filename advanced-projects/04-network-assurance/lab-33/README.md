## Advanced Network Assurance Lab 33 – Turning Telemetry into Operational Dashboards

### Scenario
Your network now exports a rich set of telemetry: NetFlow records from key interfaces, IPSLA tests for critical paths, syslog streams, and basic SNMP metrics. However:

- Most of this data is viewed only during incidents.  
- Different teams use different tools and dashboards, leading to inconsistent views.  
- Leadership wants high-level health indicators, while engineers need detailed drill-downs.

In this capstone assurance lab you will design how to **turn raw telemetry into actionable dashboards, alerts, and procedures** that support day-to-day operations and incident response.

### Project Objectives

By the end of this project you should be able to:

- Define key performance and health indicators (KPIs) for your network.  
- Design dashboards that present those KPIs at different levels (executive, NOC, engineer).  
- Specify alert thresholds and escalation paths based on telemetry.  
- Document procedures that link alerts and dashboards to concrete next actions.

### Technologies and Topics in Scope

This project draws from the Network Assurance  (4.x) in a synthesised way:

- **4.1–4.4** – Using diagnostics, NetFlow, SPAN/RSPAN, and IPSLA as data sources.  
- **4.5–4.6** – Leveraging controllers and APIs to feed and maintain dashboards.

### Project Tasks

1. **Define KPIs and audiences**
   - Identify key metrics that reflect network health, for example:
     - Interface utilisation and error rates.  
     - Latency/loss/jitter on critical paths.  
     - Application response times or transaction success rates (where visible).  
   - For each KPI, decide which audience cares most (leadership, NOC, engineers) and how often it should be reviewed.
2. **Design dashboard layouts**
   - Sketch at least two dashboard concepts:
     - An executive or leadership view with high-level status and trends.  
     - An operations/engineering view with more detailed metrics and drill-down capability.  
   - Describe which widgets, charts, or tables will appear and how they are sourced from telemetry.
3. **Define alerting and thresholds**
   - For each KPI or metric, decide:
     - What constitutes a warning vs a critical condition.  
     - How long a condition must persist before an alert is raised.  
   - Map alerts to on-call or escalation procedures, including what initial checks should be performed.
4. **Link dashboards and alerts to runbooks**
   - Choose a few representative alerts (for example high utilisation on a WAN link, IPSLA degradation, excessive drops on an interface).  
   - For each, specify:
     - Which dashboards or views engineers should consult first.  
     - Which troubleshooting runbook steps apply.  
     - How findings should be documented and closed out.
5. **Plan maintenance and evolution**
   - Describe how dashboard content and thresholds will be reviewed over time (for example quarterly reviews with operations and leadership).  
   - Consider how changes in applications or topology will be reflected in your assurance views.  
   - Identify any automation that could keep dashboards and alerting rules in sync with network changes.

### Failure and What-If Analysis

Consider these scenarios and describe how your dashboards and procedures help:

- A slow degradation in performance that does not trigger hard thresholds immediately.  
- A sudden, severe outage affecting a major site or application.  
- Noisy alerts that cause alert fatigue in the NOC.  
- Changes in business priorities that shift which KPIs matter most.

For each, explain:

- How dashboards and alerts should behave.  
- What adjustments to thresholds or visualisations might be needed.  
- How you ensure the system remains useful rather than overwhelming.

### Expected Outcomes

After completing this project you should be able to:

- Present a set of dashboard and alerting designs that make network health visible at a glance.  
- Show how those designs are grounded in the telemetry and tooling you have already planned.  
- Provide clear operational procedures that connect metrics to actions.

### Reflection

Reflect on:

- Which KPIs are most powerful in predicting or detecting issues early.  
- How you will measure the success of your dashboards and alerts (for example reduced MTTR, fewer surprise outages).  
- How you will keep your assurance views aligned with changing network and business realities.


