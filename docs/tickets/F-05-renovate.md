# F-05: Renovate

**Depends on**: F-01

## Acceptance criteria
- [ ] Renovate GitHub App installed on `home-ops`, with `renovate.json` in the repo.
- [ ] Detects: Helm chart versions in Argo Applications and values, container images, GitHub Actions, the k3s version in Ansible vars, and Ansible Galaxy collections.
- [ ] Grouping and schedule set to avoid noise: patch and minor grouped weekly, major versions as separate PRs. The dependency dashboard issue is enabled.
