# Phase 5 - Response

## Objective

Document the actions that should be taken after identifying an SSH brute-force attack.

---

## Containment

- Identify the attacking IP address.
- Block the source IP using firewall rules if appropriate.
- Monitor for additional authentication attempts.

---

## Eradication

- Reset compromised passwords if necessary.
- Remove unauthorized accounts.
- Review SSH configuration.

---

## Recovery

- Verify that legitimate users can authenticate.
- Confirm no unauthorized access occurred.
- Continue monitoring for recurring attacks.

---

## Recommendations

- Enable strong password policies.
- Configure account lockout.
- Disable password authentication when possible.
- Use SSH key authentication.
- Restrict SSH access using firewall rules.
- Enable Multi-Factor Authentication (MFA).

---

## Analyst Notes

Record any additional observations made during incident response.
