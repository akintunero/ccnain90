## Lab 38 – Segmenting Servers, Users, and Guests

### Scenario – Improving Internal Segmentation
Internal movement between user, server, and guest networks is too permissive. Your task is to define ACLs and simple controls that enforce least privilege between VLANs without breaking normal business flows.

### Network Architecture Overview
- **Topology type**: Branch office with a routed WAN connection to HQ and upstream internet via HQ.
- **Key components**:
  - Branch edge router providing routing, ACL enforcement, and logging.
  - Branch access switch and VLANs for users, voice, servers, guest, and management.
  - WAN link to HQ using `10.255.X.0/30`.
- **Security focus**:
  - Filtering traffic with ACLs at the branch and optionally at HQ.
  - Protecting management access from untrusted VLANs and the internet.
  - Enabling logging and monitoring for key events, including ACL hits and login attempts.

### Technical Requirements
- **Addressing**
  - Reuse the `192.168.X.0/24` small-network blueprint for branch VLANs (10, 20, 30, 40, 99).
  - Use a WAN /30 from the `10.255.X.0/30` blueprint between branch and HQ.
- **Security controls**
  - Implement IPv4 ACLs on the branch router to:
    - Permit essential business traffic towards HQ and the internet.
    - Restrict guest and IoT traffic from reaching sensitive resources.
    - Protect management interfaces so that only VLAN 99 and authorised HQ subnets can access them.
  - Harden device access (SSH only, secure passwords, login banners, idle timeouts).
- **Monitoring**
  - Configure logging towards a central syslog server (for example, in `192.168.30.0/24` servers VLAN).
  - Enable basic SNMP or equivalent visibility if supported in your lab environment.
  - Tune logging severity so that security events are captured without overwhelming operators.

### Implementation Checklist
- **Access control**
  - Define standard and extended ACLs for:
    - User access to HQ applications and selected internet destinations.
    - Guest internet access with limited reachability and no access to internal VLANs.
    - Management traffic from VLAN 99 and HQ management ranges.
  - Apply ACLs in the correct direction and on appropriate interfaces (WAN-facing and LAN-facing).
- **Management-plane security**
  - Restrict management access to VLAN 99 addresses and authorised HQ subnets only.
  - Use SSH for remote management; disable unused or insecure services (for example, Telnet, HTTP).
  - Configure role-appropriate user accounts and secure line settings.
- **Logging and monitoring**
  - Configure syslog server IP in the servers VLAN.
  - Set an appropriate logging level for security-relevant events.
  - Enable logging for ACL matches where appropriate to support incident triage.

### Convergence and Security Event Analysis
- Observe and document how quickly the network reacts when:
  - ACLs are updated to block or permit specific flows.
  - The branch–HQ WAN link flaps or fails and then returns.
- Track log messages for:
  - Repeated failed login attempts.
  - ACL denies from guest or untrusted VLANs.
  - Interface up/down events on the WAN link.
- Summarise the impact of these changes on user traffic and how operators would recognise and respond to them at a CCNA level.

### IP Addressing Table (Aligned to Master Blueprint)

| Segment      | Purpose                 | Subnet              | Example IPs                      |
|-------------|-------------------------|---------------------|----------------------------------|
| VLAN 10     | Branch users            | 192.168.10.0/24     | 192.168.10.1 (GW), .50–.150      |
| VLAN 20     | Branch voice            | 192.168.20.0/24     | 192.168.20.1 (GW)                |
| VLAN 30     | Branch servers/syslog   | 192.168.30.0/24     | 192.168.30.10 (syslog), .11–.20  |
| VLAN 40     | Branch guest            | 192.168.40.0/24     | 192.168.40.1 (GW)                |
| VLAN 99     | Branch management       | 192.168.99.0/24     | 192.168.99.21 (router), .22–.30  |
| WAN P2P     | Branch–HQ link          | 10.255.36.0/30      | 10.255.36.1 (branch), .2 (HQ)    |

