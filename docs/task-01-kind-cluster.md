# Task 01 - Local Kubernetes Platform Setup with Kind

## Objective

Provision a production-style local Kubernetes environment using Kind (Kubernetes in Docker) to serve as the foundational platform for GitOps deployment, observability, and security tooling.

## Why Kind?

Kind provides a lightweight, reproducible Kubernetes environment that runs entirely within Docker containers. It enables local platform engineering workflows without requiring cloud infrastructure.

For this project, Kind is used to simulate a multi-node Kubernetes cluster capable of hosting ArgoCD, Prometheus, Grafana, Alertmanager, and application workloads.

## Cluster Architecture

Control Plane Nodes:
1

Worker Nodes:
2

Total Nodes:
3

## Prerequisites

* Docker
* Kind
* kubectl
* Helm
* Terraform

## Implementation Steps

### Step 1: Verify Local Tooling

The following tools were verified before cluster provisioning:

* Kind v0.30.0
* kubectl v1.35.5
* Docker v29.5.3
* Helm v3.21.0
* Terraform v1.15.5

### Step 2: Create Kind Cluster Configuration

A custom Kind configuration file was created to provision a multi-node Kubernetes cluster consisting of:

* 1 Control Plane Node
* 2 Worker Nodes

### Step 3: Provision the Cluster

Cluster creation command:

```bash
kind create cluster \
  --name gitops-platform \
  --config kind/kind-cluster.yaml
```

### Step 4: Validate Cluster Health

Validation commands:

```bash
kubectl get nodes -o wide
kubectl get pods -A
docker ps
```

Validation confirmed:

* All nodes reached Ready state.
* Kubernetes system components were healthy.
* Worker nodes successfully joined the cluster.
* Networking and storage components initialized successfully.

## Validation

To be completed during implementation.

## Screenshots

To be completed during implementation.

## Lessons Learned

During initial cluster creation, worker nodes failed to join due to a Kubernetes node image version mismatch.

The cluster configuration was simplified to allow Kind to manage node image selection automatically, resulting in a successful multi-node cluster deployment.

This reinforced the importance of maintaining Kubernetes version consistency across cluster nodes.
