# F-11: Argo CD self-management + ApplicationSets

**Refs**: ADR-0001 · **Depends on**: F-10

Make adding a component equal to adding a folder.

## Acceptance criteria
- [ ] ApplicationSets in `clusters/homelab/` with a **git directory generator** over `infrastructure/*` and `apps/*`. Each cluster opts into components explicitly, e.g. a per-cluster list or a `clusters/homelab/` kustomization.
- [ ] **Argo CD and Cilium are managed by Argo** from the same values used at bootstrap. A sync shows no diff.
- [ ] Sync waves are defined: CRDs and infrastructure before apps.
- [ ] Changing a value in a PR → merge → Argo applies it automatically (proven with a trivial change).
- [ ] PR CI gets a **rendered-diff comment** (e.g. argocd-diff-preview) that shows what each PR changes in the cluster.
