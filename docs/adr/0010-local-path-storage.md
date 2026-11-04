# Node-local storage, no replicated storage on two nodes

Persistent volumes use k3s `local-path` on SSDs, with workloads pinned by node label. Bulk data (registry cache, logs, metrics and traces, game saves) goes on the **storage node** (1 TB). Longhorn was rejected for now: it needs three nodes to be worth it, a replica needs equal space on every node (capped by the 252 GB disk), and it costs CPU and RAM on both machines. Longhorn or Rook-Ceph is revisited when a third node arrives.

## Consequences

Each volume lives on one disk. Until VolSync backups exist, losing a disk loses its data. Nothing precious lives on homelab before then.
