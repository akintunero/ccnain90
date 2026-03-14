## Advanced Security Lab 35 – Extending Campus Security to Branches and Remote Users

### Scenario
After hardening the main campus edge and access layer, your CISO wants to ensure that **branch sites and remote users** benefit from similar security controls. Today:

- Branch routers and switches still use local credentials and inconsistent ACLs.  
- Remote users connect via a basic VPN solution with limited policy control.  
- There is no unified view of which policies apply where.

You have been asked to extend your security design so that policies remain consistent end-to-end, from campus to branches to remote users, while taking into account the smaller scale and differing constraints at branch locations.

### Project Objectives

By the end of this project you should be able to:

- Describe how device access control and AAA will be extended to branches and remote access.  
- Propose an ACL and segmentation strategy that is consistent but right-sized for branch environments.  
- Explain how CoPP and basic threat defence apply to WAN and internet edges at branches.  
- Show how remote user VPN access fits into the overall security architecture.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.1 Device access control**
  - 5.1.a Lines and local user authentication for branch and remote-access devices.  
  - 5.1.b AAA-based authentication and authorisation extended beyond the campus.  
- **5.2 Infrastructure security features**
  - 5.2.a ACLs applied at branch routers, firewalls, and VPN gateways.  
  - 5.2.b CoPP considerations on smaller WAN and internet edge devices.  
- **5.4 Components of network security design**
  - 5.4.a Threat defence at branch edges.  
  - 5.4.b Endpoint security for remote users.  
  - 5.4.c Next-generation firewall roles for branch and VPN traffic.  
  - 5.4.d TrustSec and MACsec concepts where feasible.

### Project Tasks

1. **Assess current branch and remote access posture**
   - List existing branch locations, their WAN connectivity, and any local security devices (routers, firewalls).  
   - Describe how remote users currently connect (VPN type, authentication, and access scope).  
   - Identify major gaps compared to your hardened campus design.
2. **Extend AAA and device access controls**
   - Decide how branch routers/switches and VPN gateways will use central AAA (for example TACACS+ for admin access).  
   - Define fallback behaviour if AAA is unreachable from a branch.  
   - Plan how local credentials will be managed for break-glass scenarios.
3. **Define branch ACL and segmentation strategy**
   - Propose which traffic should be permitted between branch user networks, the campus, and the internet.  
   - Decide where ACLs will be enforced (on branch routers, firewalls, or both).  
   - Align branch segmentation (for example guest vs corporate) with campus policies where practical.
4. **Integrate remote user VPN access**
   - Describe how remote users authenticate (for example multi-factor authentication with centralized identity).  
   - Define which internal resources remote users may reach and how that access is enforced (firewalls, ACLs, or policy engines).  
   - Consider how remote access traffic will be inspected (for example through NGFW or security services).
5. **Plan monitoring and incident response for branches**
   - Identify which logs and telemetry must be collected from branch devices and VPN systems.  
   - Describe how branch security events will be correlated with campus events in monitoring or SIEM platforms.  
   - Outline procedures for responding to a suspected compromise at a branch or via a remote user account.

### Design Diagram (Text Form)

At a high level, describe:

- Branch site topology, including WAN edges, local switches, and any firewalls.  
- How branch user and guest networks connect back to the campus and internet.  
- Remote user VPN termination points and their placement relative to firewalls and core infrastructure.  
- Where AAA, ACLs, and other security controls are applied across campus, branches, and remote access.

### Failure and What-If Analysis

Consider:

- Loss of WAN connectivity from a branch to the central AAA servers.  
- Misconfigured ACLs at a branch that either over-permit or over-block traffic.  
- Compromise of a remote user’s VPN credentials.  
- A malware outbreak originating at a branch or remote user system.

For each scenario, describe:

- Likely impact on users and services.  
- How your extended security design helps detect and contain the issue.  
- What further improvements you might plan for higher maturity.

### Expected Outcomes

After completing this project you should be able to:

- Present a security design that ties campus, branches, and remote access into a consistent policy framework.  
- Explain how device access, segmentation, and threat defence work together across locations.  
- Provide operations with guidance on securing and monitoring smaller sites and remote users.

### Reflection

Reflect on:

- Which aspects of extending campus controls to branches were straightforward and which required adaptation.  
- How you would prioritise investments in branch and remote access security.  
- How this extended design sets the stage for future projects such as SD-WAN or zero-trust initiatives.


