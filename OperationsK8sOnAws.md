# Operations K8S on AWS

- [Operations K8S on AWS](#operations-k8s-on-aws)
  - [Objective](#objective)
    - [Completion Test](#completion-test)
    - [Resources](#resources)
  - [Setup Guide](#setup-guide)
    - [Installation](#installation)

## Objective

The goal of this document is to help set up a general purpose operational Kubernetes cluster on AWS along with any other build related infrastructure. Ultimately, this document should assist with installing the following:

- Kops-assisted Terraform deployment of AWS
- Jenkins
- Custom Jenkins functions
- Prometheus/Grafana for cluster and application monitoring
- ArgoCD
- Code Artifact
- Package management adapters
  - Docker
  - npm
  - maven
  - pip?
  - public, private, and hosted (CodeArtifact) options

### Completion Test

By the end of this document, we'll test out this code by making a seperate repo with a maven package and ensuring that updates to that repo result in the maven repository getting built, tested, and pushed to our private AWS CodeArtifact.

Additionally, we should also have authorized access to the Jenkins, monitoring, and Argo dashboards.

ArgoCD won't be tested as part of this.

### Resources

- Go
  - [Local installation](https://go.dev/doc/install)
- kubectl
  - [Local installation](https://kubernetes.io/docs/tasks/tools/)
- Kops
  - [Local installation](https://kops.sigs.k8s.io/getting_started/install/)
- Terraform
  - [Local installation](https://learn.hashicorp.com/tutorials/terraform/install-cli)
- AWS
- Jenkins
- Prometheus
- Grafana
- ArgoCD

## Setup Guide

### Installation

Locally install the following:

- go
- kubectl
- kops
- terraform
- awscli

###
