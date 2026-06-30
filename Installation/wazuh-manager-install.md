# Wazuh Manager Installation

## System Information

| Component | Details |
|---|---|
| **OS** | Ubuntu 22.04 |
| **CPU** | 4 cores |
| **RAM** | 8 GB |

## Installation

Updated packages:

```bash
sudo apt update
```

Installed Wazuh:

```bash
curl -sO https://wazuh.com && sudo bash ./wazuh-install.sh -a

```

## Verification

Checked service:

```bash
systemctl status wazuh-manager
```

Result:

- **Service running successfully**
