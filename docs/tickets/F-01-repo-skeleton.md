# F-01: Repo skeleton

**Refs**: ADR-0001

Create the directory layout everything else plugs into, then publish the repo publicly on GitHub as `Rysekk/home-ops`.

```
clusters/homelab/        # Argo CD root app for this cluster
clusters/oci/            # empty placeholder (ADR-0011)
infrastructure/          # platform components: base/ + per-cluster overlays
apps/                    # workloads: per-cluster values
ansible/                 # node bootstrap
terraform/               # empty placeholder (ADR-0011)
docs/adr/  docs/tickets/  docs/runbooks/
```

## Acceptance criteria
- [ ] Layout above exists (with `.gitkeep` where empty), plus `README.md`, `LICENSE`, `.gitignore`, `.editorconfig`.
- [ ] README explains in under a minute: what the repo is, the two clusters, the folder map, and links to GLOSSARY and ADRs.
- [ ] Repo pushed to GitHub as public, with branch protection on `main` (PR required, CI must pass once F-04 exists).
