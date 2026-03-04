## Addressing Plan – Lab 46 Advanced Design and Automation

This plan demonstrates how to consistently apply the **MASTER ADDRESSING BLUEPRINT** across multiple sites in a way that is automation-friendly.

### Blueprint Alignment
- **Enterprise LAN**: `10.X.0.0/24` ranges assigned per site and per function.
- **Small networks / labs**: `192.168.X.0/24` reserved for isolated environments and testbeds.
- **WAN**: `10.255.X.0/30` for all point-to-point site interconnects.
- **ISP simulation**: `203.0.113.0/24` and `198.51.100.0/24` for upstream providers.

### Example Site Allocations

| Site Code | Role           | User VLAN 10         | Server VLAN 30       | Notes                      |
|----------|----------------|----------------------|----------------------|----------------------------|
| HQ       | Headquarters   | 10.10.0.0/24         | 10.30.0.0/24         | Core site and data centre  |
| B1       | Large Branch   | 10.110.0.0/24        | 10.130.0.0/24        | Regional office            |
| B2       | Small Branch   | 10.210.0.0/24        | 10.230.0.0/24        | Smaller remote office      |

### Management and WAN

| Function           | Example Subnet       | Notes                                   |
|--------------------|----------------------|-----------------------------------------|
| Global Mgmt VLAN   | 10.99.0.0/24         | Centralised management at HQ            |
| Site WAN links     | 10.255.X.0/30        | Serial or Ethernet P2P links per site   |
| ISP-1 External     | 203.0.113.0/24       | Primary ISP                             |
| ISP-2 External     | 198.51.100.0/24      | Secondary ISP                           |

### Automation Considerations
- Represent the above allocations in a structured data format (for example, YAML or JSON) with fields such as:
  - `site_code`, `role`, `user_subnet`, `server_subnet`, `management_subnet`, `wan_links`.
- Use these fields in templated configurations to:
  - Generate VLAN and SVI definitions.
  - Build WAN interface configurations and routing policies.

This addressing plan provides a consistent foundation for the remaining advanced design and automation labs.

