# home-ops

GitOps repository that declares every cluster I run, the platform components on each, and the workloads they host. Argo CD only ever reads it.

## Clusters

- **homelab**: two PCs at home. Hosts staging, shared platform services and experiments.
- **oci**: single node on an Oracle Cloud VM. Hosts prod.

## Layout

| Path | Content |
|------|---------|
| `clusters/` | Argo CD root app for each cluster (`homelab`, `oci`) |
| `infrastructure/` | Platform components: `base/` + per-cluster overlays |
| `apps/` | Workloads: per-cluster values |
| `ansible/` | Node bootstrap |
| `terraform/` | Placeholder |
| `docs/` | [ADRs](docs/adr), runbooks |

See the [glossary](GLOSSARY.md) for the vocabulary used here.
