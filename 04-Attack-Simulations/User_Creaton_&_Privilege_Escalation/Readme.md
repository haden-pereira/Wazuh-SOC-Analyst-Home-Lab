# 👤 User Creation & Privilege Escalation Attack

---

## 📌 What is a User Creation & Privilege Escalation Attack?

A **User Creation & Privilege Escalation attack** is a post-compromise technique in which an attacker creates a new local account on a Linux system and grants that account elevated privileges (such as membership in the **sudo** group).  

This allows the attacker to maintain access and perform administrative actions, often without relying on the originally compromised account.

👉 Attackers commonly use this method after obtaining initial access so they can establish persistence and gain broader control of the system.

---

## 🎯 Why Do Attackers Perform User Creation & Privilege Escalation?

Attackers create privileged user accounts for several malicious objectives:

---

### 1. Persistence
- **Goal:** Maintain access even if the original compromised credentials are reset.  
- **Example:**  
  ```bash
  sudo useradd -m backdoor_user
  sudo passwd backup_admin
  ```
  By creating a separate account, the attacker can return later without using the first compromised user.

---

### 2. Privilege Escalation
- **Goal:** Gain administrative (root-level) permissions.  
- **Example:**  
  ```bash
  sudo usermod -aG sudo backup_admin
  ```
  If the account is added to the `sudo` group, the attacker can execute privileged system commands.

---

### 3. Defense Evasion
- **Goal:** Blend in with normal administrative activity.  
- **Example:**  
  Attackers may choose account names that appear legitimate (e.g., `sys_admin`, `backup_service`) to avoid immediate suspicion during quick reviews.

---

### 4. Full System Control
- **Goal:** Perform sensitive actions that require elevated permissions.  
- **Example:**  
  ```bash
  su - backdoor_user
  sudo whoami
  ```
  The attacker can now:
  - Modify critical system files  
  - Disable security controls  
  - Create additional backdoor accounts  
  - Access sensitive logs and configurations  
  - Install persistence mechanisms  

---

## 🚨 Indicators of User Creation & Privilege Escalation

Security analysts should monitor for:

- New local user accounts being created unexpectedly.  
- User accounts being added to privileged groups like `sudo`.  
- Modifications to `/etc/passwd`, `/etc/group`, or `/etc/sudoers`.  
- Privileged command execution from newly created accounts.  
- Administrative activity occurring outside normal change windows.  

---

## 🛡️ Detection with Wazuh

During this lab, **Wazuh** continuously monitors endpoint authentication and system activity logs, including account and privilege-related events.

When suspicious user creation or privilege assignment activity is detected, Wazuh:

1. Collects relevant logs and file change events from the monitored endpoint.  
2. Decodes and analyzes user/account management activity.  
3. Matches the behavior against predefined detection rules.  
4. Generates a **security alert** in the Wazuh Dashboard.  

---

### Alert Details Include:
- 📅 Timestamp  
- 🖥️ Affected endpoint  
- 👤 Created/modified username  
- 🛠️ Privilege/group change details  
- 🆔 Rule ID  
- ⚠️ Alert severity  

👉 This enables the SOC analyst to **investigate persistence and privilege abuse attempts** effectively.
