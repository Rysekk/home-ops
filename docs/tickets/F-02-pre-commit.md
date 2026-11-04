# F-02: Pre-commit hooks

**Refs**: ADR-0004 · **Depends on**: F-01

Catch secrets and broken YAML before they ever reach git history. On a public repo, a leaked secret can only be rotated, never taken back.

## Acceptance criteria
- [ ] `.pre-commit-config.yaml` with: **gitleaks**, yamllint, trailing-whitespace / end-of-file, check-merge-conflict, and a hook that **refuses `*.sops.*` files that aren't encrypted**.
- [ ] `.yamllint` tuned for Kubernetes YAML (long lines allowed, document start optional).
- [ ] Verified: committing a fake token is blocked.
