## Advanced Security Lab 37 – Infrastructure ACLs and Control Plane Policing Strategy

### Scenario
Now that you have a clearer AAA design, leadership is concerned that **management and control planes** are still too exposed:

- Device management interfaces are reachable from more networks than necessary.  
- Infrastructure ACLs have grown organically and are hard to review.  
- There is limited protection against malformed or excessive control-plane traffic.

In this lab you will design an infrastructure ACL (iACL) and Control Plane Policing (CoPP) strategy that defines exactly which traffic is allowed to reach network devices and at what rate, without breaking legitimate operations.

### Project Objectives

By the end of this project you should be able to:

- Design iACL policies that protect management and infrastructure services.  
- Define CoPP classes and policies that protect routing and control protocols.  
- Explain how iACLs and CoPP complement each other in your security architecture.  
- Plan how these controls will be deployed and maintained safely.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.2 Infrastructure security features**
  - 5.2.a ACLs to enforce policy and protect infrastructure.  
  - 5.2.b Control plane policing (CoPP).  
- **5.1 Device access control**
  - How iACLs and CoPP interact with AAA and management access.

### Project Tasks

1. **Identify required management and control traffic**
   - List which protocols and services must reach network devices (for example SSH, SNMP, NTP, syslog, routing protocols, CDP/LLDP as needed).  
   - For each, specify the legitimate source networks (for example NOC subnets, management VLANs, trusted monitoring systems).  
   - Note any legacy or unnecessary protocols that should be phased out.
2. **Design infrastructure ACLs (iACLs)**
   - Propose ACLs that:
     - Explicitly permit required management and control traffic from authorised sources.  
     - Deny or log unexpected traffic to device addresses.  
   - Decide where these ACLs will be applied (for example inbound on edge interfaces or on dedicated management interfaces).  
   - Consider how iACLs will be kept consistent across devices.
3. **Define CoPP classes and policies**
   - Group control-plane traffic into classes (for example routing, management, general control).  
   - Propose rate limits or policing actions that protect the CPU while allowing normal operation.  
   - Describe how CoPP policies will be tested in a lab before production deployment.
4. **Plan deployment and validation**
   - Outline a phased rollout approach, starting with monitoring-only or log-only policies where possible.  
   - Define checks to ensure that legitimate management sessions and protocol adjacencies are not broken.  
   - Describe how you will roll back quickly if unintended impact is observed.
5. **Document operations and change management**
   - Specify how new management tools or services will be onboarded into iACL and CoPP policies.  
   - Define who can request changes and how they are reviewed.  
   - Suggest periodic audits to ensure policies still match the environment.

### Design Diagram (Text Form)

At a high level, describe:

- Where iACLs are applied in the topology (core, distribution, edge, management interfaces).  
- Which devices implement CoPP and which classes of traffic they protect.  
- The flow of legitimate management and control traffic through the network.

Use this as the basis for a diagram that highlights protection boundaries around your infrastructure.

### Failure and What-If Analysis

Consider:

- An overly strict iACL that blocks legitimate management access.  
- A CoPP policy that is too aggressive and causes routing adjacencies to flap.  
- A sudden flood of unwanted traffic towards device control planes (for example DoS attempts).  
- New services introduced without corresponding updates to iACL/CoPP policies.

For each scenario, describe:

- Impact on device stability and network operations.  
- How you would detect the issue (logs, monitoring, user reports).  
- What adjustments or safeguards you would implement to prevent or mitigate it.

### Expected Outcomes

After completing this project you should be able to:

- Present a clear infrastructure ACL and CoPP strategy that protects network devices.  
- Explain how it integrates with your existing AAA, segmentation, and firewall designs.  
- Provide guidance for operations on safely deploying and maintaining these protections.

### Reflection

Reflect on:

- How much complexity is appropriate in your iACL and CoPP designs for your environment.  
- Which parts of the policy are most important to document and review regularly.  
- How you will educate other engineers about the intent and safe handling of these controls.


