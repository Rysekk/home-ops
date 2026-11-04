# Apps I write ship as Helm charts published to ghcr

Each app repo publishes a versioned Helm chart as an OCI artifact on ghcr.io, signed with cosign like the image. `home-ops` pins the chart version and holds the values for each cluster, including the image digest. A Kustomize base referenced by git URL was the alternative. It is simpler, but it has no versioned artifact, and every third-party app in `home-ops` is Helm anyway.
