## Failure Testing – Lab 21 Routing and WAN Edge

### Test 1 – Default Route Removed
- **Action**
  - Remove the default route from HQ-R1 (`ip route 0.0.0.0 0.0.0.0 10.255.21.2`).
- **Expected impact**
  - Inter-VLAN connectivity inside HQ continues to function.
  - Connectivity from HQ VLANs to the ISP network (`203.0.113.0/24`) fails.
- **Verification**
  - `show ip route` on HQ-R1 to confirm absence of the default route.
  - `ping` and `traceroute` from a VLAN 10 host to `203.0.113.10`.
- **Recovery**
  - Re-add the default route and confirm external reachability is restored.

### Test 2 – WAN Link Failure
- **Action**
  - Shut the HQ-R1 interface facing ISP-R1.
- **Expected impact**
  - HQ has no path to the ISP network.
  - LAN routing and management remain unaffected.
- **Verification**
  - `show ip interface brief` on both HQ-R1 and ISP-R1.
  - `ping` from HQ hosts to the ISP test host before and after the shutdown.
- **Recovery**
  - Re-enable the interface and ensure the link returns to an up/up state.

### Test 3 – Subnet Mask Misconfiguration
- **Action**
  - Intentionally configure an incorrect mask on one SVI (for example, use `/25` instead of `/24` on VLAN 10).
- **Expected impact**
  - Some hosts may communicate while others cannot reach certain destinations depending on their IP assignments.
- **Verification**
  - `show ip interface brief` and `show running-config | section interface` on the routing device.
  - `ping` between hosts at different ends of the `192.168.10.0/24` range.
- **Recovery**
  - Correct the subnet mask and re-verify connectivity.

### Documentation
For each failure scenario:
- Capture CLI evidence (key show commands and pings).
- Describe the observed symptoms and underlying root cause.
- Record corrective steps and lessons learned to support later multi-site and dynamic routing labs.

