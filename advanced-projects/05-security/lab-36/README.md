## Advanced Security Lab 36 – AAA Policy Design for Devices and Users

### Scenario
Your organisation has decided to centralise authentication and authorisation using AAA for both **network devices** and **end users**. At the moment:

- Some devices still rely on local usernames and passwords.  
- Different teams operate separate RADIUS/TACACS+ servers with inconsistent policies.  
- Wired and wireless user access is not aligned to a common identity model.

The CISO wants a unified AAA strategy that improves security and simplifies operations across campus, branches, and remote access. In this lab you will design AAA policies for device administration and user access, and show how they fit into your broader security architecture.

### Project Objectives

By the end of this project you should be able to:

- Design AAA policies for network device administration using TACACS+ or RADIUS.  
- Define AAA policies for user access across wired and wireless networks.  
- Show how AAA ties into network access control mechanisms such as 802.1X, MAB, and WebAuth.  
- Explain how AAA design supports auditing, compliance, and incident response.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.1 Device access control**
  - 5.1.a Lines and local user authentication in a AAA context.  
  - 5.1.b Authentication and authorisation using AAA servers.  
- **5.4 Components of network security design**
  - 5.4.a Threat defence and logging from a AAA perspective.  
  - 5.4.d How TrustSec or similar technologies might consume AAA-derived attributes.

### Project Tasks

1. **Assess current AAA usage**
   - Inventory which devices use central AAA today and which rely on local credentials.  
   - Identify existing AAA servers, protocols (TACACS+/RADIUS), and policies in use.  
   - Note any overlapping or conflicting policies across teams or sites.
2. **Design AAA for device administration**
   - Choose a standard approach for device admin AAA (for example TACACS+ for command authorisation).  
   - Define roles or privilege levels for different administrator types (for example read-only, operator, engineer).  
   - Decide how logs and accounting records will be stored for auditing.
3. **Design AAA for user access**
   - Decide how users will authenticate to the network (for example 802.1X for corporate, WebAuth/portal for guests).  
   - Map user groups (for example employees, contractors, guests) to appropriate policies and VLANs or SGTs.  
   - Consider how remote users (VPN) fit into the same identity framework.
4. **Integrate AAA with network access control**
   - Show how AAA servers interact with switches, wireless controllers, and VPN gateways.  
   - Describe how attributes from AAA (for example group membership, posture) can influence access control decisions.  
   - Outline how AAA failures will be handled (for example fail-open vs fail-closed, limited access VLANs).
5. **Document operational and security considerations**
   - Define procedures for creating, modifying, and removing AAA policies.  
   - Describe how AAA-related incidents (for example account lockouts, misconfigurations) will be detected and resolved.  
   - Suggest periodic reviews of AAA logs to detect suspicious activity.

### Design Diagram (Text Form)

At a high level, describe:

- The placement of AAA servers relative to campus, branch, and VPN infrastructure.  
- How devices (switches, routers, controllers, VPN gateways) communicate with AAA.  
- The flow of user authentication from endpoint to network device to AAA server and back.

Use this as the basis for a diagram that highlights identity and policy decision points.

### Failure and What-If Analysis

Consider:

- Outage of a primary AAA server or loss of connectivity to the AAA cluster.  
- Misconfigured AAA policies that deny access to administrators or legitimate users.  
- Attackers attempting to brute-force accounts or misuse stolen credentials.  
- A need to quickly revoke access for a compromised account or device.

For each scenario, describe:

- The expected behaviour of network devices and user sessions.  
- How your AAA design helps detect and contain the issue.  
- What changes or safeguards (for example secondary AAA servers, rate limiting, monitoring) you would put in place.

### Expected Outcomes

After completing this project you should be able to:

- Present a unified AAA policy design covering devices, users, and remote access.  
- Explain how it aligns with broader security and compliance requirements.  
- Provide guidance to operations and security teams on maintaining and auditing AAA.

### Reflection

Reflect on:

- How centralised AAA changes the way your organisation thinks about identity and access.  
- Which aspects of AAA design are most critical to document clearly.  
- How you will evolve your AAA architecture as your network and requirements grow.


