## Advanced Security Lab 38 – Hardening a Campus Edge and Access Layer

### Scenario
Your current campus network was built with basic connectivity in mind, not security. Devices still use simple line passwords, there is little consistency in AAA, and ACLs have been added reactively over time. Wireless security is a mix of pre shared keys and open guest SSIDs, and there is no clear design for network access control.

Your CISO has asked you to propose a **security hardening plan** for the campus edge and access layer that:

- Improves device and management plane security.
- Introduces consistent access control using ACLs and QoS or CoPP where needed.
- Strengthens wireless security for corporate and guest users.
- Lays the groundwork for identity based access control using 802.1X and related methods.

In this scenario you work through where and how next-generation firewalls fit into the existing topology.


### Project Objectives

By the end of this project you should be able to:

- Describe how device access control will be implemented with AAA.  
- Propose an ACL strategy that protects infrastructure and enforces policy.  
- Explain how CoPP or similar techniques can protect the control plane.  
- Design wireless security profiles appropriate for corporate, BYOD, and guest.  
- Show where network access control methods such as 802.1X, MAB, and WebAuth will be used.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.1 Device access control**
  - 5.1.a Configuring and verifying lines and local user authentication.
  - 5.1.b Authentication and authorisation using AAA.
- **5.2 Infrastructure security features**
  - 5.2.a ACLs to enforce policy and protect infrastructure.
  - 5.2.b Control plane policing (CoPP).
- **5.3 REST API security**
  - Describing security considerations for REST APIs used to manage the network.
- **5.4 Components of network security design**
  - 5.4.a Threat defence.
  - 5.4.b Endpoint security.
  - 5.4.c Next-generation firewall placement and role.
  - 5.4.d TrustSec and MACsec as part of a secure architecture.

### Project Tasks

1. **Secure device access**
   - Define how administrators will log into routers, switches, and controllers (for example SSH with AAA).  
   - Decide which local accounts, if any, will remain for break glass scenarios.  
   - Plan line and VTY protections, including session limits and timeouts.
2. **Design AAA and authorization**
   - Choose an AAA model (for example TACACS+ for device admin, RADIUS for user auth).  
   - Describe how roles or command authorization will be used for network administrators.  
   - Decide where AAA servers will reside and how devices will reach them.
3. **Plan infrastructure ACLs and CoPP**
   - Identify management and control plane traffic that should be permitted to devices.  
   - Define ACLs that restrict who can reach device management interfaces.  
   - Outline how CoPP will protect control protocols from abuse.
4. **Define wireless security profiles**
   - Create profiles for:
     - Corporate devices (for example 802.1X with EAP).  
     - BYOD (for example WebAuth or PSK with additional controls).  
     - Guest (captured in a guest VLAN with appropriate internet access only).
   - Explain which authentication methods each profile will use and why.
5. **Design network access control**
   - Decide where 802.1X, MAB, and WebAuth will be applied (for example wired access ports, wireless SSIDs, guest portals).  
   - Show how the access layer will interact with central policy engines or firewalls.

### Design Diagram (Text Form)

At a high level, describe:

- Where AAA servers sit relative to the campus core.  
- How access switches are connected and where authenticated access will occur.  
- Where firewalls and other threat defence devices are placed.  
- How guest and corporate wireless traffic flows through the network.

Use this as the basis for a drawing that highlights security control points, not just connectivity.

### Failure and What-If Analysis

Consider:

- What happens when AAA servers are unreachable.  
- How users are affected if 802.1X fails or misbehaves.  
- What happens to management access when infrastructure ACLs are misconfigured.

For each scenario, describe:

- User and admin impact.  
- How you would detect the issue.  
- Which design choices (for example fallback methods or separate management VLANs) help reduce risk.

### Expected Outcomes

After completing this project you should be able to:

- Present a coherent security hardening plan for a campus network.  
- Link specific ENCOR security topics to concrete design decisions.  
- Explain how your design can be implemented in phases without major disruption.

### Reflection

Reflect on:

- Which controls give the best security improvement for the effort required.  
- How you balanced usability with strict access control.  
- Which areas would benefit most from integration with a broader security stack (for example endpoint security or SIEM correlation).

