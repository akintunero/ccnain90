## Failure Testing – Lab 11 Switching and Redundancy

### Test 1 – Uplink Failure
- **Action**
  - Shut down one trunk uplink from ASW1 to DSW1.
- **Expected impact**
  - Traffic from ASW1 should seamlessly transition to the remaining uplink.
  - End-user connectivity should experience minimal interruption.
- **Verification**
  - `show interfaces trunk` and `show spanning-tree` on ASW1 and DSW1.
  - End-to-end `ping` between hosts attached to ASW1 and ASW2.
- **Recovery**
  - Re-enable the uplink and confirm that STP reconverges as expected.

### Test 2 – STP Root Misplacement
- **Action**
  - Change STP priority on an access switch so that it becomes root for VLAN 10.
- **Expected impact**
  - STP topology changes; certain uplinks may now be blocking or forwarding differently.
  - Traffic paths may become suboptimal and, in some misconfigurations, cause instability.
- **Verification**
  - `show spanning-tree vlan 10` on all switches.
  - Note root bridge ID, root ports, and blocked ports.
- **Recovery**
  - Restore the original STP priority on DSW1 so it is again the root.

### Test 3 – Trunk Misconfiguration
- **Action**
  - On one uplink, remove VLAN 20 (voice) from the allowed VLAN list.
- **Expected impact**
  - Voice endpoints on that access switch lose connectivity to voice services.
  - Data VLAN users remain unaffected.
- **Verification**
  - `show interfaces trunk` to confirm allowed VLANs.
  - `ping` and, if available, test calls from IP phones across the campus.
- **Recovery**
  - Re-add VLAN 20 to the trunk allowed list and verify restoration of service.

### Documentation
For each failure:
- Capture key `show` and `ping` outputs.
- Describe the user-visible symptoms and the underlying technical cause.
- Document the corrective change and any design recommendations to prevent similar issues (for example, standard trunk templates).