### Verification Commands
- **ACL and interface checks**
  - `show access-lists`
  - `show ip interface` and `show run interface` to confirm ACL application.
- **Security and management**
  - `show running-config | include line vty`
  - `show logging`
  - `show users` and related commands for active sessions.
- **End-to-end tests**
  - `ping` and application tests from branch VLANs to HQ and beyond.
  - Confirm that guest VLAN 40 cannot access internal VLANs but can reach appropriate external destinations via HQ.

### Routing and Security Design Diagram (Textual)

Use the following text-based diagram as a reference:

- **Branch LAN**
  - `BR-SW1`
    - VLAN 10 – Users (`192.168.10.0/24`).
    - VLAN 20 – Voice (`192.168.20.0/24`).
    - VLAN 30 – Servers/syslog (`192.168.30.0/24`).
    - VLAN 40 – Guest (`192.168.40.0/24`).
    - VLAN 99 – Management (`192.168.99.0/24`).
  - `BR-R1`
    - LAN-facing subinterfaces or SVIs for VLANs above.
    - WAN interface to HQ – `10.255.36.1/30`.
- **HQ / Upstream**
  - `HQ-R1` – WAN interface `10.255.36.2/30` toward branch; default route toward ISP.
  - `ISP-R1` – upstream network `203.0.113.0/24` and/or `198.51.100.0/24`.

ACLs are primarily enforced on `BR-R1` at the branch edge, with optional additional filtering at HQ.

### Failure Testing Requirements
- Intentionally over-restrict an ACL to block legitimate user traffic (for example, users in VLAN 10 accessing HQ apps) and observe the impact.
- Remove ACL protection from a management interface and explore potential exposure (conceptually) from guest and user VLANs.
- Disable logging or misconfigure the syslog destination and discuss how this affects incident response and troubleshooting.
- Simulate repeated failed login attempts from an untrusted VLAN and verify that they are visible in logs and can be correlated to a source IP.

Document detailed test cases in the `failure-testing.md` file, including both security impact and operational detection.

### Troubleshooting Challenge Scenarios

1. **Guest VLAN can reach internal servers**
   - Identify which ACL or interface is misconfigured.
   - Propose and document a least-privilege correction.
2. **Syslog messages stop arriving at the server**
   - Determine whether the issue is on the network, device configuration, or the server.
   - Use `show logging` and connectivity tests from the router to the syslog host.
3. **Intermittent SSH failures from management VLAN**
   - Evaluate potential causes (for example, ACL hit counts, CPU utilisation due to excessive logging, line configuration limits).

For each challenge, record:
- Observed symptoms.
- Commands used to isolate the fault.
- Final resolution and any long-term hardening recommendations.

### Operational Documentation Requirements

Produce operational documentation suitable for a branch runbook, including:

- **Security policy summary** for the branch (what each VLAN is allowed to reach).
- **ACL inventory** with high-level descriptions (do not list full configs).
- **Logging and monitoring plan**, including log retention expectations and who reviews logs.
- **Incident response checklist** for:
  - Suspected compromised host on the user or guest VLAN.
  - Detected unauthorised management access attempts.

This documentation should be concise enough for an on-call CCNA-level engineer to follow during an incident.

### Expected Outcomes
- Only authorised traffic flows between branch, HQ, and external networks in line with business policy.
- Management access is limited to dedicated management subnets and authorised HQ ranges.
- Security events and key operational changes are visible in the logging and monitoring system.
- Learners can reason about the security impact of misconfigurations and respond using structured troubleshooting and documentation practices.

### Reflection
Reflect on:

- **Policy translation**: How did you convert business requirements into specific ACL statements and logging policies?
- **Balance between security and usability**: What trade-offs did you observe when tuning ACLs and logging levels?
- **Operational readiness**: How confident would you be handing this branch over to an operations team with only your runbook?

Capture these reflections to inform more advanced security, optimisation, and incident-response labs.

