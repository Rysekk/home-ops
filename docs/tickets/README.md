# Tickets: Foundation

Only the foundation is planned: the repo itself (F-01 to F-05), then the homelab nodes up to a self-managing Argo CD (F-06 to F-12). Everything after that (platform core, observability, apps, backups, prod migration) is deliberately **not** ticketed yet. The ADRs record where it is heading.

| # | Ticket | Depends on | Status |
|---|--------|------------|--------|
| F-01 | [Repo skeleton](F-01-repo-skeleton.md) | none | ⬜ |
| F-02 | [Pre-commit hooks](F-02-pre-commit.md) | F-01 | ⬜ |
| F-03 | [SOPS + age setup](F-03-sops-age.md) | F-01 | ⬜ |
| F-04 | [PR CI: validation](F-04-pr-ci.md) | F-01, F-02 | ⬜ |
| F-05 | [Renovate](F-05-renovate.md) | F-01 | ⬜ |
| F-06 | [Install Ubuntu on both PCs](F-06-install-ubuntu.md) | none | ⬜ |
| F-07 | [Ansible inventory + OS baseline](F-07-ansible-os-baseline.md) | F-01, F-06 | ⬜ |
| F-08 | [k3s via Ansible](F-08-k3s.md) | F-07 | ⬜ |
| F-09 | [Cilium bootstrap](F-09-cilium.md) | F-08 | ⬜ |
| F-10 | [Argo CD bootstrap + root app](F-10-argocd-bootstrap.md) | F-09 | ⬜ |
| F-11 | [Argo CD self-management + ApplicationSets](F-11-applicationsets.md) | F-10 | ⬜ |
| F-12 | [Rebuild-from-scratch drill](F-12-rebuild-drill.md) | F-11 | ⬜ |

Legend: ⬜ todo · 🔧 in progress · ✅ done
