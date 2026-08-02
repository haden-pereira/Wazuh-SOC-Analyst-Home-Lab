# Response

## Objective

Document the actions that should be taken after identifying unauthorized user creation and privilege escalation activity.

---

## Containment

- Identify the unauthorized user account.
- Disable or lock the unauthorized account.
- Remove the account from privileged groups (if possible).
- Isolate the affected endpoint if malicious activity is suspected.
- Monitor for additional unauthorized account or privilege changes.

---

## Eradication

- Delete unauthorized user accounts.
- Remove unauthorized privilege assignments (e.g., sudo group membership).
- Review user management logs and audit logs for additional malicious activity.
- Identify and eliminate the root cause that allowed the account creation or privilege escalation.

---

## Recovery

- Verify that only authorized user accounts exist.
- Confirm privileged group memberships are correct.
- Validate that legitimate administrators retain appropriate access.
- Continue monitoring for further user creation or privilege escalation attempts.
- Ensure audit logging and Wazuh monitoring are functioning correctly.

---

## Recommendations

- Enforce the principle of least privilege.
- Restrict administrative account creation to authorized personnel.
- Enable Multi-Factor Authentication (MFA) for privileged accounts.
- Regularly review user accounts and group memberships.
- Enable and retain audit logging for user and privilege management.
- Implement periodic privilege and access reviews.
- Configure alerts for unauthorized user creation and privilege escalation events.

---
