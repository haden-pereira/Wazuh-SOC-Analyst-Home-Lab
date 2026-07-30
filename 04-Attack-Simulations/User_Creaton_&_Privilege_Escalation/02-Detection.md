# Detection

## Objective

Verify that user creation and privilege escalation activities are successfully detected by Wazuh.

---

## Detection Workflow

```text
         User Creation                Privilege Escalation
       │                              │
       ▼                              ▼
/var/log/auth.log           /var/log/audit/audit.log
       │                              │
       └──────────────┬───────────────┘
                      ▼
                 Wazuh Agent
                      │
                      ▼
                Wazuh Manager
                      │
                      ▼
                Rule Matching
                      │
                      ▼
                Security Alerts
```

---

## Log Sources

```text
/var/log/auth.log (User creation)
/var/log/audit/audit.log (Privilege escalation)
```

---

## Detection Rules

### User Creation

| Field | Value |
|--------|-------|
| Rule ID | 5902 |
| Rule Level | 8 |
| Rule Description | New user added to the system |

### Privilege Escalation

| Field | Value |
|--------|-------|
| Rule ID | 100003 |
| Rule Type | Custom Local Rule |
| Rule Level | 12 |
| Rule Description | Privilege escalation: User added to sudo group using usermod |

---

## Alert Information

### User Creation

| Field | Value |
|--------|-------|
| Timestamp | July 30, 2026 @ 18:43:17  |
| Username | backdoor_user |
| Endpoint | wazuhagent123-VirtualBox |
| Event | New Local User Created |

### Privilege Escalation

| Field | Value |
|--------|-------|
| Timestamp | July 30, 2026 @ 18:44:00 |
| Username | backdoor_user |
| Endpoint | wazuhagent123-VirtualBox |
| Command | usermod -aG sudo backdoor_user |
| Event | Privilege Escalation Detected |

---

## Evidence

### Attack Commands

```bash
sudo useradd -m -s /bin/bash backdoor_user
sudo passwd backdoor_user
sudo usermod -aG sudo backdoor_user
```

---

### User Creation - Wazuh Dashboard

<img width="1847" height="489" alt="image" src="https://github.com/user-attachments/assets/730f0043-7711-46a8-9eca-472ce6be9351" />


---

### User Creation - Alert Details

<img width="913" height="763" alt="image" src="https://github.com/user-attachments/assets/f3077102-a11c-4bd4-9d96-b5015c5a2f9f" />
<img width="924" height="199" alt="image" src="https://github.com/user-attachments/assets/da355ee0-85e3-48da-85f1-696c170c8170" />

---

### Privilege Escalation - Wazuh Dashboard

<img width="1847" height="423" alt="image" src="https://github.com/user-attachments/assets/78b90406-ee2a-43b7-a3cd-e28bb487462a" />

---

### Privilege Escalation - Alert Details

<img width="923" height="748" alt="image" src="https://github.com/user-attachments/assets/12f1cfcf-fe9d-452e-a154-1b5abaa922be" />
<img width="925" height="227" alt="image" src="https://github.com/user-attachments/assets/4204b0a4-dc9f-4379-96d9-9cf516df559f" />


---

## Expected Outcome

The Wazuh Manager successfully detects both user account creation and privilege escalation activities.

- The default Wazuh rule (**Rule ID 5902**) detects the creation of a new local user account.
- The custom Wazuh rule (**Rule ID 100003**) detects the execution of the `usermod` command used to add a user to the `sudo` group. This action grants administrative privileges and is classified as a privilege escalation event.
Together, these alerts provide visibility into account management activities that could indicate unauthorized persistence or privilege escalation on a monitored Linux endpoint.
