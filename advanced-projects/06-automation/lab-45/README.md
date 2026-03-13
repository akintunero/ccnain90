## Advanced Automation Lab 44 – First Steps in Network Automation and APIs

### Scenario
Your network team has been asked to "start using automation" to reduce repetitive work and improve consistency. Today, most changes are made by hand on the CLI. There is no clear inventory of which devices exist, and simple tasks such as pushing a new NTP server or updating an ACL require a lot of copy and paste.

Management is not asking for a full controller deployment on day one. Instead, they want you to propose and demonstrate a small but meaningful automation initiative that:

- Uses basic Python or a similar scripting language where appropriate.
- Works with structured data such as JSON or YAML.
- Interacts with at least one API (for example Cisco DNA Center, vManage, or device level RESTCONF/NETCONF).

### Project Objectives

By the end of this project you should be able to:

- Read and reason about simple Python scripts that perform network tasks.  
- Understand how JSON and YANG style data models structure configuration and state.  
- Explain how APIs from Cisco DNA Center or vManage can be used to query and change the network.  
- Interpret REST API responses, including codes and payload data.  
- Describe where EEM applets or orchestration tools fit into your automation roadmap.

### Technologies and Topics in Scope

This project ties into the ENCOR Automation section:

- Basic Python components and scripts.  
- JSON encoding and structured data.  
- High level principles of YANG and data modelling.  
- APIs for Cisco DNA Center and vManage.  
- REST API codes and payloads using DNA Center or RESTCONF.  
- EEM applets for configuration, troubleshooting, or data collection.  
- Agent based and agentless orchestration tools such as Chef, Puppet, Ansible, and SaltStack.

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

