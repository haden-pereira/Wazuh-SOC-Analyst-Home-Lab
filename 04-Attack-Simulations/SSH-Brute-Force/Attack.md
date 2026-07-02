# Phase 2 - Attack Simulation

## Objective

The objective of this phase is to simulate an SSH brute-force attack against the monitored Ubuntu endpoint. Multiple failed authentication attempts are generated to trigger security events that can be collected and analyzed by Wazuh.

---

## Attack Scenario

An attacker located on a separate Ubuntu Desktop virtual machine attempts to gain unauthorized access to the Endpoint VM by repeatedly trying different passwords for a known user account.

No automated password-cracking tools (such as Hydra) are used in this simulation. Instead, multiple manual SSH login attempts are performed to demonstrate how authentication failures are logged and detected.

---

## Attack Path

```text
Attacker VM
      │
      │ SSH Login Attempts
      ▼
Endpoint VM
      │
      │ Authentication Logs
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
| Target Service | SSH |
| Target Port | 22 |
| Target IP | *10.0.2.3* |

---

## Attack Commands



```bash
 for i in {1..15}; do ssh -o ConnectTimeout=2 baduser@10.0.2.3 > /dev/null; sleep 0.5; done
```



## Expected Result
Failed authentication attempt should generate an event within the Linux authentication logs.

These events are then forwarded to the Wazuh Manager for analysis.
