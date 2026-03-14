## Advanced Infrastructure Lab 23 – NTP and Time Synchronisation Design

### Scenario
During recent incidents, engineers discovered that device clocks across the network were significantly out of sync:

- Core switches and routers showed different times for the same event.  
- Wireless controllers and firewalls had their own NTP sources or local clocks.  
- Syslog and SIEM timelines were difficult to correlate with application logs.  

This made it hard to understand the true sequence of events and to prove what happened when. In this lab you will design a **network-wide NTP and time synchronisation strategy** so that infrastructure, security, and application components share a common, reliable sense of time.

### Project Objectives

By the end of this project you should be able to:

- Choose appropriate NTP (and where relevant PTP) time sources for the enterprise.  
- Design an NTP hierarchy that avoids single points of failure and keeps time consistent.  
- Map how accurate time supports troubleshooting, security investigations, and compliance.  
- Explain how your design fits into the broader IP services strategy.

### Technologies and Design Topics in Scope

This project focuses on the IP services portion of the Infrastructure  (3.3):

- **3.3 IP services**
  - 3.3.a Interpreting network time protocol configurations such as NTP and PTP.  
  - Related considerations for syslog and monitoring alignment.

### Project Tasks

1. **Assess current time synchronisation state**
   - Identify which devices are currently configured with NTP, and which rely on local clocks.  
   - Determine whether NTP servers are internal, external, or both.  
   - Note any devices that show obvious time drift or inconsistent timestamps in logs.
2. **Select authoritative time sources**
   - Decide whether the enterprise will use external public NTP servers, GPS-backed internal servers, or a combination.  
   - Consider which sites (campus, datacentre, DR) should host local NTP servers for resilience.  
   - Document any firewall or security requirements for NTP traffic.
3. **Design the NTP hierarchy**
   - Define which devices are NTP servers, clients, or both (for example, core routers acting as NTP servers for access devices).  
   - Plan stratum levels and redundancy so that the loss of a single server does not break time sync.  
   - Decide how branch sites will synchronise time, especially if WAN links are unreliable.
4. **Integrate time with logging and monitoring**
   - Describe how accurate time supports syslog, NetFlow, IPSLA, and security event correlation.  
   - Identify which logging and monitoring platforms must also follow the NTP design.  
   - Plan simple checks to validate that timestamps match across major systems.
5. **Document operational practices**
   - Provide guidance on how and when to change NTP servers (for example during migrations).  
   - Define what to check if a device shows incorrect time (NTP reachability, stratum, offset, and jitter).  
   - Suggest periodic audits to confirm that new devices follow the NTP standard.

### Design Diagram (Text Form)

Use this to sketch the time synchronisation topology:

- **Authoritative layer**
  - External or GPS-backed NTP servers and their connections to the enterprise.  
- **Core and distribution**
  - Devices that act as NTP servers for the rest of the network, including redundancy.  
- **Access and remote sites**
  - Access switches, routers, controllers, and security devices showing from which NTP servers they obtain time.

### Failure and What-If Analysis

Consider these scenarios and describe your design’s behaviour:

- The primary external NTP source becomes unreachable.  
- An internal NTP server’s clock drifts significantly due to misconfiguration.  
- A group of devices is accidentally left pointing to an obsolete NTP IP address.  
- A security policy change blocks NTP traffic between key sites.

For each, explain:

- How you would detect the issue (for example via logs, monitoring, or visible clock skew).  
- What failover or redundancy mechanisms mitigate the impact.  
- What corrective actions should be taken and how to avoid similar problems in future.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear, hierarchical NTP design for your enterprise network.  
- Show how accurate and consistent time improves troubleshooting and security investigations.  
- Provide simple instructions for operations to maintain and verify time synchronisation.

### Reflection

Reflect on:

- How critical accurate time is for your organisation’s specific applications and compliance needs.  
- Which parts of your NTP design are most sensitive to misconfiguration or neglect.  
- How you would incorporate PTP or more precise time mechanisms if future requirements demanded it.


