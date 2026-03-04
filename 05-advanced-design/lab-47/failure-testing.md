## Failure Testing – Lab 46 Advanced Design and Automation

Because this is a design and documentation lab, failure testing is primarily conceptual. You will identify and reason about potential failure modes in a multi-site, template-driven deployment.

### Scenario 1 – Overlapping Subnets Between Sites
- **Risk**
  - Two sites are accidentally assigned overlapping `10.X.0.0/24` ranges.
- **Impact**
  - Routing loops, blackholes, or unpredictable traffic forwarding.
- **Mitigation**
  - Strong IP address management (IPAM) practices.
  - Automated validation checks on addressing data before template rendering.

### Scenario 2 – Incorrect WAN /30 Assignment
- **Risk**
  - A WAN point-to-point link is configured with mismatched /30 subnets at each end.
- **Impact**
  - WAN adjacency and routing fail for the affected site.
- **Mitigation**
  - Template-driven interface definitions tied to structured WAN link data.
  - Automated pre-deployment linting to detect inconsistent addressing.

### Scenario 3 – Template Error Propagation
- **Risk**
  - An error in a shared template pushes an incorrect VLAN or IP configuration to dozens of devices.
- **Impact**
  - Widespread outages or security policy violations.
- **Mitigation**
  - Use dry-run and staged deployments (for example, deploy to a single test site first).
  - Implement configuration backups and rapid rollback procedures.

Document for each scenario:
- How it might manifest in `show` command outputs and monitoring tools.
- Which safeguards (process and technical) you would put in place.

