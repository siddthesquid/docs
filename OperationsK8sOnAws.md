# Operations K8S on AWS

- [Operations K8S on AWS](#operations-k8s-on-aws)
  - [Objective](#objective)
    - [Completion Test](#completion-test)
    - [Resources](#resources)
  - [Setup Guide](#setup-guide)
    - [Installation](#installation)
    - [Deployment files](#deployment-files)
    - [Create Kops Cluster](#create-kops-cluster)
    - [Deploy Grafana](#deploy-grafana)
    - [Deploy Prometheus](#deploy-prometheus)
    - [Deploy Jenkins](#deploy-jenkins)
    - [Deploy ArgoCD](#deploy-argocd)
  - [Extra Stuff](#extra-stuff)
    - [Basic Jenkins Libraries](#basic-jenkins-libraries)
    - [Create Monitoring Dashboards](#create-monitoring-dashboards)
    - [Testing](#testing)

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
  - [Getting Started with kOps on AWS](https://kops.sigs.k8s.io/getting_started/aws/)
- Terraform
  - [Local installation](https://learn.hashicorp.com/tutorials/terraform/install-cli)
- AWS
  - [Local installation (AWS CLI)](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
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

Installation guides should be linked above in the [Resources](#resources) section.

### Deployment files

Much of our configuration will live in code as much as securely possible.

- [`ops-infra`](https://github.com/siddthesquid/ops-infra) - mostly Terraform and kops-configured Terraform yamls
- [`ops-deploy`](https://github.com/siddthesquid/ops-deploy) - manifest files for K8s and other controllers/operators

```sh
git clone git@github.com:siddthesquid/ops-infra.git
git clone git@github.com:siddthesquid/ops-deploy.git
```

### Create Kops Cluster

1. Prepare your environment.

   We first need to `cd` into our `ops-infra` directory and set the environment variables

   ```sh
   cp .env.example .env # Fill out environment variables under Initialize
   . .env
   ```

2. Download your AWS credentials for terraform to use, and then run

   ```sh
   aws configure
   ```

   using `us-east-1` as the region.

3. Create an S3 bucket for the Terraform state.

   ```sh
   aws s3api create-bucket \
   --bucket $TERRAFORM_S3_BUCKET \
   --region $TERRAFORM_S3_REGION
   ```

4. Next, we'll set up IAM for kops. Within `ops-infra`, we need to run the following.

   ```sh
   git checkout 01-kops-init
   terraform init
   terraform apply
   ```

### Deploy Grafana

### Deploy Prometheus

### Deploy Jenkins

### Deploy ArgoCD

## Extra Stuff

### Basic Jenkins Libraries

### Create Monitoring Dashboards

### Testing
