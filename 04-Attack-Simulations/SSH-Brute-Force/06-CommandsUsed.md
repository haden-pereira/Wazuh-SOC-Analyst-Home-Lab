# Commands Reference

This document contains every command used throughout the SSH brute-force detection lab.

---

## Attack Commands

```bash
for i in {1..15}; do ssh -o ConnectTimeout=2 wazuhagent123@10.0.2.3 > /dev/null; sleep 0.5; done

```

---

## Investigation Commands

View authentication logs

```bash
sudo cat /var/log/auth.log
```

View recent logins

```bash
last
```

View active sessions

```bash
who
```

Check SSH service

```bash
systemctl status ssh
```

View SSH journal

```bash
journalctl -u ssh
```

Check listening SSH port

```bash
ss -tulpn | grep ssh
```

Check failed authentication events

```bash
grep "Failed password" /var/log/auth.log
```

---

## Wazuh Commands

Restart Agent

```bash
sudo systemctl restart wazuh-agent
```

Check Agent Status

```bash
sudo systemctl status wazuh-agent
```

View Agent Logs

```bash
sudo tail -f /var/ossec/logs/ossec.log
```


