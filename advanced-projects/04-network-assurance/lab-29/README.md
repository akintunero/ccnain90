## Advanced Network Assurance Lab 29 – Investigating a “Sometimes Slow” Internal Application

### Scenario
Users across several departments are complaining that a key internal web application is “slow at random times”. Sometimes it loads in under a second, and sometimes pages hang for many seconds. No major outages are visible, and basic pings and simple connectivity checks often look fine. Leadership wants a clear, evidence-based answer to three questions:

- Is the bottleneck in the **network, server, or application** layer?  
- How confident are you in that conclusion?  
- What specific data backs up your assessment?

You have been asked to use the network assurance and monitoring tools available in the environment to investigate and explain the situation in a way that non-network stakeholders can understand.

### Project Objectives

By the end of this project you should be able to:

- Apply a structured troubleshooting approach to intermittent performance issues.  
- Use tools such as ping, traceroute, debugs, SNMP, syslog, NetFlow, SPAN/RSPAN, and IPSLA in a coordinated way.  
- Correlate network evidence with application behaviour to support or refute “it’s the network” claims.  
- Summarise your findings and confidence level in a short investigation report.

### Technologies and Topics in Scope

This project draws from the Network Assurance section:

- **4.1 Problem diagnosis tools**
  - Using debugs and conditional debugs, traceroute, ping, SNMP, and syslog to diagnose issues.  
- **4.2 Flexible NetFlow**
  - Observing traffic patterns for the application over time.  
- **4.3 Traffic mirroring**
  - Using SPAN or RSPAN for targeted packet capture.  
- **4.4 IPSLA**
  - Measuring application or transport performance across the network.  
- **4.5 Cisco Catalyst Center workflows**
  - Considering how controller-based views could accelerate analysis.  
- **4.6 Model-driven interfaces**
  - Where NETCONF/RESTCONF could help automate data collection.

### Project Tasks

1. **Clarify and quantify the problem**
   - Identify the application (URL, servers, ports) and affected user locations.  
   - Define what “slow” means in measurable terms (for example more than 3 seconds to load the main dashboard).  
   - Capture when the problem occurs (time-of-day patterns, specific days, or events like backups).
2. **Establish basic connectivity and path**
   - From representative user locations, record ping latency and loss to the application front-end.  
   - Run traceroute/pathtrace to confirm the network path and detect any routing asymmetry.  
   - Note whether the problem correlates with obvious connectivity issues or only with higher-layer behaviour.
3. **Collect device health and logs**
   - Review CPU, memory, and interface utilisation on key routers and switches along the path using SNMP or CLI.  
   - Inspect syslog for interface errors, flaps, or protocol events in the time windows when users report slowness.  
   - Document whether the network appears healthy or under stress during incidents.
4. **Analyse flows and packets**
   - Use NetFlow or Flexible NetFlow to examine traffic for the application:
     - Volume, top talkers, and any unusually large or bursty flows.  
     - Changes in patterns during normal vs slow periods.  
   - Use SPAN or RSPAN on a strategic interface to capture a short packet trace during a slow period:
     - Look for retransmissions, resets, or high application-layer response times.
5. **Use IPSLA or synthetic tests**
   - Configure or review IPSLA probes (for example HTTP or TCP connect) targeting the application front-end.  
   - Compare probe results across time windows and from different network locations.  
   - Determine whether the network path itself ever shows significant latency or loss spikes.
6. **Formulate and document findings**
   - Summarise evidence that points toward or away from the network as the root cause.  
   - Clearly state your working hypothesis (for example “likely server/application-side issue with no strong network evidence”).  
   - List any remaining questions or tests that would further increase your confidence.

### Failure and What-If Analysis

Consider and document how your assurance approach would change if:

- The issue only affected users at a single branch.  
- The issue only occurred during backup windows in the datacentre.  
- The application front-end servers were moved from on-premises to a cloud provider.

For each variation, list:

- Which tools and data sources you would rely on most.  
- What additional instrumentation (for example cloud provider logs, WAN performance metrics) would be required.

### Expected Outcomes

At the end of this lab you should be able to:

- Present a reasoned, evidence-backed hypothesis about the root cause of the slow application.  
- Explain your level of confidence and what further data would either confirm or challenge your conclusion.  
- Suggest concrete next steps for application, server, or network teams based on your findings.

### Reflection

Reflect on:

- Which tools and data turned out to be most useful for this kind of intermittent performance issue.  
- How you might improve baseline monitoring (dashboards, alerts, synthetic tests) to detect similar problems earlier.  
- How controller-based or automated workflows could reduce the manual effort of this style of investigation.


