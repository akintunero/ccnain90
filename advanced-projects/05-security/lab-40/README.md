## Advanced Security Lab 40 – Evaluating TrustSec and MACsec in Your Design

### Scenario
Your security architecture already includes segmentation (VLANs, ACLs, and possibly SGTs), but leadership is evaluating technologies like **Cisco TrustSec** and **MACsec** to strengthen security further:

- Some high-value links between core, distribution, and datacentre devices are not encrypted.  
- Policy is still largely tied to IP addresses and VLANs rather than to user or device identity.  
- There is interest in more dynamic, identity-based policy enforcement, but concerns about complexity.

In this lab you will assess where TrustSec and MACsec could realistically fit into your environment and what benefits they would provide relative to their cost and complexity.

### Project Objectives

By the end of this project you should be able to:

- Explain the roles of TrustSec and MACsec in a modern enterprise network.  
- Identify specific links or segments where MACsec would add meaningful protection.  
- Propose how identity or tag-based policies (for example SGTs) could complement existing VLAN/ACL models.  
- Provide a reasoned recommendation on whether and where to adopt these technologies.

### Technologies and Topics in Scope

This project draws from the Security section:

- **5.4 Components of network security design**
  - 5.4.d TrustSec and MACsec.  
- **5.2 Infrastructure security features**
  - How these technologies interact with existing ACLs and segmentation.

### Project Tasks

1. **Review current segmentation and link protection**
   - Describe your existing segmentation model (VLANs, ACLs, possibly VRFs or SGTs).  
   - Identify critical links (for example core-to-datacentre, core-to-branch) where data sensitivity or regulatory requirements may demand encryption.  
   - Note where identity information (user, device type) is already available via AAA or other sources.
2. **Evaluate potential MACsec deployment**
   - Determine which devices and links support MACsec in your environment or planned hardware.  
   - Decide where link-layer encryption would add value (for example inter-switch trunks carrying sensitive data).  
   - Consider operational implications: key management, performance impact, and troubleshooting.
3. **Evaluate potential TrustSec (or SGT-based) deployment**
   - Describe how security group tags (SGTs) or similar concepts could be used to express policy by role rather than IP.  
   - Propose simple examples (for example “Finance”, “Guest”, “IoT”) and how policies between them would look.  
   - Identify which infrastructure components (switches, controllers, firewalls) would participate in tag-based enforcement.
4. **Assess integration with existing controls**
   - Explain how TrustSec or MACsec would coexist with your current ACLs, firewalls, and access control methods.  
   - Identify any overlaps or conflicts, and how you would avoid double-enforcing or missing policies.  
   - Consider migration strategies from purely IP-based policies to identity/tag-based ones.
5. **Formulate a recommendation and roadmap**
   - Summarise where TrustSec and MACsec provide clear benefits and where they might be overkill.  
   - Propose a small pilot or proof-of-concept scope if adoption seems worthwhile.  
   - Outline prerequisites (hardware, software, PKI, skill sets) and risks to consider.

### Design Diagram (Text Form)

At a high level, describe:

- Links where MACsec would be enabled (for example between specific core and distribution switches).  
- Areas where TrustSec/SGT-based policy would apply (for example campus access and core, datacentre edge).  
- How tags or identities would flow from access devices through the network to enforcement points.

Use this as the basis for a diagram that shows where and how these technologies would be layered onto your existing design.

### Failure and What-If Analysis

Consider:

- MACsec key negotiation failures on critical inter-switch links.  
- Misconfigured or conflicting TrustSec policies that block legitimate traffic.  
- Partial deployment where some devices understand tags and others do not.  
- A need to quickly disable TrustSec or MACsec during an incident or migration.

For each, describe:

- Impact on connectivity and security.  
- How you would detect and diagnose the issue.  
- What safeguards or rollback mechanisms you would plan in advance.

### Expected Outcomes

After completing this project you should be able to:

- Clearly articulate where TrustSec and MACsec fit (or do not fit) in your environment.  
- Provide leadership with a balanced view of benefits, costs, and complexity.  
- Suggest concrete next steps if these technologies are to be piloted or adopted more widely.

### Reflection

Reflect on:

- Whether your organisation is ready, from both a skills and process perspective, to adopt these advanced features.  
- How TrustSec and MACsec complement or overlap with other security initiatives such as zero trust.  
- What additional learning or lab work you would pursue before recommending production deployment.


