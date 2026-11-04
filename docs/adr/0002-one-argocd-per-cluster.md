# One Argo CD per cluster (pull model)

Each cluster runs its own Argo CD and reconciles `clusters/<name>/` from `home-ops`. A hub-and-spoke setup (an Argo CD on homelab pushing to oci over the VPN) was rejected because prod must keep reconciling when the house loses power or internet. Hub-and-spoke only pays off with many clusters.
