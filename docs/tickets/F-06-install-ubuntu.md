# F-06: Install Ubuntu 24.04 on both PCs

**Refs**: ADR-0003

The only manual step. Everything after it is Ansible.

## Acceptance criteria
- [ ] Ubuntu Server 24.04 LTS (minimal) on the **compute node** (32 GB RAM / 252 GB SSD) and the **storage node** (8 GB RAM / 1 TB SSD).
- [ ] Hostnames chosen and recorded. DHCP reservations set on the Livebox so the IPs are stable.
- [ ] SSH key login works from the laptop, with one admin user.
- [ ] `docs/hardware.md`: CPU, RAM, disks, MAC address, IP and role for each machine.
