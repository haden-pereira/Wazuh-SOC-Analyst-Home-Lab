# Lab Architecture

## Environment

| Component | Configuration | Role |
|---|---|---|
| **Wazuh Manager** | Ubuntu Server 24.04 LTS, all-in-one deployment | Central SIEM |
| **Services** | Manager + Indexer + Dashboard | Log collection, analysis, and visualization |
| **Endpoint** | Ubuntu 22.04.5 LTS | Monitored host |
| **Agent** | Wazuh Agent v4.14.5, Agent ID `001` | Event forwarding |
| **Attacker Machine** | Ubuntu Desktop, isolated VM on same NAT network | Attack simulation |

## Network

All machines communicate within a private virtual network.

## Architecture Diagram

```text
                         +-----------------------------+
                         |   Private Virtual Network   |
                         +-----------------------------+

     +--------------------+               +----------------------+
     |  Endpoint VM       |               |  Attacker VM         |
     |  Ubuntu 22.04.5    |               |  Ubuntu Desktop      |
     |  Wazuh Agent 4.14.5|               |  Attack Simulation   |
     |  Agent ID: 001     |               |  Isolated on NAT     |
     +----------+---------+               +----------+-----------+
                |                                     
                | Logs / Events                        
                v                                     
     +-----------------------------------------------------------+
     |                    Wazuh Manager VM                       |
     |                Ubuntu Server 24.04 LTS                   |
     |             Manager + Indexer + Dashboard                |
     |                      Central SIEM                        |
     +-----------------------------------------------------------+
```

## Data Flow

```text
+-----------+
| Endpoint  |
+-----------+
      |
      v
+-------------+
| Wazuh Agent |
+-------------+
      |
      v
+---------------+
| Wazuh Manager |
+---------------+
      |
      v
+------------+
| Dashboard  |
+------------+
      |
      v
+-------------+
| SOC Analyst |
+-------------+
```

## Monitoring Flow

1. The **Endpoint** generates logs and security events.
2. The **Wazuh Agent** collects and forwards telemetry.
3. The **Wazuh Manager** processes and correlates events.
4. The **Dashboard** displays alerts and system activity.
5. The **SOC Analyst** investigates findings.
