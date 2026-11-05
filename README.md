# home-ops

GitOps repository that declares every cluster I run, the platform components on each, and the workloads they host. Argo CD only ever reads it.

## Clusters

- **homelab**: two PCs at home. Hosts staging, shared platform services and experiments.
- **oci**: single node on an Oracle Cloud VM. Hosts prod.

## Hardware

| Node | Role | CPU | RAM | Storage | OS |
|------|------|-----|-----|---------|----|
| `cp-01` | k3s server (compute) | Intel Core i7-7700T (4C/8T) | 32 GB | 256 GB NVMe | Ubuntu 26.04 LTS |
| storage node (planned) | k3s agent (storage) | | 8 GB | 1 TB SSD | Ubuntu 26.04 LTS |

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
