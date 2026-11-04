# F-09: Cilium bootstrap

**Refs**: ADR-0009 · **Depends on**: F-08

Ansible installs Cilium once with Helm. Argo CD adopts it in F-11 using the **same values file**, so there is no drift between bootstrap and steady state.

## Acceptance criteria
- [ ] Values live at `infrastructure/base/cilium/values.yaml` (plus a homelab overlay if needed). Ansible reads them from the repo, and they aren't duplicated anywhere.
- [ ] Chart version pinned.
- [ ] Hubble enabled.
- [ ] Both nodes are `Ready`. `cilium status` and `cilium connectivity test` pass.
- Out of scope: Gateway API, LB-IPAM, NetworkPolicies (platform core, later).
