# home-ops

The GitOps repository that declares every cluster I run, the platform components on each of them, and the workloads they host.

## Repositories

**home-ops**:
This repository. It holds the desired state of every cluster. Argo CD only ever reads it.
_Avoid_: infra repo, config repo, homelab repo

**App repo**:
A repository for software I write. It contains the source code, the image build, and that app's deploy package (its Helm chart). It never decides where or which version runs.
_Avoid_: service repo, source repo

## Clusters and environments

**homelab**:
The cluster made of the two PCs at home. It hosts staging, the shared platform services, and experiments.
_Avoid_: lab, home cluster, dev

**oci**:
The single-node cluster on the Oracle Cloud VM. It hosts prod.
_Avoid_: cloud cluster, remote

**Prod**:
The trading-app instance that runs on **oci**.
_Avoid_: production cluster (prod is an environment, not a cluster)

**Staging**:
The trading-app instance that runs on **homelab**. Every new image lands here first.
_Avoid_: dev, preprod, test

**Promotion**:
Moving an image digest that has been validated on staging into prod's values through a reviewed pull request.
_Avoid_: deploy, release

## Contents of home-ops

**Infrastructure**:
A platform component that workloads depend on, such as networking, certificates, secrets, gateways or monitoring.
_Avoid_: add-on, system app, core

**App**:
A workload hosted for its own sake, whether I wrote it (trading-app) or a third party did (a game server).
_Avoid_: service, workload (when meaning this folder)

**Platform baseline**:
The set of infrastructure components and policies every cluster is expected to converge to.
_Avoid_: stack, standard

## Nodes

**Compute node**:
The homelab PC with 32 GB of RAM. It runs the control plane and the heavy workloads. Hostname: `cp-01`.
_Avoid_: master, main node

**Storage node**:
The homelab laptop with the 500 GB SSD. It holds bulk persistent data. Hostname: `worker-01`.
_Avoid_: NAS

## Exposure

**Internal gateway**:
The entry point for services that are reachable only through the private network (Tailscale) or the LAN.
_Avoid_: private ingress

**External gateway**:
The entry point for services published to the internet, reachable only through the Cloudflare Tunnel.
_Avoid_: public ingress, DMZ
