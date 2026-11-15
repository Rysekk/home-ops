# ansible

Prepares the Ubuntu nodes for k3s. Run every command from this folder (`ansible/`), so that `ansible.cfg` is picked up.

## Setup

`source .venv/bin/activate`

```sh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt                                      # ansible-core + ansible-lint, pinned
ansible-galaxy collection install -r requirements.yml -p collections # ansible.posix, community.general
```

The nodes are reached by their SSH aliases (`cp-01`, `worker-01`) from `~/.ssh/config`, with key auth and a user that can `sudo`. Test it:

```sh
ansible all -m ansible.builtin.ping
```

## Run

```sh
ansible-playbook playbooks/baseline.yml --check --diff   # dry run: show what would change
ansible-playbook playbooks/baseline.yml                  # apply
```

## Layout

| Path | Content |
|------|---------|
| `inventory/homelab.yml` | Hosts and groups: `k3s_server` (`cp-01`), `k3s_agent` (`worker-01`) |
| `playbooks/` | Entry points: which roles run on which hosts |
| `roles/baseline/` | Node prerequisites for Kubernetes, applied to all nodes |
| `requirements.txt` | Python tooling for the control node |
| `requirements.yml` | Ansible collections, installed into `collections/` (gitignored) |

## Roles

### baseline

| Task file | What it does |
|-----------|--------------|
| `kernel.yml` | Loads `overlay` and `br_netfilter` now and at boot, sets the forwarding and bridge sysctls in `/etc/sysctl.d/90-kubernetes.conf` |
| `swap.yml` | Turns swap off, removes it from `/etc/fstab` and deletes the swap file |
| `time.yml` | check the chrony package is installed, if not install it and check the service is started and enable |

Variables and their defaults are in `roles/baseline/defaults/main.yml`.

## Lint

```sh
ansible-lint   # production profile, see .ansible-lint
```

The same check runs in CI on every pull request that touches `ansible/`.
