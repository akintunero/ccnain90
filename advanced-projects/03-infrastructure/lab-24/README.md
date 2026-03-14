## Advanced Infrastructure Lab 24 – NAT/PAT Design at the Enterprise Edge

### Scenario
Your organisation is preparing to standardise internet and partner connectivity across multiple sites. Today:

- Some sites use one-to-one static NAT on firewalls.  
- Others use many-to-one PAT on edge routers with overlapping internal address ranges.  
- There is no consistent approach for which internal networks can reach which external services.  

As more SaaS applications and partner connections are added, this ad-hoc NAT/PAT behaviour is causing troubleshooting headaches and security reviews. In this lab you will design a **coherent NAT/PAT strategy at the enterprise edge**, including how it will evolve if a second ISP or additional partner links are introduced.

### Project Objectives

By the end of this project you should be able to:

- Differentiate when to use static NAT, dynamic NAT, and PAT in an enterprise design.  
- Propose a standard NAT/PAT model for user, server, and guest networks at the edge.  
- Consider how overlapping private address space will be handled.  
- Explain how your NAT/PAT design interacts with routing, security policies, and logging.

### Technologies and Design Topics in Scope

This project focuses on the IP services portion of the Infrastructure  (3.3):

- **3.3 IP services**
  - 3.3.b Configuring NAT/PAT for edge connectivity.  
  - Related placement of first-hop redundancy and firewalls.

### Project Tasks

1. **Inventory current NAT/PAT usage**
   - List which devices currently perform NAT/PAT (routers, firewalls, or both).  
   - For each site, identify:
     - Which internal networks are translated.  
     - Which public or provider-assigned address ranges are used.  
     - Any known overlapping private address ranges between sites.
2. **Define NAT/PAT design goals**
   - Clarify requirements for:
     - Internet access from user and guest networks.  
     - Server-initiated and inbound connections (for example published services).  
     - Partner or VPN connections that may require specific address presentation.  
   - Decide whether a common edge policy can be applied across most sites.
3. **Propose a standard NAT/PAT model**
   - Decide where NAT/PAT will live (edge routers, firewalls, or a combination).  
   - Specify:
     - Which networks use PAT to reach the internet.  
     - Which services require static NAT or port forwarding.  
     - How guest or untrusted networks are isolated and translated.  
   - Address how overlapping private ranges (for example 192.168.0.0/16) will be handled between sites or partners.
4. **Plan for growth and multiple ISPs**
   - Describe how your NAT/PAT design would extend to a dual-ISP environment (for example different public address pools per ISP, failover behaviour).  
   - Consider how policy-based routing, VRFs, or separate firewalls might be involved.  
   - Note how logging and security monitoring will track translated connections across edges.
5. **Document operational practices**
   - Define how new NAT rules are requested, approved, and implemented to avoid sprawl.  
   - Provide a checklist for verifying changes (for example test connectivity, confirm logs, validate security policy alignment).  
   - Suggest periodic clean-up reviews to remove unused or risky NAT entries.

### Design Diagram (Text Form)

Use this to sketch your NAT/PAT design:

- **Internal zones**
  - User, server, management, and guest networks with their internal address ranges.  
- **Edge devices**
  - Routers and/or firewalls performing NAT/PAT, annotated with public address pools.  
- **External zones**
  - Internet and any partner or VPN clouds, indicating which translated addresses they see.

### Failure and What-If Analysis

Consider these scenarios and describe the impact on your design:

- Exhaustion of the available public address pool used for PAT.  
- A misconfigured static NAT that unintentionally exposes an internal host.  
- A change in partner requirements that mandates different source addresses.  
- Introduction of a second ISP with different public address blocks.

For each, explain:

- How connectivity and security may be affected.  
- Which controls (for example ACLs, firewalls, or NAT order-of-operations) help reduce risk.  
- What steps operations should take to resolve the issue and prevent recurrence.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear NAT/PAT design for the enterprise edge that balances simplicity, security, and flexibility.  
- Show how it supports current internet and partner connectivity while preparing for future growth.  
- Provide actionable guidance for implementing and maintaining NAT/PAT configurations across sites.

### Reflection

Reflect on:

- How NAT/PAT complexity can creep in over time and how your design addresses that risk.  
- Which stakeholders (security, application owners, partners) need to understand your addressing and translation model.  
- How future technologies (for example IPv6 adoption) might change or simplify your NAT/PAT strategy.


