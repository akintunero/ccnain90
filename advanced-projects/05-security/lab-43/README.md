## Advanced Security Lab 43 – End-to-End Security Architecture Review and Audit Readiness

### Scenario
Your organisation is preparing for an internal security audit and a potential external compliance assessment. The audit team will expect evidence that the enterprise network has a **documented, consistent security architecture** from device access through to wireless and monitoring, not just isolated controls.

You have been asked to produce an **end-to-end security architecture document** that:

- Maps implemented controls to a simple security framework (for example access control, infrastructure protection, monitoring).
- Provides an audit-ready checklist of what is in place and what gaps remain.
- Shows how device security, AAA, ACLs, CoPP, wireless security, and 802.1X (or MAB/WebAuth) work together.
- Describes how security is monitored and how changes are reviewed over time.

This lab is a capstone: you synthesise the security topics from earlier labs into one coherent narrative and readiness pack.

### Project Objectives

By the end of this project you should be able to:

- Produce a high-level security architecture document that covers device access, infrastructure, wireless, and network access control.
- Build an audit-style checklist that maps controls to  areas (device access, AAA, ACLs, CoPP, wireless, 802.1X/MAB/WebAuth, monitoring).
- Explain how each control supports the others and where single points of failure or gaps exist.
- Propose a short "audit readiness" plan: evidence to collect, owners, and review frequency.

### Technologies and Design Topics in Scope

This project draws from the full Security section as a capstone:

- **5.1 Device access control** – lines, passwords, AAA as the foundation for audit evidence.
- **5.2 Infrastructure security features** – ACLs and CoPP and how they are documented.
- **5.3 REST API security** – how API access is secured and logged for audit.
- **5.4 Wireless security features** – EAP, WebAuth, PSK and how they are profiled.
- **5.5 Components of network security design** – threat defence, endpoint, NGFW, TrustSec, MACsec, 802.1X, MAB, WebAuth, and how they appear in an architecture document and audit checklist.

### Project Tasks

1. **Draft the security architecture narrative**
   - Write a short overview (one or two pages) that describes:
     - How administrators access network devices (SSH, AAA, break-glass).
     - How infrastructure is protected (ACLs, CoPP, management segmentation).
     - How wireless and wired access are controlled (EAP, WebAuth, 802.1X, MAB).
     - How security is monitored and tuned over time.
   - Use simple headings that an auditor could follow (e.g. Access Control, Infrastructure Protection, Monitoring).
2. **Create an audit-ready checklist**
   - Build a table or list that maps each major control to:
     - Syllabus reference (e.g. 5.1.a, 5.2.b).
     - Implementation status (in place, partial, planned, gap).
     - Evidence type (config snippet, screenshot, runbook, log sample).
     - Owner or team responsible.
   - Include device access, AAA, ACLs, CoPP, wireless profiles, 802.1X/MAB/WebAuth, and monitoring/review.
3. **Identify dependencies and gaps**
   - For each control, note what it depends on (e.g. 802.1X depends on RADIUS and switch config).
   - List the top three to five gaps that would be raised in an audit and suggest remediation order.
4. **Define audit readiness process**
   - Propose how often the architecture document and checklist are updated (e.g. after major changes, annually).
   - Describe what evidence should be collected before an audit (config backups, logs, policy docs).
   - Suggest a short runbook for "audit prep" so the team knows what to gather and who to ask.

### Design Diagram (Text Form)

Describe a single diagram that an auditor could use to understand the security architecture:

- **Control layers** – device access (AAA), infrastructure (ACLs, CoPP), network access (802.1X, MAB, WebAuth), wireless (EAP, WebAuth, guest), and monitoring (logs, review).
- **Key components** – where AAA servers, firewalls, and wireless controllers sit; where policies are enforced.
- **Data flows** – how management traffic, user authentication, and telemetry are separated and protected.

Use this description to draw one "security architecture overview" that ties all labs 34–42 together.

### Failure and What-If Analysis

Consider and document:

- An auditor asks: "How do you prove that only authorised people can access network devices?" What evidence and narrative do you provide?
- An auditor asks: "What happens if your RADIUS server is down?" How does fallback work, and is it acceptable from a compliance perspective?
- A new branch is connected without going through the standard security checklist. What controls might be missing and how would you detect that?

For each, describe the impact, the evidence you would show, and how the architecture document and checklist help answer the question.

### Expected Outcomes

After completing this project you should be able to:

- Present a concise, end-to-end security architecture document suitable for internal or external review.
- Use an audit-style checklist to show what is in place and what remains to be done.
- Explain how device access, AAA, ACLs, CoPP, wireless, 802.1X/MAB/WebAuth, and monitoring fit together in one story.
- Propose a repeatable audit readiness process with evidence and owners.

### Reflection

Reflect on:

- Which parts of the security architecture were hardest to document clearly and why.
- How the checklist would change if the organisation had to meet a specific standard (e.g. PCI-DSS, ISO 27001).
- What you would improve in the next round of security projects based on this end-to-end review.
