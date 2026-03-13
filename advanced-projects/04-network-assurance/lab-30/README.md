## Advanced Network Assurance Lab 29 – Finding the Slow Application

### Scenario
Users across several departments are complaining that a key internal web application is "slow at random times". Sometimes it works fine, sometimes pages hang for many seconds. No major outages are visible, and basic pings look normal most of the time. Leadership wants a clear answer to:

- Where the problem is (network, server, or application).
- How confident you are in that answer.
- What data you used to reach your conclusion.

You have been asked to use the network assurance and monitoring tools available in the environment to investigate and explain the situation.

### Project Objectives

By the end of this project you should be able to:

- Use classic tools such as ping, trace route, debugs, SNMP, and syslog in a structured way.  
- Explain how NetFlow or Flexible NetFlow help you understand traffic patterns.  
- Show how SPAN or RSPAN captures can confirm or rule out network issues.  
- Use IPSLA style tests to measure performance over time.  
- Describe where a controller such as Cisco DNA Center or NETCONF/RESTCONF based automation could simplify ongoing assurance.

### Technologies and Topics in Scope

This project maps to the ENCOR Network Assurance section:

- Diagnosing problems with debugs, conditional debugs, trace route, ping, SNMP, and syslog.  
- Device monitoring and remote logging with syslog.  
- NetFlow and Flexible NetFlow.  
- SPAN, RSPAN, and ERSPAN.  
- IPSLA.  
- Cisco DNA Center style configuration and monitoring workflows.  
- NETCONF and RESTCONF for programmatic monitoring or configuration.

### Project Tasks

You can work through these tasks conceptually, or by building a small lab that simulates the pattern.

1. **Clarify the problem**
   - Define which application is slow and from which locations.  
   - Ask what "slow" means in measurable terms (for example more than 3 seconds to load a page).
2. **Baseline connectivity**
   - Use ping and trace route from representative user locations to the application front end.  
   - Document latency, path, and any asymmetry in routing.
3. **Collect device health and logs**
   - Review CPU, memory, and interface statistics from key routers and switches using SNMP or CLI.  
   - Check syslog for interface flaps, error counters, or protocol issues in the relevant time windows.
4. **Examine traffic flows with NetFlow**
   - Look at NetFlow or Flexible NetFlow records for the application.  
   - Identify changes in volume, top talkers, or unusual flows during slow periods.
5. **Use SPAN or RSPAN strategically**
   - Decide where to mirror traffic (for example on a core or aggregation interface).  
   - Capture a short window of traffic during a slow period and review for retransmissions, resets, or application level issues.
6. **Configure or interpret IPSLA style tests**
   - Set up or review existing IPSLA probes that measure HTTP or TCP performance to the application.  
   - Compare probe results during normal and degraded periods.
7. **Consider controller and API based workflows**
   - If you imagine using Cisco DNA Center or similar, describe how its dashboards and path traces could speed up this investigation.  
   - Note where NETCONF/RESTCONF based scripts could automate checks across devices.

### Failure and What-If Analysis

Consider and document how your assurance approach would change if:

- The issue only affected users at a single branch.  
- The issue only occurred during backup windows in the datacentre.  
- The application was moved from on premises to a cloud provider.

For each variation, list:

- Which tools you would rely on most.  
- Which new data sources you would need.

### Expected Outcomes

At the end of this lab you should be able to:

- Present a reasoned hypothesis about the root cause of the slow application.  
- Support your position with specific evidence from assurance tools.  
- Explain what additional data you would collect if you had more time or access.

### Reflection

Reflect on:

- Which tools gave you the highest value information for this kind of problem.  
- How you might build permanent dashboards or alerts so that similar issues are detected earlier in the future.  
- How automation or controller based workflows could reduce the manual effort involved in your investigation.

