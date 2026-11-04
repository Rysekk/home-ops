# No inbound ports at home

Nothing is exposed through a router port-forward:

- **Public HTTP** goes through a Cloudflare Tunnel (outbound only) to the **external gateway**, with Cloudflare Access or a self-hosted IdP in front.
- **Private and admin access** goes through Tailscale to the **internal gateway**, with ACLs kept as code in this repo.
- **Game servers** (raw TCP/UDP, which Cloudflare's free plan cannot tunnel) go through playit.gg. A self-hosted relay (Pangolin) on a separate VM is a later project.

The ISP router (Livebox 7) cannot segment the LAN. Until a lab router exists, isolation relies on having no inbound ports plus Cilium egress policies that block public namespaces from the home LAN.

## Considered Options

- **Raw WireGuard** for private access: manual peers and no NAT traversal. It is fine for one site-to-site link, but tedious for a mesh of devices.
- **NetBird / Headscale**: fully self-hostable equivalents of Tailscale and the fallback if the SaaS control plane becomes a problem.
- **Router port-forwards for games**: what most homelabbers do. Rejected because it exposes the home IP.
