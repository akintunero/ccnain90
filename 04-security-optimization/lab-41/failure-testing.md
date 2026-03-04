## Failure Testing – Lab 36 Security and Monitoring

### Test 1 – Overly Restrictive ACL
- **Action**
  - Modify an ACL so that it inadvertently blocks legitimate user access to a business-critical HQ application.
- **Expected impact**
  - Users in VLAN 10 can no longer reach the application server at HQ.
- **Verification**
  - `show access-lists` to confirm hit counters on deny statements.
  - `ping` and application tests from branch users to HQ.
- **Recovery**
  - Refine the ACL to permit the required traffic while maintaining security posture.

### Test 2 – Guest VLAN Escalation Attempt
- **Action**
  - Temporarily relax ACLs protecting guest VLAN 40 to simulate misconfiguration.
- **Expected impact**
  - Guest users may gain unintended access to internal VLANs.
- **Verification**
  - Attempt `ping` and access to internal resources from the guest network.
  - Check logs for unauthorised attempts.
- **Recovery**
  - Reinstate strict guest ACLs to allow only internet-bound traffic.

### Test 3 – Logging Disabled
- **Action**
  - Disable or misconfigure syslog on the branch router.
- **Expected impact**
  - Security and operational events are no longer recorded centrally.
- **Verification**
  - `show logging` and syslog server logs to confirm absence of new messages.
- **Recovery**
  - Restore correct syslog configuration and verify log flow resumes.

### Documentation
For each test:
- Record the configuration changes made, observed symptoms, and log entries.
- Summarise the security risk introduced and how timely monitoring could detect it.
- Capture recommendations for operational procedures and change control.

