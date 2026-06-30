# Wazuh Agent Installation

> This section documents the installation and verification of the Wazuh agent on the target Ubuntu system.

## System Information

| Component | Details |
|---|---|
| **OS** | Ubuntu 22.04 |
| **CPU** | 4 cores |
| **RAM** | 8 GB |

## Installation

### Update Packages

```bash
sudo apt update
```

### Install Wazuh Agent

```bash
curl -so wazuh-agent.deb https://wazuh.com && sudo WAZUH_MANAGER="<10.0.2.3>" dpkg -i ./wazuh-agent.deb && sudo systemctl enable wazuh-agent && sudo systemctl start wazuh-agent
```

## Verification

### Check Agent Service

```bash
systemctl status wazuh-agent
```

Result:

- **Service running successfully**
