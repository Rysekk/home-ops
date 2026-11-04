# k3s on Ubuntu 26.04, provisioned by Ansible, with Talos deferred

Homelab nodes run Ubuntu 26.04 LTS (Server, 26.04.1 or later) with k3s, installed and configured from `ansible/`. I chose a general-purpose distro over Talos Linux because shell access to the nodes is the point: debugging cgroups, OOM, I/O and networking down to the Linux mechanism is the main thing I want to learn, and Ansible on real Linux is the more transferable skill. Talos (immutable, API-only, no configuration drift) is the leading alternative in the home-ops community. It stays a candidate for a later, documented migration.

## Consequences

- Configuration drift is possible because nodes are mutable. The mitigation is that every change goes through Ansible and the lab is periodically rebuilt from scratch.
- With two machines there is **one k3s server and one agent**. The control plane is a single point of failure, which is accepted for a homelab. etcd HA would need three server nodes.
- 26.04 rather than 24.04: k3s v1.37 is validated on both, and 26.04.1 is past the first point release. It gives support until about 2031 instead of about 2029 and a 7.0 kernel, which is comfortably above Cilium's minimum. Since the lab is rebuilt from Ansible anyway, starting on the newer LTS avoids an in-place release upgrade later.
- 26.04 ships `sudo-rs` and the Rust coreutils (uutils) by default. Ansible modules or roles that rely on GNU-specific behaviour may need the classic `sudo` / `coreutils` packages, and most community roles were written for 22.04 or 24.04.
