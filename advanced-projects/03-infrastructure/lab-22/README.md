## Advanced Infrastructure Lab 22 – Wireless Client Troubleshooting and Root Cause Mapping

### Scenario
After your new wireless design is rolled out, helpdesk tickets show a familiar pattern:

- Some users can see SSIDs but cannot obtain an IP address.  
- Others connect but experience frequent disconnects or timeouts.  
- A few report that Wi‑Fi works in some areas but not others, even on the same SSID.  

Many of these issues are blamed on “the Wi‑Fi”, but investigation often reveals underlying Layer 2 or Layer 3 causes (VLANs, routing, DHCP, DNS, or firewall policies). In this lab you will develop a **structured troubleshooting approach for wireless client issues** and explicitly map findings back to the wired infrastructure.

### Project Objectives

By the end of this project you should be able to:

- Classify common wireless client problems and link them to specific infrastructure components.  
- Define a repeatable troubleshooting flow that moves from client to AP to controller to wired network.  
- Identify which Layer 2 and Layer 3 checks are most important when Wi‑Fi users report problems.  
- Document findings in a way that helps both wireless and wired teams collaborate.

### Technologies and Design Topics in Scope

This project continues the Infrastructure focus (3.x), with emphasis on:

- **3.1 Layer 2**
  - Evaluating VLAN membership and trunk behaviour for wireless SSID mappings.  
- **3.2 Layer 3**
  - Verifying gateway reachability and routing for wireless client subnets.  
- **3.3 IP services**
  - Checking DHCP, DNS, and first-hop redundancy for wireless VLANs.

### Project Tasks

1. **Define typical wireless client problem categories**
   - Connectivity failures (cannot see SSID, cannot associate, cannot obtain IP).  
   - Performance issues (slow throughput, high latency, intermittent drops).  
   - Reachability issues (can reach local resources but not internet, or vice versa).  
   - Authentication or captive portal problems.
2. **Design a step-by-step troubleshooting flow**
   - Start at the client: verify basic settings, signal strength, and association status.  
   - Move to the AP: check which SSID/VLAN the client is on and whether the AP has successfully joined the controller.  
   - Follow the path into the wired network: confirm VLAN tagging on switch ports, SVI reachability, and routing.  
   - Check DHCP, DNS, and any firewalls or ACLs on the path.
3. **Identify key commands and data sources**
   - On controllers/APs: logs, client sessions, RF statistics.  
   - On switches/routers: interface status, VLAN and trunk configuration, routing table entries, ARP/ND tables.  
   - On servers or infrastructure services: DHCP leases, DNS responses, authentication logs.
4. **Create example troubleshooting stories**
   - Write at least two short case studies, for example:
     - A client that associates but fails DHCP due to a missing helper address.  
     - A user who can reach internal apps but not the internet because of an ACL on the edge.  
   - For each story, show how your flow leads from the symptom to the root cause.
5. **Develop a handoff template**
   - Create a simple template that helpdesk or junior engineers can fill in before escalating:  
     - Client details (MAC, IP, SSID, location).  
     - Initial checks performed and results.  
     - Suspected infrastructure component (AP, controller, switch, router, firewall, server).

### Design Diagram (Text Form)

Use this to sketch a troubleshooting-oriented view:

- **Client and RF edge**
  - Client connecting to an AP, with SSID and VLAN mapping annotated.  
- **Wireless infrastructure**
  - Controller or management plane components that track client state.  
- **Wired path**
  - Access switch, distribution/core, gateway, and internet edge showing where DHCP, DNS, and ACLs reside.

### Failure and What-If Analysis

Consider and describe how your troubleshooting flow handles:

- A misconfigured access switch port that places AP traffic in the wrong VLAN.  
- A DHCP server outage for a wireless subnet.  
- A change in firewall policy that unintentionally blocks wireless clients only.  
- RF-only issues (for example interference or low signal) where the wired path is healthy.

For each, explain:

- The observable client symptoms.  
- Which points in your flow would reveal the problem.  
- How you would document the resolution and update runbooks to prevent repeat incidents.

### Expected Outcomes

After completing this project you should be able to:

- Lead a structured investigation of wireless client problems that quickly distinguishes RF from wired issues.  
- Provide operations staff with a clear, reusable checklist for Wi‑Fi incident handling.  
- Improve collaboration between wireless and wired teams by clearly mapping responsibilities.

### Reflection

Reflect on:

- Which parts of the troubleshooting flow are most likely to be skipped under time pressure and how to prevent that.  
- How tooling (controller dashboards, logs, NMS) can make this process faster and more accurate.  
- What training or documentation would help non-wireless specialists handle basic Wi‑Fi tickets more confidently.


