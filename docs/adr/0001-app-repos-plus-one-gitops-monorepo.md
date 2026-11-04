# Split app repos from a single home-ops GitOps monorepo

Software I write lives in its own **app repo** (code, image build, CI, Helm chart). Everything about *what runs where* (cluster bootstrap, infrastructure, app values for each cluster, Terraform, Ansible) lives in a single `home-ops` repo that covers **every** cluster. Config and code change at different rates and for different reasons. Argo CD should only clone and react to config. Third-party apps (game servers, VPN…) are just folders in `home-ops` and never get their own repo.

## Considered Options

- **One repo for everything, code included**: the simplest option, but code commits pollute Argo's history and trigger reconciliation, and CI paths get tangled. This is how `low-latency-observability` works today.
- **One GitOps repo per cluster**: duplicates the shared infrastructure, and promotion then crosses repos.
- **App repo + home-ops monorepo** (chosen): the app-repo / config-repo split that enterprises use, kept to two kinds of repo, as homelabbers do.

## Consequences

- App CI no longer commits to its own repo. It bumps a digest in `home-ops` (see ADR-0006).
- `low-latency-observability` must eventually lose `deploy/terraform`, `deploy/argocd` and the cluster add-ons (see ADR-0011 for timing).
