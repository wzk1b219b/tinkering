# On-Call Cheatsheet

Quick reference for late-night incidents.

## First 5 Minutes

- `tail -200f /var/log/app.log` — watch live logs
- `systemctl status app` — is it running?
- `curl -fsS http://localhost/health` — local health check

## Common Fixes

- Restart service: `sudo systemctl restart app`
- Reload config: `sudo systemctl reload app`
- Check disk: `df -h` / `du -sh *`
- Check memory: `free -h`
- Check load: `uptime`

## Escalation

- `journalctl -u app --since "10 min ago"` — grab recent logs
- `tcpdump -i eth0 port 443 -c 100` — capture traffic
- `strace -p <pid> -f -e trace=network` — debug syscalls

## Aftermath

- Write a blameless postmortem
- Add a runbook entry
- Update this file if you learned something
