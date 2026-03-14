## Advanced Automation Lab 44 – Building a Configuration Compliance Checker

### Scenario
Your enterprise network has grown over time and different teams have touched the configuration. Some sites have the correct NTP, logging, and management settings. Others still use legacy servers or missing commands. There is no simple way to answer a basic question: **which devices match the current standard and which do not**.

In this first automation project you will design a small configuration compliance checker. The goal is not to push changes, but to:

- Describe a simple standard for a few key settings.  
- Represent that standard and the device list as structured data.  
- Use Python and APIs to collect the current state and compare it against the standard.  
- Produce a human readable report that operations can act on.

You are creating a tool that answers "are we compliant" before you move on to more advanced automation in later labs.

### Project Objectives

By the end of this project you should be able to:

- Define a narrow but clear configuration standard for services such as NTP, logging, or SNMP.  
- Represent device inventory and intent in JSON so that a script can consume it.  
- Explain how a Python script or similar tool can query devices or a controller for current settings.  
- Interpret REST API responses and map them to pass or fail checks.  
- Outline how this compliance checker could be extended or integrated with orchestration tools.

### Technologies and Design Topics in Scope

This project draws from the Automation section:

- **6.1 Python components and scripts**  
  Reading and explaining simple Python used for state collection and comparison.  
- **6.2 JSON encoded data**  
  Designing JSON structures for inventory and standards.  
- **6.3 Data modelling with YANG**  
  Understanding how models make it easier to target specific configuration items.  
- **6.4 APIs for Cisco Catalyst Center and SD-WAN Manager**  
  Describing how their APIs expose device configuration and operational data.  
- **6.5 REST API responses**  
  Interpreting HTTP codes and payloads returned by RESTCONF or controller APIs.  
- **6.6 EEM applets**  
  Considering how local event based checks could complement central compliance.  
- **6.7 Orchestration tools**  
  Comparing a lightweight script to tools like Ansible or other orchestrators.

### Project Tasks

1. **Choose the scope of your standard**  
   - Select two or three configuration items that matter everywhere, for example:
     - NTP server addresses.  
     - Syslog server and logging level.  
     - SNMP community or user configuration.  
   - Write a short text description of what "good" looks like for each item.
2. **Design the JSON data model**  
   - Create a JSON structure that includes:
     - A list of devices with IP, role, and site.  
     - The expected settings for your chosen configuration items.  
   - Make sure your structure is easy to extend if new checks are added later.
3. **Plan how to collect current state**  
   - Decide whether your checker will:
     - Call a controller API such as Cisco Catalyst Center or SD-WAN Manager.  
     - Use RESTCONF directly against devices.  
     - Use a temporary SSH based approach if APIs are not yet available.  
   - For each option, describe what authentication is needed and how you will protect credentials.
4. **Outline or review a Python script**  
   - Sketch a script (or read an example) that:
     - Reads the JSON inventory and standard.  
     - Connects to each device or to the controller.  
     - Retrieves the relevant configuration fields.  
     - Compares actual values to expected ones and records pass or fail.  
   - Note the main functions or blocks and what each is responsible for.
5. **Design the compliance report**  
   - Decide what the output should look like, for example:
     - A table per site showing pass and fail counts.  
     - A list of devices that are out of compliance and why.  
   - Describe how operations staff would use this report during maintenance windows.

### Design Diagram (Text Form)

Describe a logical view of your compliance checker:

- A "standards" block that contains JSON definitions for required settings.  
- An "inventory" block that lists devices and connection details.  
- A "collector" block that uses Python and APIs or SSH to pull current state.  
- A "comparison" block that evaluates pass or fail.  
- A "report" block that generates human readable output for engineers.

Use this description to draw a simple flow diagram from standards to final report.

### Failure and What-If Analysis

Consider the following situations and document your response:

- A device is reachable but the API call fails or returns an error code. How does the checker record this and alert the team.  
- A new device is added to the network but not to the JSON inventory. How will you notice that it is missing from compliance checks.  
- The definition of the standard changes, for example a new NTP server is added. How do you update the JSON and make sure all devices are tested against the new value.

For each case, explain the operational impact and how your design reduces risk or confusion.

### Expected Outcomes

After completing this project you should be able to:

- Describe a small but concrete automation solution that improves visibility of configuration drift.  
- Walk someone through the data structures and script flow used by a compliance checker.  
- Explain how this approach prepares your team for more advanced automation in later labs.

### Reflection

