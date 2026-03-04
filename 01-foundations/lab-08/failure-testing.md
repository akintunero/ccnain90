## Failure Testing – Lab 01 Foundations

This lab introduces structured failure testing so that learners build troubleshooting discipline from the beginning.

### Test 1 – VLAN Misassignment
- **Action**
  - Move one user port from VLAN 10 to an incorrect VLAN (for example, VLAN 30 if configured, or an unused VLAN).
- **Expected impact**
  - The affected host loses connectivity to its default gateway and other VLAN 10 hosts.
- **Verification**
  - `show vlan brief` and `show interfaces switchport` on the access switch.
  - `ping` from the affected host to `192.168.10.1` and to a working host in VLAN 10.
- **Recovery**
  - Return the access port to VLAN 10 and confirm connectivity is restored.

### Test 2 – Default Gateway Outage
- **Action**
  - Administratively shut down the Layer 3 interface providing `192.168.10.1`.
- **Expected impact**
  - Hosts in VLAN 10 cannot reach other VLANs or the simulated ISP network.
  - Local link-layer connectivity (within VLAN 10) should remain intact.
- **Verification**
  - `show ip interface brief` and `show ip route` on the router or multilayer switch.
  - `ping` between VLAN 10 hosts (should succeed) and from VLAN 10 hosts to the ISP network (should fail).
- **Recovery**
  - Re-enable the gateway interface and confirm normal operation resumes.

### Test 3 – Default Route Removal
- **Action**
  - Remove or disable the static default route towards the ISP simulation.
- **Expected impact**
  - Inter-VLAN routing remains functional.
  - Connectivity to `203.0.113.0/24` (and any other external prefixes) is lost.
- **Verification**
  - `show ip route` to confirm that the default route is absent.
  - `ping` from user VLAN hosts to `203.0.113.10` before and after removal.
- **Recovery**
  - Reconfigure the default route and verify successful pings to the ISP simulation network.

### Documentation
For each failure test:
- Capture key command outputs before, during, and after the fault.
- Note symptoms observed from the end-user perspective.
- Summarise root cause, detection method, and corrective action taken.

This failure analysis documentation becomes a reusable troubleshooting playbook for later, more complex labs.

