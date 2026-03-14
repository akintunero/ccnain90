## Advanced Security Lab 39 – Combining Endpoint and Network Controls for Layered Defence

### Scenario
Your network security design has focused heavily on infrastructure controls so far: AAA, ACLs, CoPP, and segmentation at the campus and branch edges. However, recent incidents have highlighted that **endpoint security posture** (for example antivirus, EDR agents, operating system patch levels) is just as important:

- Some compromised endpoints had full network access despite weak local controls.  
- Network logs showed suspicious behaviour, but endpoint telemetry provided the real root cause.  
- Security teams want a clearer model for how endpoint and network controls should work together.

In this lab you will design how endpoint security tools and network security features complement each other to create a layered defence strategy.

### Project Objectives

By the end of this project you should be able to:

- Describe the respective roles of endpoint security and network security controls.  
- Propose ways to share information between endpoint tools (for example EDR, AV) and network components (for example firewalls, switches, controllers).  
- Explain how network access and segmentation can respond to endpoint risk signals.  
- Outline incident response workflows that leverage both endpoint and network telemetry.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.4 Components of network security design**
  - 5.4.a Threat defence.  
  - 5.4.b Endpoint security.  
  - 5.4.c Next-generation firewall placement.  
  - 5.4.d TrustSec and MACsec concepts as part of a broader architecture.  

### Project Tasks

1. **Clarify endpoint vs network responsibilities**
   - Define what endpoint security tools are responsible for (for example malware detection, host firewalling, posture assessment).  
   - Define what network security components are responsible for (for example segmentation, traffic inspection, access control).  
   - Identify areas of overlap and where coordination is most important.
2. **Design information sharing and integration points**
   - Describe how endpoint tools can signal risk to the network (for example via APIs, tags, or group membership changes).  
   - Propose how NGFWs, controllers, or policy engines might consume those signals to adjust access (for example quarantining a host).  
   - Consider how SIEM or SOAR platforms fit into this picture.
3. **Align segmentation with endpoint posture**
   - Propose a simple model where endpoint posture (for example compliant vs non-compliant) influences which VLANs, SGTs, or policies apply.  
   - Describe how 802.1X, MAB, and WebAuth could be used to place endpoints into appropriate segments based on identity and posture.  
   - Note any constraints in your current environment that would affect this design.
4. **Plan joint incident response workflows**
   - Choose at least two incident types (for example malware on a user laptop, suspicious lateral movement from a server).  
   - For each, describe:
     - What endpoint tools detect and how they respond locally.  
     - What network changes are made (for example blocking IPs/domains, isolating a host, tightening ACLs).  
     - How evidence from both sides is correlated to understand impact.
5. **Document governance and ownership**
   - Define who owns endpoint policies and who owns network policies, and how they coordinate.  
   - Suggest regular review meetings or processes to keep endpoint and network strategies aligned.  
   - Note any training or documentation required so teams understand each other’s tools and constraints.

### Design Diagram (Text Form)

At a high level, describe:

- Where endpoint security tools sit in relation to network components (for example agents on hosts, management consoles, NGFWs, controllers).  
- How signals about endpoint health or risk flow to network devices or policy engines.  
- How traffic from different endpoint categories (trusted, at-risk, guest) flows through the network and security stack.

Use this as the basis for a diagram that highlights both endpoint and network control layers.

### Failure and What-If Analysis

Consider:

- Endpoint tools fail to report posture or status correctly.  
- Network segmentation is misaligned with endpoint risk levels.  
- A large number of endpoints suddenly report as high-risk (for example widespread malware campaign).  
- Disagreements between endpoint and network teams about who should act first during an incident.

For each scenario, describe:

- Potential impact on security and operations.  
- How your layered design mitigates or exposes risk.  
- Which process or technical improvements would reduce the chance or impact of such situations.

### Expected Outcomes

After completing this project you should be able to:

- Explain a clear, layered defence model that uses both endpoint and network controls.  
- Show how endpoint telemetry and network telemetry work together in investigations.  
- Provide practical guidance for improving coordination between endpoint and network security teams.

### Reflection

Reflect on:

- Where your current organisation relies too heavily on either endpoint or network controls alone.  
- How you would prioritise integration work between endpoint and network tools.  
- How this layered approach supports broader security frameworks such as zero trust.


