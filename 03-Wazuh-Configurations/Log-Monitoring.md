
# Log Monitoring — Wazuh Configuration

> [!IMPORTANT]
> This document summarises the active log sources monitored in this lab and the network ports used for agent-to-manager communication.

## Log Source Summary

| Log Source | Path / Mechanism | Frequency | Primary Use |
|---|---|---|---|
| **journald** | `systemd journal` | Real-time | Authentication, sudo, user account events |
| **Syscheck (FIM)** | `/etc`, `/usr/bin`, `/usr/sbin` | Every 12 hours | File tampering, config changes, binary replacement |

## Ports Configuration

| Port | Protocol | Purpose |
|---|---|---|
| **1514** | TCP | Log event forwarding — agent sends collected logs to the Wazuh Manager |
| **1515** | TCP | Agent registration and key exchange (enrollment with the Manager) |
| **443** | TCP (HTTPS) | Wazuh Dashboard access via browser |

## Port Notes

- Default Wazuh ports were used for this lab — `1514` for the secure agent connection and `1515` for enrollment, both on the Wazuh Server (`10.0.2.3`).
- Dashboard access runs over HTTPS on port `443` rather than the default unencrypted alternative — confirmed during the lab security hardening step.
