## CCNA in 90 Days – Project Labs

This repository contains a **50‑lab CCNA practice curriculum** structured to take learners from foundational CLI skills through switching, routing/WAN, security/monitoring, and into advanced design and light automation concepts.  
Each lab is documentation‑driven (no full configs), with a strong focus on **realistic business scenarios**, **Cisco‑aligned designs**, and **professional engineering deliverables**.

The labs are organised into five phases:

- [`01-foundations`](./01-foundations/)
- [`02-switching`](./02-switching/)
- [`03-routing-wan`](./03-routing-wan/)
- [`04-security-optimization`](./04-security-optimization/)
- [`05-advanced-design`](./05-advanced-design/)

Use this README as your top‑level guide to navigate the curriculum.

---

## Master Addressing and VLAN Blueprint

All labs follow a consistent **master blueprint** so that skills are transferable across scenarios:

- **Small networks (per‑VLAN subnets)**: `192.168.X.0/24`
- **Enterprise LAN (site subnets)**: `10.X.0.0/24`
- **WAN point‑to‑point links**: `10.255.X.0/30`
- **VLAN IDs**
  - 10 – Users
  - 20 – Voice
  - 30 – Servers
  - 40 – Guest
  - 50 – IoT
  - 99 – Management
- **ISP simulation ranges**
  - `203.0.113.0/24`
  - `198.51.100.0/24`

Each lab’s `addressing-plan.md` and `README.md` apply this blueprint to a specific scenario.

---

## Phase Overview and Directory Links

### 01 – Foundations (`01-foundations/`, labs 01–10)

- **Directory**: [`01-foundations`](./01-foundations/)
- **Focus**:
  - Basic CLI navigation and device hardening.
  - IPv4 addressing and subnet allocation using `192.168.X.0/24`.
  - Single‑site VLANs (10, 20, 99) and default gateways.
  - Simple inter‑VLAN routing and default routes to an ISP cloud.
- **Use case examples**:
  - Small IT consulting office.
  - Single‑switch small business LAN with management VLAN.
- **Deliverables per lab**:
  - `README.md` – scenario, architecture overview, technical requirements, implementation checklist, IP table, verification, failure testing, expected outcomes, reflection.
  - `addressing-plan.md` – VLAN/subnet allocations, gateway strategy.
  - `topology-description.md` – device roles, link types, VLAN layout.
  - `expected-outcomes.md` – learning outcomes and success criteria.
  - `failure-testing.md` – planned misconfigurations and recovery steps.

Suggested progression: complete labs **01–10** sequentially to solidify CLI comfort, base IP addressing, and VLAN fundamentals before moving on.

---

### 02 – Switching and Redundancy (`02-switching/`, labs 11–20)

- **Directory**: [`02-switching`](./02-switching/)
- **Focus**:
  - Multi‑switch campus designs with access + distribution layers.
  - VLANs 10/20/30/40/99 spanning multiple switches.
  - 802.1Q trunks, STP root selection, and redundant uplinks.
  - (Optionally) EtherChannel concepts and basic tuning.
- **Use case examples**:
  - Two‑floor office or small campus with redundant access to a distribution switch.
- **Deliverables per lab**:
  - Same document set as foundations, with additional emphasis on:
    - Spanning‑tree behaviour.
    - Link‑failure handling at Layer 2.

Suggested progression: labs **11–20** build switching depth; pay attention to how STP and trunk design are documented and verified.

---

### 03 – Routing and WAN (`03-routing-wan/`, labs 21–35)

- **Directory**: [`03-routing-wan`](./03-routing-wan/)
- **Focus**:
  - Inter‑VLAN routing at HQ and branch sites.
  - WAN point‑to‑point links using `10.255.X.0/30`.
  - Static routes, default routes, and later simple dynamic routing (for example, OSPF single area).
  - **Labs 30–35**: upper‑bound CCNA routing, dual‑site routing with convergence analysis between HQ, branch, and ISP.
- **Use case examples**:
  - Single HQ with ISP edge.
  - HQ–branch topologies with dynamic routing and shared ISP access.
- **Enhanced content (labs 30–35)**:
  - **Convergence analysis** sections:
    - Measure/describe behaviour during WAN or ISP failures.
    - Compare static‑only vs static + dynamic routing.
  - **Routing design diagrams (textual)**:
    - Clear device‑to‑subnet and link representation (SVIs, WAN /30s, ISP loopbacks).
  - **Troubleshooting challenges**:
    - Branch reaches HQ but not ISP.
    - Asymmetric routing and post‑failure instability.
  - **Operational documentation requirements**:
    - Runbook‑style notes on routing, change/rollback, and monitoring.

Suggested progression: labs **21–29** introduce routing and WAN; labs **30–35** push you into convergence‑oriented, exam‑upper‑bound thinking.

---

### 04 – Security and Optimisation (`04-security-optimization/`, labs 36–45)

