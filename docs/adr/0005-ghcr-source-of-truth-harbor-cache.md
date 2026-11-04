# ghcr.io is the image source of truth; Harbor is only a homelab cache

CI pushes images and charts to ghcr.io, and prod pulls from it directly. Harbor, when it is added, runs on homelab only as a pull-through cache (k3s `registries.yaml` mirrors fall back to the upstream registry). A self-hosted registry as the primary would make prod depend on a PC at home and would need GitHub Actions to reach the house. Since the app source is public, a private registry would also hide almost nothing.

## Consequences

Vulnerability scanning cannot rely on Harbor, which never sees prod's images. Scanning is layered instead: Trivy in CI as a gate, Trivy Operator in every cluster for CVEs published after the build, and Renovate for fixes.
