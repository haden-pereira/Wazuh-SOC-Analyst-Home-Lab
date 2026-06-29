# Wazuh SOC Analyst Home Lab

A hands-on Security Operations Center (SOC) home lab built on Wazuh SIEM, covering the full analyst workflow — from infrastructure deployment and endpoint monitoring through attack simulation, alert investigation, detection engineering, and professional incident documentation.

***

## Project Overview

This lab showcases a practical SOC environment built around **Wazuh SIEM** to simulate how a security analyst monitors endpoints, investigates alerts, and documents suspicious activity.

The environment is designed to mirror real blue-team workflows:
- Collect security telemetry from an Ubuntu endpoint
- Forward and analyze logs through Wazuh Manager
- Review alerts in the Wazuh Dashboard
- Simulate attacker techniques in a controlled lab
- Investigate detections and map them to MITRE ATT&CK

***

## Objectives

- Deploy a working SIEM environment in a home lab
- Configure endpoint monitoring with the Wazuh Agent
- Simulate realistic attack activity on a Linux host
- Generate, review, and investigate security alerts
- Create and tune detections for higher signal quality
- Document incidents using a SOC analyst mindset

***

## Lab Architecture

```text
+-----------------------------+          +-----------------------------+
|     Attacker VM             |          |     Wazuh Server VM         |
|     Ubuntu Desktop          |          |     Ubuntu Server 24.04     |
|     (Attack simulation)     |          |                             |
|     10.0.2.15                | -------> |  Wazuh Manager              |
+-----------------------------+          |  Wazuh Indexer (OpenSearch) |
                                         |  Wazuh Dashboard            |
+-----------------------------+          |  10.0.2.3                   |
|     Endpoint VM             |          +-----------------------------+
|     Ubuntu 22.04.5 LTS      |                      ^
|     Wazuh Agent v4.14.5     | ---------------------|
|     Agent ID: 001           |     Log forwarding
|     10.0.2.15               |     (port 1514)
+-----------------------------+

Network: VirtualBox NAT Network (isolated)
```

### Components

| Component | Role |
|-----------|------|
| Ubuntu Endpoint | Generates logs and simulated attack activity |
| Wazuh Agent | Collects endpoint telemetry and forwards events |
| Wazuh Manager | Processes logs, applies rules, and triggers alerts |
| Wazuh Dashboard | Visualizes alerts and supports investigation |

***

## Tools and Technologies

| Tool | Purpose |
|------|---------|
| Wazuh | SIEM platform, detection, and alerting |
| Ubuntu | Monitored Linux endpoint |
| VirtualBox | Lab virtualization |
| Linux | System administration and attack simulation |
| MITRE ATT&CK | Detection mapping and adversary behavior classification |

***

## Attack Simulations Completed

| Attack Simulation | Outcome | Analyst Value |
|------------------|---------|---------------|
| Unauthorized User Creation | Detected | Demonstrates account monitoring and suspicious admin activity visibility |
| SSH Brute Force | Detected | Shows authentication monitoring and repeated failed login detection |
| Privilege Escalation | Detected | Highlights elevated access monitoring and post-compromise visibility |

***

## Skills Demonstrated

- SIEM deployment and basic architecture design
- Endpoint visibility and log forwarding
- Linux security monitoring
- Alert triage and investigation
- Detection engineering and rule tuning
- Incident documentation and reporting
- Threat hunting in a controlled environment
- MITRE ATT&CK-based detection mapping

***

## Workflow

1. Build the virtual lab environment.
2. Install and configure the Wazuh components.
3. Connect the Ubuntu endpoint to the Wazuh Manager.
4. Simulate attack techniques on the monitored host.
5. Review generated alerts in the dashboard.
6. Investigate events and validate detections.
7. Document findings like a SOC analyst.

***

## Why This Project Matters

This home lab demonstrates practical SOC skills beyond theory. It shows the ability to deploy a monitoring stack, generate meaningful telemetry, investigate alerts, and present findings in a structured, analyst-friendly format.

For cybersecurity portfolios, projects like this help prove hands-on capability in:
- Security monitoring
- Detection validation
- Incident analysis
- Blue-team operations
- Technical documentation

## Future Improvements
 
- Deploy Wazuh active response to auto-block IPs after brute force threshold


