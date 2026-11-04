# F-10: Argo CD bootstrap + root app

**Refs**: ADR-0001, ADR-0002 · **Depends on**: F-09

## Acceptance criteria
- [ ] Ansible installs Argo CD with Helm, using values from `infrastructure/base/argocd/values.yaml` (chart version pinned).
- [ ] Ansible applies `clusters/homelab/root.yaml`, which points at `clusters/homelab/` in `home-ops` on `main`. After this step, Ansible's job is done.
- [ ] Argo UI reachable from the laptop with `kubectl port-forward` (ingress comes later). The initial admin password is rotated, or admin is disabled once SSO exists.
