
# 🔐 SSH Brute-Force Attack

---

## 📌 What is an SSH Brute-Force Attack?

An **SSH brute-force attack** is a password guessing attack in which an attacker repeatedly attempts to authenticate to a Linux system by trying numerous username and password combinations over the **SSH (Secure Shell)** service.  

The attack continues until valid credentials are found or the attacker stops attempting.

👉 SSH is commonly used by system administrators for remote management of Linux servers. Because SSH often provides **administrative access**, it is a frequent target for attackers seeking unauthorized access.

---

## 🎯 Why Do Attackers Perform SSH Brute-Force Attacks?

Attackers attempt SSH brute-force attacks to gain unauthorized access to systems for a variety of malicious purposes:

---

### 1. Initial Access
- **Goal:** Obtain valid login credentials and establish an initial foothold.  
- **Example:**  
  An attacker successfully guesses the password for the account `student` and logs into the Linux server via SSH.  
  Once authenticated, they now have direct access to the machine.

---

### 2. Remote Administration
- **Goal:** Execute commands remotely as a legitimate user.  
- **Example:**  
  ```bash
  ssh student@192.168.56.20
  ```
  The attacker can now:
  - Browse directories  
  - Execute Linux commands  
  - Install malicious software  
  - Modify system files  
  - Download sensitive information  

---

### 3. Persistence
- **Goal:** Ensure continued access even if the compromised password is changed.  
- **Example:**  
  ```bash
  sudo useradd backup_admin
  sudo usermod -aG sudo backup_admin
  ```
  Even if the original account is disabled, the attacker can continue accessing the system using the newly created account.

---

### 4. Privilege Escalation
- **Goal:** Gain administrative (root) privileges if the compromised account has limited permissions.  
- **Example:**  
  ```bash
  sudo -l
  ```
  If misconfigurations exist, the attacker may exploit them to gain **full administrative control** over the Linux server.

---

## 🚨 Indicators of an SSH Brute-Force Attack

Security analysts should monitor for:

- A high number of failed SSH login attempts within a short period.  
- Repeated authentication attempts from the same source IP address.  
- Attempts targeting multiple usernames.  
- Login attempts occurring outside normal working hours.  
- A successful login immediately following numerous failed attempts.  

---

## 🛡️ Detection with Wazuh

During this lab, **Wazuh** continuously monitors the endpoint’s authentication logs (`/var/log/auth.log`).

When multiple failed SSH authentication attempts are detected, Wazuh:

1. Collects the authentication logs from the monitored endpoint.  
2. Decodes and analyzes the log entries.  
3. Matches the activity against predefined detection rules.  
4. Generates a **security alert** in the Wazuh Dashboard.  

---

### Alert Details Include:
- 📅 Timestamp  
- 🌐 Source IP address  
- 👤 Affected username  
- 🆔 Rule ID  
- ⚠️ Alert severity  

👉 This enables the SOC analyst to **investigate the incident** effectively.
