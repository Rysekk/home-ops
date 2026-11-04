# F-04: PR CI: validation

**Refs**: ADR-0001 · **Depends on**: F-01, F-02

Every PR proves its YAML renders and is valid before merge.

## Acceptance criteria
- [ ] GitHub Actions workflow on `pull_request`, with jobs that only run when their paths change:
  - **gitleaks** (always)
  - **kustomize build / helm template** for every changed folder under `clusters/`, `infrastructure/` and `apps/`
  - **kubeconform** on the rendered output (with the CRD schemas catalog, so Cilium and Argo CRDs validate)
  - **ansible-lint** on `ansible/**`
- [ ] Workflow actions pinned by SHA (Renovate will bump them, F-05).
- [ ] A deliberately broken manifest fails the PR.
- Out of scope: the rendered-diff comment (F-11), and tflint/terraform plan (once Terraform moves, ADR-0011).
