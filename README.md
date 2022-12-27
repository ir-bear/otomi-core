<h1 align="center">
  <img src="https://otomi.io/img/otomi-logo.svg" width="224px"/><br/>
  Self-hosted PaaS for Kubernetes
</h1>

<p align="center">
  <a href="https://github.com/redkubes/otomi-core/releases/"><img alt="Releases" src="https://img.shields.io/github/v/release/redkubes/otomi-core" /></a>
  <a href="https://hub.docker.com/r/otomi/core"><img alt="Docker pulls" src="https://img.shields.io/docker/pulls/otomi/core" /></a>
  <a href="https://img.shields.io/github/workflow/status/redkubes/otomi-core/Build%20and%20publish%20Docker"><img alt="Build status" src="https://img.shields.io/github/actions/workflow/status/redkubes/otomi-core/main.yml?branch=main" /></a>
  <a href="https://img.shields.io/github/last-commit/redkubes/otomi-core"><img alt="Last commit" src="https://img.shields.io/github/last-commit/redkubes/otomi-core" /></a>
  <a href="https://img.shields.io/crates/l/ap"><img alt="License" src="https://img.shields.io/crates/l/ap" /></a>
  <a href="https://img.shields.io/badge/contributions-welcome-orange.svg"><img alt="Contributions" src="https://img.shields.io/badge/contributions-welcome-orange.svg" /></a>
  <a href="http://otomi.io/"><img src="https://img.shields.io/website-up-down-green-red/http/shields.io.svg" alt="Website otomi.io"></a>
  <a href="https://join.slack.com/t/otomi/shared_invite/zt-1axa4vima-E~LHN36nbLR~ay5r5pGq9A"><img src="https://img.shields.io/badge/slack--channel-blue?logo=slack"></a>
  <a href="https://twitter.com/RedKubes"><img src="https://img.shields.io/static/v1?label=Twitter&message=Follow&color=1DA1F2" alt="Follow us on Twitter"></a>
  <a href="https://www.facebook.com/groups/otomiusers"><img src="https://img.shields.io/static/v1?label=Facebook&message=Join group&color=1877F2" alt="Join Facebook group"></a>
</p>

**Otomi** is a stack of integrated Kubernetes applications combined with automation and self-service. Otomi can be installed on any Kubernetes cluster, offering a multi and hybrid platform experience out-of-the-box. No more re-inventing the wheel when building and maintaining your own Kubernetes based (internal developer) platform or bespoke stack.

<p align="center"><img src="https://github.com/redkubes/otomi-core/blob/main/docs/img/otomi-apps.png/?raw=true" width="100%" align="center" alt="Otomi integrated applications"></p>

## Otomi helps 

**Developers** - To focus on their apps only
* Deploy containerized apps without writing any YAML manifests
* Get a standardized set of observalitity tools
* Store images in a private registry
* Build and run custom CI pipelines
* Configure ingress for deployed apps
* Manage your own secrets

**Platform & Operations teams** - To set up and manage production-ready Kubernetes-based platforms
* Skip the Day-0 and Day-1 effort and minimize Day-2 operations
* Avoid creating and maintaining multiple bespoke K8s stacks
* Onboard development teams on shared clusters in a comprehensive multi-tenant setup
* Get all the required K8s apps in an integrated way
* Ensure governance with security policies
* Implement zero-trust networking with east-west and north-south network control
* Make development teams self-serving
* Change the desired state of the platform based on Configuration-as-Code
* Support multi and hybrid cloud use cases
* Offer a standardized set of tools to all development teams

## Getting started

### Helm

To install Otomi using Helm, make sure to have a K8s cluster up and running with at least:

- Version `1.18` up to `1.23`
- A node pool with **6 vCPU** and **8GB+ RAM** (more is advised!)
- Calico CNI installed (or any other CNI that supports K8s network policies)

When using the `custom` provider, make sure the K8s LoadBalancer Service created by `Otomi` can obtain an external accessible IP address (using a cloud load balancer or MetalLB).

Add the Helm repository:

```bash
helm repo add otomi https://otomi.io/otomi-core \
helm repo update
```

and then install the Helm chart:

```bash
helm install otomi otomi/otomi \
--set cluster.k8sVersion=$VERSION \ # 1.19, 1.20, 1.21, 1.22 and 1.23 are supported
--set cluster.name=$CLUSTERNAME \
--set cluster.provider=$PROVIDER # use 'azure', 'aws', 'google', 'digitalocean', 'ovh', 'vultr', or 'custom' for any other cloud or onprem K8s
```