Spend a few minutes noting:

- Which configuration items in your own environment would benefit most from compliance checking.  
- How comfortable your team is with JSON, APIs, and reading simple scripts today.  
- What you would do next to turn this design into a working tool, even if you start with a small pilot.

## Advanced Automation Lab 44 – First Steps in Network Automation and APIs

### Scenario
Your network team has been asked to "start using automation" to reduce repetitive work and improve consistency. Today, most changes are made by hand on the CLI. There is no clear inventory of which devices exist, and simple tasks such as pushing a new NTP server or updating an ACL require a lot of copy and paste.

Management is not asking for a full controller deployment on day one. Instead, they want you to propose and demonstrate a small but meaningful automation initiative that:

- Uses basic Python or a similar scripting language where appropriate.
- Works with structured data such as JSON or YAML.
- Interacts with at least one API (for example Cisco DNA Center, vManage, or device level RESTCONF/NETCONF).

In this first automation lab you concentrate on a very small but valuable use case that builds confidence in scripting and APIs.


### Project Objectives

By the end of this project you should be able to:

- Read and reason about simple Python scripts that perform network tasks.  
- Understand how JSON and YANG style data models structure configuration and state.  
- Explain how APIs from Cisco DNA Center or vManage can be used to query and change the network.  
- Interpret REST API responses, including codes and payload data.  
- Describe where EEM applets or orchestration tools fit into your automation roadmap.

### Technologies and Topics in Scope

This project draws from the Automation section:

- **6.1 Python components and scripts**
  - Interpreting basic Python constructs used in network automation.
- **6.2 JSON-encoded data**
  - Constructing valid JSON-encoded files to describe inventory and intent.
- **6.3 Data modelling with YANG**
  - Describing high-level principles and benefits of a data modelling language such as YANG.
- **6.4 APIs for Cisco Catalyst Center and SD-WAN Manager**
  - Describing how these APIs expose configuration and operational data.
- **6.5 REST API responses**
  - Interpreting REST API response codes and payloads using Cisco Catalyst Center and RESTCONF.
- **6.6 EEM applets**
  - Constructing EEM applets to automate configuration, troubleshooting, or data collection.
- **6.7 Orchestration tools**
  - Comparing agent-based and agentless orchestration tools (for example Chef, Puppet, Ansible, and SaltStack).

### Project Tasks

You do not need to write production quality code. The goal is to understand and explain an automation approach that could realistically be adopted by your team.

1. **Choose a simple but valuable use case**
   - Examples:
     - Collect basic inventory and interface status from all devices.  
     - Roll out a new NTP or syslog configuration to a group of switches.  
     - Check that certain ACLs or QoS policies are present and correctly configured.
2. **Define your data model**
   - Decide what information your script or tool needs (for example device IPs, roles, credentials, target NTP servers).  
   - Represent that data in JSON or YAML. Make sure the structure is clear and easy to extend.
3. **Select an interaction method**
   - Option A: Use device level APIs (RESTCONF or NETCONF) to pull or push configuration snippets.  
   - Option B: Use a controller API such as Cisco DNA Center or vManage to perform actions on your behalf.  
   - Option C: Use SSH based libraries (for example in Python) as a first step while you explore APIs.
4. **Sketch or read a Python script**
   - Either write a small script yourself or find a simple example that:
     - Reads your JSON or YAML inventory.  
     - Connects to devices or a controller.  
     - Performs your chosen task in a loop.  
   - Make sure you understand each major part of the script: input, connection, action, and output.
5. **Consider EEM and orchestration tools**
   - Describe how an EEM applet could automate a very local task on a device (for example collecting logs when an interface flaps).  
   - Compare this to what an orchestration tool like Ansible would do at scale.

### Validation and What-If Analysis

Think through:

- How you would test your automation safely (for example read only operations first, then small pilot groups).  
- How you would roll back changes if something went wrong.  
- How you would handle authentication and secrets securely as your scripts or tools grow.

### Expected Outcomes

After completing this project you should be able to:

- Explain, in plain language, a small automation project that would help your team.  
- Walk through a basic Python and JSON based workflow for that project.  
- Describe how you would evolve this into a more robust solution using controllers, APIs, or orchestration tools.

### Reflection

Reflect on:

- Which tasks in your current environment are best suited to early automation.  
- Which skills you and your team would need to develop to be comfortable with scripting and APIs.  
- How you can build confidence and trust in automated changes by starting small and validating carefully.