- **Directory**: [`04-security-optimization`](./04-security-optimization/)
- **Focus**:
  - IPv4 ACL design and placement.
  - Management‑plane security (SSH, VTY, management VLAN 99).
  - Logging to syslog, basic monitoring, and incident‑response thinking.
  - Segmentation of users, voice, servers, guest, and management.
- **Use case examples**:
  - Secured branch office with WAN back to HQ and internet via HQ.
  - Branch servers (including syslog/monitoring) in dedicated VLANs.
- **Enhanced content (labs 36–45)**:
  - **Convergence and security event analysis**:
    - Impact of ACL updates and WAN flaps.
    - Log visibility for failed logins, ACL denies, and interface events.
  - **Routing + security design diagrams (textual)**:
    - Branch VLANs 10/20/30/40/99, branch–HQ /30s, ISP simulation ranges.
  - **Troubleshooting challenge scenarios**:
    - Guest VLAN reaching internal servers.
    - Syslog message loss.
    - Intermittent SSH issues from management networks.
  - **Operational documentation requirements**:
    - Branch security policy summaries.
    - ACL inventories at a descriptive (not config) level.
    - Logging/monitoring plan and incident‑response checklists.

Suggested progression: labs **36–45** move beyond “feature configuration” into **security operations** and **runbook‑style documentation**.

---

### 05 – Advanced Design and Automation (`05-advanced-design/`, labs 46–50)

- **Directory**: [`05-advanced-design`](./05-advanced-design/)
- **Focus**:
  - Multi‑site enterprise design using `10.X.0.0/24` LANs and `10.255.X.0/30` WAN links.
  - Summarisation, default route origination, and failover behaviour across HQ and branches.
  - Template‑driven design suitable for tools such as Ansible or Python scripts (conceptually; no code required).
- **Use case examples**:
  - HQ with multiple large and small branches and dual ISPs.
  - Gradual migration from ad‑hoc configs to templated, standardised builds.
- **Enhanced content (labs 46–50)**:
  - **Convergence planning**:
    - Expected routing/failover behaviour for branch WAN loss and ISP failover.
    - Design‑time reasoning about timers and failure domains.
  - **Routing design diagrams (textual)**:
    - HQ core, WAN edges, branches, ISP1 `203.0.113.0/24`, ISP2 `198.51.100.0/24`.
  - **Troubleshooting challenge scenarios**:
    - Template changes breaking internet but not site‑to‑site reachability.
    - Slow failover to backup ISP.
    - Overlapping subnets between lab and production spaces.
  - **Operational documentation requirements**:
    - Site catalogue, routing/failover behaviour, template ownership and change control, monitoring/alerting expectations.

Suggested progression: labs **46–50** are design‑heavy and intended to stretch you to the **upper limit of CCNA** design and operations expectations, while setting you up for more advanced studies.

---

### Advanced Projects – Advanced Scenario Labs

- **Directory**: [`advanced-projects`](./advanced-projects/)
- **Focus**:
  - 50 optional project style labs that revisit core enterprise topics (architecture, virtualization, infrastructure, network assurance, security, and automation).
  - Larger, real life scenarios that expect you to design, plan, and troubleshoot at an advanced level rather than follow short, guided steps.
- **Use case examples**:
  - Multi site campus and WAN designs.
  - VRF and tunneling projects for multi tenant environments.
  - End to end infrastructure and assurance exercises that combine routing, wireless, and IP services.
  - Security hardening and automation initiatives that feel close to real enterprise work.

You can work through these projects after the main 50 CCNA labs when you are ready for deeper design and troubleshooting practice.

---

## How to Use This Repository

- **For self‑study**
  - Work labs in numerical order for a 50‑day or “CCNA in 90 days” path.
  - For each lab:
    - Read `README.md` to understand the scenario and requirements.
    - Use `addressing-plan.md` and `topology-description.md` to build the topology in your chosen simulator.
    - Implement and then verify using the **Verification** and **Failure testing** sections.
    - Capture notes in the **Reflection** section (as if you were writing to a senior engineer).

- **For instructors / academies**
  - Treat each lab folder as a **lesson module**:
    - `README.md` → instructor guide and student brief.
    - `addressing-plan.md` → master answer key for addressing.
    - `topology-description.md` → basis for official diagrams.
    - `failure-testing.md` → structured break/fix exercises.
  - Sequencing is already aligned to CCNA exam domains and increasing complexity.

- **For revision**
  - Re‑use later‑phase labs (30–50) as **capstone scenarios** to test convergence reasoning, troubleshooting discipline, and documentation skills.

---

## Next Steps

- Start in [`01-foundations`](./01-foundations/) and progress forward, or jump directly to a phase that matches your current level.
- As you complete labs, consider maintaining your own notes or a separate branch with your device configurations and additional commentary.

This structure is intentionally designed to mirror a **professional network engineering academy**: every lab expects not just CLI work, but also **clear documentation, verification, failure testing, and reflection**. 



