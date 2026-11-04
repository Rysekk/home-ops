# Cilium as CNI, Gateway API implementation and LoadBalancer IPAM

k3s is installed with flannel, Traefik, ServiceLB and its network-policy controller disabled. Cilium provides networking, NetworkPolicy enforcement, the Gateway API implementation (internal and external gateways) and LoadBalancer IPs through LB-IPAM with L2 announcements. One component replaces four, and it brings Hubble flow visibility. If the Cilium Gateway's limits are hit, Envoy Gateway is the planned replacement, and that switch gets its own ADR.

## Consequences

The baseline for public namespaces is default-deny NetworkPolicies, Pod Security Admission `restricted`, and no automounted service-account tokens.
