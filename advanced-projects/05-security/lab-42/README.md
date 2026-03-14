## Advanced Security Lab 42 – Monitoring and Tuning Security Policies Over Time

### Scenario
You have implemented a range of security controls — AAA, ACLs, CoPP, segmentation, and access control — but security is not a “set and forget” exercise. Over time:

- New applications and services appear without corresponding policy updates.  
- Rules that were once necessary become obsolete or overly permissive.  
- Alert noise can cause important events to be missed.

Your CISO wants confidence that security policies are **actively monitored, reviewed, and tuned** using logs, APIs, and controller views. In this lab you will design how security controls are observed and adjusted over time rather than only during initial deployment.

### Project Objectives

By the end of this project you should be able to:

- Define key security metrics and logs that must be monitored.  
- Propose regular review and tuning processes for ACLs, access policies, and infrastructure protections.  
- Explain how controllers, APIs, and SIEM/SOAR platforms can assist in ongoing security operations.  
- Show how changes to policies are validated and documented.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.2 Infrastructure security features**
  - 5.2.a ACLs and related policy enforcement.  
  - 5.2.b CoPP and other control plane protections.  
- **5.3 REST API security**
  - How secure APIs are used to read and adjust configuration or gather telemetry.  
- **5.4 Components of network security design**
  - Threat defence, endpoint security, and NGFW integration in an operational context.

### Project Tasks

1. **Define security monitoring requirements**
   - List the types of events and metrics you need to watch, such as:
     - Denied connections from critical ACLs.  
     - Control plane drops or CoPP hits.  
     - Authentication failures and unusual AAA patterns.  
     - NGFW or IDS/IPS alerts tied to network segments.  
   - Decide where this data will be collected (for example SIEM, NMS, controller).
2. **Create a policy review and tuning process**
   - Propose how often ACLs, access policies, and CoPP rules are reviewed (for example quarterly).  
   - Define criteria for identifying rules that can be tightened or removed.  
   - Suggest how to involve application owners and security teams in the review.
3. **Leverage controllers and APIs**
   - Describe how a controller (for example Cisco Catalyst Center) or automation scripts could:
     - Check for policy consistency across devices.  
     - Highlight deviations from a defined baseline.  
     - Assist in rolling out or rolling back security changes.  
   - Consider API access controls and logging for any automated changes.
4. **Design change validation and rollback**
   - For each type of security control (ACLs, CoPP, access policies), define:
     - Pre-change checks and approvals.  
     - Post-change validation steps (for example targeted connectivity tests, log review).  
     - Clear rollback procedures and conditions.  
   - Ensure changes can be traced to specific tickets or requests.
5. **Integrate with incident response**
   - Explain how security monitoring feeds incident detection (for example alert thresholds, correlation rules).  
   - Describe how post-incident reviews will identify needed policy changes or tuning.  
   - Suggest how lessons learned will be captured in documentation and runbooks.

### Design Diagram (Text Form)

At a high level, describe:

- The flow of logs and metrics from devices, firewalls, and controllers into monitoring platforms.  
- How analysts or automated systems consume this data and trigger investigations.  
- Where policy changes originate and how they are propagated to network devices.

Use this as the basis for a diagram that shows both data flows and control flows in your security operations.

### Failure and What-If Analysis

Consider:

- Important security alerts being drowned out by low-value noise.  
- A critical policy change deployed without sufficient validation.  
- Monitoring gaps where certain segments or devices are not properly logged.  
- Loss of visibility due to SIEM or controller outages.

For each, describe:

- Potential impact on detection and response.  
- How your monitoring and tuning processes should address or mitigate the issue.  
- What improvements (process, tooling, or architecture) would further reduce risk.

### Expected Outcomes

After completing this project you should be able to:

- Present a realistic plan for continuous monitoring and tuning of network security policies.  
- Demonstrate how logs, APIs, and controller views are used to maintain security posture over time.  
- Provide operations and security teams with a framework for managing policy evolution safely.

### Reflection

Reflect on:

- How your organisation currently manages policy drift and whether it is sufficient.  
- Which aspects of monitoring and tuning would benefit most from automation.  
- How you will ensure that security operations keep pace with network and business changes.


