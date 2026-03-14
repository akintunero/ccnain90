## Advanced Security Lab 41 – Phased Rollout of 802.1X, MAB, and WebAuth

### Scenario
Your network design now includes strong AAA, ACLs, and segmentation, but most access ports still operate in a **“trust the port”** model (for example open access with only basic VLAN assignment). Leadership wants to migrate to **identity-based access control** using 802.1X, MAB, and WebAuth across wired and wireless, but there is concern about:

- Breaking production access during rollout.  
- Supporting legacy or non-802.1X capable devices.  
- Handling guest and contractor access gracefully.

In this lab you will design a phased rollout plan for 802.1X, MAB, and WebAuth that balances security improvements with operational safety.

### Project Objectives

By the end of this project you should be able to:

- Propose a realistic migration strategy from open or static access to 802.1X/MAB/WebAuth.  
- Define policies for different device and user types (managed endpoints, BYOD, guests, IoT).  
- Explain how fallback mechanisms (MAB, WebAuth) will be used without weakening the overall posture.  
- Describe how to test and validate each phase before expanding deployment.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.1 Device access control**
  - 5.1.b Authentication and authorisation using AAA, including 802.1X.  
- **5.4 Components of network security design**
  - 5.4.a Threat defence considerations for access control choices.  
  - 5.4.c Next-generation firewall and policy engine integration for identity-aware enforcement.

### Project Tasks

1. **Classify endpoint and user types**
   - Identify categories such as:
     - Corporate-managed endpoints (laptops, desktops).  
     - BYOD devices.  
     - Guests and contractors.  
     - IoT or headless devices (printers, cameras, sensors).  
   - For each category, describe capabilities (for example 802.1X support) and security requirements.
2. **Define target access policies**
   - For each category, specify:
     - Preferred authentication method (802.1X, MAB, WebAuth).  
     - Resulting VLAN/segment or SGT.  
     - Any additional posture or compliance checks to be applied.  
   - Ensure that guest and BYOD access are appropriately limited and monitored.
3. **Design a phased deployment plan**
   - Phase 1: Monitor-only or low-impact deployment (for example 802.1X in audit mode, logging authentication results without enforcement).  
   - Phase 2: Enforce 802.1X for a subset of ports or user groups, with clear rollback procedures.  
   - Phase 3: Expand enforcement to broader areas, refine MAB and WebAuth handling for exceptions.  
   - For each phase, define success criteria and go/no-go checks.
4. **Plan operational support and troubleshooting**
   - Describe how helpdesk and operations will handle common issues (for example certificate problems, password expiry, unknown devices).  
   - List key logs and tools (for example AAA logs, switch/controller views) needed to diagnose access problems.  
   - Provide guidance on when to temporarily bypass enforcement (for example maintenance windows) and how to log such actions.
5. **Integrate with existing security services**
   - Show how identity information from 802.1X/MAB/WebAuth can be used by policy engines, NGFWs, or SIEMs.  
   - Consider how access decisions might change based on risk scores or endpoint posture.  
   - Outline how this identity-based model supports future zero-trust initiatives.

### Design Diagram (Text Form)

At a high level, describe:

- Where 802.1X, MAB, and WebAuth are enforced (wired ports, wireless SSIDs, guest portals).  
- How authentication flows from endpoints to access devices to AAA servers.  
- How different endpoint categories map to network segments or policies.

Use this as the basis for a diagram that highlights authentication and authorisation flows.

### Failure and What-If Analysis

Consider:

- A widespread 802.1X misconfiguration that prevents managed endpoints from authenticating.  
- Legacy or IoT devices that cannot support 802.1X and rely on MAB.  
- A captive portal outage affecting guest WebAuth access.  
- Sudden spikes in authentication failures due to password or certificate issues.

For each scenario, describe:

- Impact on users and services.  
- How your phased rollout and fallback mechanisms mitigate the impact.  
- What monitoring and alerting you would put in place to detect and respond quickly.

### Expected Outcomes

After completing this project you should be able to:

- Present a phased, low-risk plan for introducing 802.1X, MAB, and WebAuth across your network.  
- Explain how identity-based access control improves security without crippling operations.  
- Provide actionable guidance for operations and security teams to support the rollout.

### Reflection

Reflect on:

- Which groups or locations you would prioritise first for 802.1X enforcement.  
- How you will measure the success of the rollout (for example reduction in unauthorised access, improved visibility).  
- What training and communication are needed so users and support teams are prepared.


