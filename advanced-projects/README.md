## CCNA Advanced Projects – ENCOR 350-401 Scenario Labs

The `advanced-projects` area extends the CCNA lab journey with **real world, ENCOR 350-401 aligned projects**.  
These labs are designed as larger, scenario based exercises that map to the Implementing Cisco Enterprise Network Core Technologies blueprint, including dual stack architecture, virtualization, infrastructure, network assurance, security, and automation.

Each project assumes you already know the core CLI and concepts from the main `ccnain90` labs and now want to practice **design, implementation planning, and troubleshooting** at a more advanced, CCNP style level.

### ENCOR Domains and Folders

1. **Architecture**  
   - Dual stack (IPv4 and IPv6) enterprise design  
   - High availability, QoS, SD-WAN and SD-Access fundamentals  
   - Folder: [`01-architecture`](./01-architecture/)
2. **Virtualization**  
   - Device and data path virtualization, VRF, tunneling, overlay concepts  
   - Folder: [`02-virtualization`](./02-virtualization/)
3. **Infrastructure**  
   - Layer 2 and Layer 3 services, wireless, and IP services  
   - Folder: [`03-infrastructure`](./03-infrastructure/)
4. **Network Assurance**  
   - Monitoring, telemetry, and assurance workflows  
   - Folder: [`04-network-assurance`](./04-network-assurance/)
5. **Security**  
   - Infrastructure protection, access control, and secure design  
   - Folder: [`05-security`](./05-security/)
6. **Automation**  
   - Python, APIs, data models, and basic orchestration concepts  
   - Folder: [`06-automation`](./06-automation/)

There are **50 advanced labs** in total:

- Labs **01 to 08** – Architecture  
- Labs **09 to 13** – Virtualization  
- Labs **14 to 28** – Infrastructure  
- Labs **29 to 33** – Network Assurance  
- Labs **34 to 43** – Security  
- Labs **44 to 50** – Automation

---

## Lab Structure (Per Advanced Project)

Each advanced project lives in a folder such as:

- `01-architecture/lab-01/`
- `03-infrastructure/lab-20/`
- `06-automation/lab-50/`

Inside each `lab-XX` folder you will find a `README.md` that follows this structure:

- **Scenario**  
  Realistic business and technical story that sets the context, constraints, and success criteria for the project.
- **Network Architecture Overview**  
  High level description of the target design, including roles such as core, distribution, access, WAN edge, and any wireless or SD-WAN/SD-Access components when relevant.
- **Technical Requirements**  
  Concrete requirements that come from the scenario and the ENCOR blueprint topics (for example high availability techniques, QoS policy, routing protocols, virtualization boundaries, or automation interfaces).
- **Implementation Checklist**  
  Ordered list of tasks an engineer would perform to realise the design. You can treat this as a project plan or as a guide for building the topology in your preferred lab environment.
- **Routing or Switching Design Diagram (Text Form)**  
  Text based description of the topology that you can easily translate into a drawing or into a network simulator.
- **Verification and Assurance Commands**  
  Key commands or checks to validate that the design and configuration behave as expected.
- **Failure Testing**  
  Planned failures or misconfigurations you should introduce on purpose and then recover from to confirm resilience and observability.
- **Expected Outcomes and Reflection**  
  What you should be able to explain and demonstrate at the end of the project, plus reflection prompts about design trade-offs.

These projects are **not** about memorising the exam blueprint. They are here to give you **real life style scenarios** that connect the blueprint topics to day to day enterprise work.

---

## How the Projects Map to the ENCOR Blueprint

The projects draw directly from the official ENCOR 350-401 topic areas, for example:

- **Architecture (labs 01 to 08)**  
  - Tiered and fabric based enterprise campus designs  
  - High availability with redundancy, FHRP, and SSO  
  - On premises versus cloud deployments  
  - SD-WAN and SD-Access control and data plane building blocks  
  - QoS components and policy concepts across wired and wireless

- **Virtualization (labs 09 to 13)**  
  - Device virtualization (hypervisors, virtual machines, virtual switching)  
  - VRF based data path segmentation  
  - GRE and IPsec tunneling for overlay transport  
  - Overlay concepts such as LISP or VXLAN

- **Infrastructure (labs 14 to 28)**  
  - Layer 2 design, trunks, EtherChannel, and spanning tree  
  - Layer 3 design with OSPF, EIGRP concepts, and simple eBGP between neighbors  
  - Wireless deployment models, AP modes, roaming, and client troubleshooting  
  - IP services such as NTP, NAT/PAT, first hop redundancy, and multicast

- **Network Assurance (labs 29 to 33)**  
  - Using debugs, trace route, ping, SNMP, and syslog to diagnose issues  
  - Syslog based device monitoring and remote logging  
  - NetFlow and Flexible NetFlow use cases  
  - SPAN, RSPAN, ERSPAN, and IPSLA  
  - Cisco DNA Center style workflows for configuration and monitoring  
  - NETCONF and RESTCONF based monitoring or changes

- **Security (labs 34 to 43)**  
  - Secure device access, lines, and AAA based authentication and authorization  
  - Infrastructure protection with ACLs and control plane policing  
  - REST API security at a high level  
  - Wireless security profiles such as EAP, WebAuth, and PSK  
  - Threat defense, endpoint security, next generation firewalls, TrustSec and MACsec  
  - Network access control using 802.1X, MAB, and WebAuth

- **Automation (labs 44 to 50)**  
  - Interpreting basic Python scripts used for network tasks  
  - Working with JSON structures and YANG style data modelling concepts  
  - Exploring APIs for Cisco DNA Center and vManage  
  - Reading REST API codes and results from DNA Center or RESTCONF  
  - Using EEM applets for small automation tasks  
  - Comparing agent based and agentless orchestration tools

Each lab focuses on a realistic enterprise situation where these topics matter and asks you to design, implement in a lab tool, verify, and then deliberately break and fix parts of the solution.

---

## How to Use the Advanced Projects

You can approach these projects in several ways:

- **As a CCNP ENCOR study track**  
  - Pick one or two labs from each domain to match where you are in your reading or video course.  
  - Use the scenarios as prompts to build or extend your own Packet Tracer, CML, GNS3, or physical lab.

- **As capstones after the core CCNA in 90 labs**  
  - When you finish the main `ccnain90` lab path, come here to test your design and troubleshooting skills with more open ended, multi step work.

- **As practice for design and troubleshooting interviews**  
  - Use the scenarios to practise talking through designs, trade-offs, and failure handling with a study partner or mentor.

Remember that there is no single right answer for many of these projects. The goal is to think and work like an enterprise network engineer while staying grounded in the ENCOR exam topics.