When the installer job is completed, follow the [activation steps](https://otomi.io/docs/installation/activation/).

## Integrated K8s applications

Otomi installs, configures, integrates and automates all of your favorite K8s apps:

- [Istio](https://github.com/istio/istio): The service mesh framework with end-to-end transit encryption
- [Velero](https://github.com/vmware-tanzu/velero): Back up and restore your Kubernetes cluster resources and persistent volumes
- [Argo CD](https://github.com/argoproj/argo-cd): Declarative continuous deployment
- [KubeClarity](https://github.com/openclarity/kubeclarity): Detect vulnerabilities of container images
- [Knative](https://github.com/knative/serving): Deploy and manage serverless workloads
- [Prometheus](https://github.com/prometheus/prometheus): Collecting container application metrics
- [Grafana](https://github.com/grafana/grafana): Query and visualize metrics
- [Loki](https://github.com/grafana/loki): Collecting container application logs
- [Harbor](https://github.com/goharbor/harbor): Container image registry with role-based access control, image scanning, and image signing
- [HashiCorp Vault](https://github.com/hashicorp/vault): Manage Secrets and Protect Sensitive Data
- [Kubeapps](https://github.com/vmware-tanzu/kubeapps): Launching and managing applications on Kubernetes
- [Keycloak](https://github.com/keycloak/keycloak): Identity and access management for modern applications and services
- [OPA/Gatekeeper](https://github.com/open-policy-agent/opa): Policy-based control for cloud-native environments
- [Cert-Manager](https://github.com/cert-manager/cert-manager): Add certificates and certificate issuers as resource types in Kubernetes clusters
- [Jaeger](https://github.com/jaegertracing/jaeger): End-to-end distributed tracing and monitor for complex distributed systems
- [Kiali](https://github.com/kiali/kiali): Observe Istio service mesh relations and connections
- [External DNS](https://github.com/kubernetes-sigs/external-dns): Synchronize exposed ingresses with DNS providers
- [Drone](https://github.com/harness/drone): Continuous integration platform built on Docker
- [Gitea](https://github.com/go-gitea/gitea): Self-hosted Git service
- [Nginx Ingress Controller](https://github.com/kubernetes/ingress-nginx): Ingress controller for Kubernetes
- [Minio](https://github.com/minio/minio): High performance Object Storage compatible with Amazon S3 cloud storage service

## Otomi Features

<p align="center"><img src="https://github.com/redkubes/otomi-core/blob/main/docs/img/otomi-features.png/?raw=true" width="100%" align="center" alt="Otomi features"></p>

- [x] Drag and drop apps to create your own preferred suite
- [x] GitOps out-of-the-box
- [x] Advanced ingress architecture with self-service
- [x] Configuration validation
- [x] Configure network policies for internal ingress and external egress
- [x] Deploy workloads without writing any YAML
- [x] Create and manage secrets in Vault and use them in workloads
- [x] Role-based access to all integrated applications
- [x] Enforce Pod security policies
- [x] Comprehensive multi-tenant setup
- [x] Automation tasks
- [x] Expose services on multiple (public/private) networks
- [x] SOPS/KMS for encryption of sensitive configuration values
- [x] BYO IdP, DNS and/or CA

## Otomi Projects

Otomi consists out of the following projects:

- Otomi Core (this project): The heart of Otomi
- [Otomi Tasks](https://github.com/redkubes/otomi-tasks): Autonomous jobs orchestrated by Otomi Core
- [Otomi API](https://hub.docker.com/repository/docker/otomi/api): The brain of Otomi, handling console input and talking to Otomi Core
- [Otomi Console](https://hub.docker.com/repository/docker/otomi/console): The UI of Otomi for admins and teams, talking to Otomi API
- [Otomi Clients](https://github.com/redkubes/otomi-clients): Factory to build and publish openapi clients used in Otomi Tasks

## Documentation

Check out the [dev docs index](./docs/README.md) for developer documentation or go to [otomi.io](https://otomi.io) for more detailed documentation.

## Contribution

If you wish to contribute please read our [Contributor Code of Conduct](https://otomi.io/community/code-of-conduct) and [Contribution Guidelines](https://otomi.io/community/get-involved).

If you want to say **thank you** or/and support the active development of Otomi:

- [Star](https://github.com/redkubes/otomi-core) the Otomi project on Github
- Feel free to write articles about the project on [dev.to](https://dev.to/), [medium](https://medium.com/) or on your personal blog and share your experiences

This project exists thanks to all the people who have contributed

<a href="https://github.com/redkubes/otomi-core/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=redkubes/otomi-core" />
</a>

## License

Otomi is licensed under the [Apache 2.0 License](https://github.com/redkubes/otomi-core/blob/main/LICENSE).