# User Creation and Privilege Escalation Simulation

## Objective

The objective of this phase is to simulate an attacker creating a new local user account and then escalating its privileges by granting administrative (sudo) access on the monitored Ubuntu endpoint. These activities generate security events that can be collected and analyzed by Wazuh.

---

## Attack Scenario

An attacker who has obtained administrative access to the Endpoint VM creates a new local user account to establish persistence. The attacker then adds the newly created account to the **sudo** group, granting it administrative privileges.

This simulation demonstrates how Wazuh monitors account creation and privilege escalation events that may indicate unauthorized system modifications.

---

## Attack Path

```text
Administrator / Attacker
          │
          │ Create User
          │ Grant Sudo Privileges
          ▼
Endpoint VM
          │
          │ Authentication & Account Management Logs
          ▼
Wazuh Agent
          │
          ▼
Wazuh Manager
          │
          ▼
Wazuh Dashboard
```

---

## Target Information

| Item | Value |
|------|-------|
| Target System | Ubuntu Endpoint |
| Actions | User Creation & Privilege Escalation |
| User Created | backdoor_user |
| Privilege Granted | sudo |
| Privileges Required | Root / Sudo |

---

## Attack Commands

Create a new user:

```bash
sudo useradd -m -s /bin/bash backdoor_user
sudo passwd backdoor_admin
```

Grant administrative privileges:

```bash
sudo usermod -aG sudo backdorr_user
```

Verify the user's group membership:

```bash
id backdoor_user
```

---

## Expected Result

The creation of a new user account and the assignment of administrative privileges should generate account management and group modification events within the Linux authentication logs.

These events are then forwarded by the Wazuh Agent to the Wazuh Manager for analysis. Wazuh detects and records both the user creation and privilege escalation activities, allowing them to be investigated through the Wazuh Dashboard.
