## Detection 

## Objective

Verify that the SSH brute-force activity has been successfully detected by Wazuh.

---

## Detection Workflow

```text
SSH Login Failure
        │
        ▼
/var/log/auth.log
        │
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
Security Alert
```

---

## Log Source

```
/var/log/auth.log
```

---

## Detection Rule

| Field | Value |
|--------|-------|
| Rule ID | 5710 |
| Rule Level | 5 |
| Rule Description | sshd: Attempt to login using a non-existent user |

---

## Alert Information

| Field | Value |
|--------|-------|
| Timestamp | 2026-07-01T16:17:07.522+0000 |
| Source IP | 	10.0.2.15 |
| Username | baduser |
| Endpoint | 	wazuh-agent |
| Event | Failed SSH Login |

---

## Evidence

- Command:
<img width="1217" height="102" alt="Comand" src="https://github.com/user-attachments/assets/515666b4-742e-4e8a-b2c4-dd52babe1d07" />

- Wazuh Dashboard:
<img width="1131" height="680" alt="Logs" src="https://github.com/user-attachments/assets/4a7ea34b-e899-475b-8640-da80af4307f0" />

  
- Alert Details:
<img width="1006" height="775" alt="image" src="https://github.com/user-attachments/assets/9274fee9-5d00-4fad-9371-416ddd2aed80" />
<img width="603" height="273" alt="image" src="https://github.com/user-attachments/assets/898f7296-9f4c-4961-be8c-20f2a548bdd3" />



  

---

## Expected Outcome

The Wazuh Manager should identify multiple failed authentication attempts and generate an alert indicating possible brute-force activity.

