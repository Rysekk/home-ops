# home-ops

GitOps repository that declares every cluster I run, the platform components on each, and the workloads they host. Argo CD only ever reads it.

## Clusters

- **homelab**: two machines at home (a mini PC and a laptop). Hosts staging, shared platform services and experiments.
- **oci**: single node on an Oracle Cloud VM. Hosts prod.

## Hardware

| Node | Role | CPU | RAM | Storage | OS |
|------|------|-----|-----|---------|----|
| `cp-01` | k3s server (compute) | Intel Core i7-7700T (4C/8T) | 32 GB | 256 GB NVMe | Ubuntu 26.04 LTS |
| `worker-01` | k3s agent (storage) | TBD (Acer Aspire VN7-571G laptop) | 12 GB | 500 GB SATA SSD | Ubuntu 26.04 LTS |

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
