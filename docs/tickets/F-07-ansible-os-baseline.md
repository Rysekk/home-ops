# F-07: Ansible inventory + OS baseline

**Refs**: ADR-0003, ADR-0008 · **Depends on**: F-01, F-06

## Acceptance criteria
- [ ] `ansible/inventory/homelab.yml` with groups `k3s_server` (compute node) and `k3s_agent` (storage node).
- [ ] A `baseline` role that is idempotent (a second run reports `changed=0`):
  - SSH hardening: no password auth, no root login
  - unattended security upgrades
  - time sync
  - swap disabled
  - kernel modules and sysctls required by Kubernetes and Cilium
  - **host firewall** (nftables/ufw): SSH from the LAN only, plus the k3s and Cilium node-to-node ports between the two nodes only
- [ ] `ansible/README.md`: how to run it, and the required Ansible version and collections (`requirements.yml`).
