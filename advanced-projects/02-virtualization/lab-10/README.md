## Advanced Virtualization Lab 10 – Multi-Tenant VRF and Secure Tunneling Design

### Scenario
Your data centre team has begun virtualising firewalls and routers on hypervisors, but there is no consistent plan for how these virtual devices plug into the VRF and tunnelling design. Some workloads are still on physical appliances, others on virtual machines, and connectivity is fragile.

In this lab you emphasise how hypervisors, virtual switches, and virtual firewalls fit into the multi-tenant VRF design so that physical and virtual network functions can coexist without breaking separation between business units.

### Project Objectives

By the end of this project you should be able to:

- Propose a VRF layout for multiple tenants or business units.  
- Show how GRE or IPsec tunnels will carry traffic for each VRF between sites.  
- Explain how this design could evolve into an overlay based solution later.  
- Identify where virtual switching and virtual machines fit into the design, if needed.

### Technologies and Design Topics in Scope

This project draws from the Virtualization section:

- **2.1 Device virtualization technologies**
  - 2.1.a Hypervisor type 1 and type 2.
  - 2.1.b Virtual machines and their lifecycle.
  - 2.1.c Virtual switching in virtualised environments.
- **2.2 Data path virtualization technologies**
  - 2.2.a VRF-based segmentation for multi-tenant or multi-business-unit designs.
  - 2.2.b GRE and IPsec tunnelling to carry virtualised paths over untrusted networks.
- **2.3 Network virtualization concepts**
  - 2.3.a LISP as an example of separating identity from location.
  - 2.3.b VXLAN as an overlay to extend Layer 2 segments over a Layer 3 underlay.

### Project Tasks

1. **Identify tenants and traffic types**
   - List the business units or tenants that require separation.  
   - Identify shared services (for example internet, DNS, identity) that may be common across VRFs.
2. **Design the VRF layout**
   - Decide which VRFs are needed (for example TenantA, TenantB, Shared-Services).  
   - Define which VLANs or subnets will live in each VRF at HQ and at remote sites.
3. **Plan GRE or IPsec tunnels**
   - Decide whether you will use GRE, IPsec, or a combination (for example GRE over IPsec).  
   - Show how each VRF will reach its remote counterparts using those tunnels.  
   - Document which routers terminate tunnels and which ones simply route between VRFs and tunnels.
4. **Consider device and virtual switching**
   - Decide where hypervisors or virtual switches might be used (for example to host virtual firewalls or routers per tenant).  
   - Explain how virtual switches connect into the physical VRF design.
5. **Outline an overlay ready design**
   - Describe how LISP or VXLAN could later replace or complement GRE/IPsec without changing every endpoint.  
   - Identify which parts of your design would remain the same and which would change.

### Design Diagram (Text Form)

Use this description to build a diagram:

- **HQ Site**
  - Core routers or distribution switches with multiple VRFs.  
  - Interfaces or SVIs mapped to VRFs for each tenant.  
  - One or more edge routers that terminate GRE or IPsec tunnels to remote sites.
- **Remote Sites**
  - Smaller routers with a subset of VRFs that match HQ.  
  - Tunnel interfaces connected back to HQ edge routers.  
  - Local user or server VLANs mapped into the appropriate VRFs.
- **Overlay Ready Layer**
  - A note showing where a VXLAN or LISP control plane could be added later to virtualize addressing while reusing the same physical underlay.

### Failure and What-If Analysis

Consider the impact of the following events on each tenant:

- Loss of a single tunnel between one remote site and HQ.  
- Loss of a single HQ edge router that terminates multiple tunnels.  
- Misconfiguration of a VRF import or export target, causing route leaks between tenants.

For each case, write down:

- Which traffic stops working.  
- Which VRFs remain unaffected.  
- How you would detect the problem and which design choices help limit impact.

### Expected Outcomes

When you complete this lab you should be able to:

- Draw and explain a VRF based design that separates multiple business units.  
- Show how GRE or IPsec tunnels provide connectivity between sites for each VRF.  
- Discuss how overlay technologies could later simplify or extend the design.

### Reflection

Reflect on:

- How many VRFs you chose and why.  
- How your design balances simplicity and isolation.  
- How much effort would be required to migrate this design to a full SD-WAN or VXLAN based solution in the future.

