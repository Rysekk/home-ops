# k3s on Ubuntu 24.04, provisioned by Ansible, with Talos deferred

Homelab nodes run Ubuntu 24.04 LTS with k3s, installed and configured from `ansible/`. I chose a general-purpose distro over Talos Linux because shell access to the nodes is the point: debugging cgroups, OOM, I/O and networking down to the Linux mechanism is the main thing I want to learn, and Ansible on real Linux is the more transferable skill. Talos (immutable, API-only, no configuration drift) is the leading alternative in the home-ops community. It stays a candidate for a later, documented migration.

## Consequences

- Configuration drift is possible because nodes are mutable. The mitigation is that every change goes through Ansible and the lab is periodically rebuilt from scratch.
- With two machines there is **one k3s server and one agent**. The control plane is a single point of failure, which is accepted for a homelab. etcd HA would need three server nodes.
