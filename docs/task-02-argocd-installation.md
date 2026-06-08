# Task 02 - ArgoCD Installation and Configuration

## Objective

Install and configure ArgoCD as the GitOps controller for the Kubernetes platform.

ArgoCD will continuously monitor the GitOps repository and synchronize Kubernetes resources automatically, enabling a declarative deployment workflow.

## Why ArgoCD?

ArgoCD provides:

* Continuous synchronization between Git and Kubernetes
* Automated deployment reconciliation
* Deployment visibility
* Rollback capabilities
* GitOps-based change management

## Implementation Steps

### Step 1: Prepare Platform Namespaces

Dedicated namespaces were created to provide logical separation between platform services and application workloads.

Namespaces created:

* argocd
* monitoring
* dev
* staging
* prod

Command used:

```bash
kubectl create namespace argocd
kubectl create namespace monitoring
kubectl create namespace dev
kubectl create namespace staging
kubectl create namespace prod
```

Validation:

```bash
kubectl get ns
```

All namespaces were successfully created and reached the Active state.

#### Screenshot Evidence: Platform Namespace Preparation

The namespace validation confirmed that the platform, monitoring, and application environment namespaces were created successfully.

![Platform Namespace Preparation](../screenshots/task-02-argocd/task-02-platform-namespaces.png)

Caption: Platform Namespace Preparation

### Step 2: Install ArgoCD

ArgoCD was installed into the dedicated `argocd` namespace using the official installation manifest.

Command used:

```bash
kubectl apply -n argocd \
-f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Installed components:

* ArgoCD Server
* ArgoCD Repository Server
* ArgoCD Application Controller
* ArgoCD ApplicationSet Controller
* ArgoCD Notifications Controller
* ArgoCD Redis
* ArgoCD Dex Server

Validation command:

```bash
kubectl get pods -n argocd
```

All ArgoCD components successfully reached the Running state.

#### Screenshot Evidence: ArgoCD Components Running Successfully

The ArgoCD pod validation confirmed that all controller, server, repository, Redis, Dex, ApplicationSet, and notification components were running in the `argocd` namespace.

![ArgoCD Components Running Successfully](../screenshots/task-02-argocd/task-02-argocd-components-running.png)

Caption: ArgoCD Components Running Successfully

## Validation

## Validation

The following validation checks were performed:

### Namespace Validation

```bash
kubectl get ns
```

Verified namespaces:

* argocd
* monitoring
* dev
* staging
* prod

### ArgoCD Component Validation

```bash
kubectl get pods -n argocd
```

Verified:

* argocd-server
* argocd-repo-server
* argocd-application-controller
* argocd-applicationset-controller
* argocd-dex-server
* argocd-redis
* argocd-notifications-controller

All components reached the Running state.

### ArgoCD UI Validation

Port forwarding was established:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

The ArgoCD web interface was successfully accessed through:

```text
https://localhost:8080
```

Authentication using the initial admin credentials was successful and the dashboard loaded correctly.

#### Screenshot Evidence: ArgoCD Dashboard Access Validation

The dashboard validation confirmed that the ArgoCD UI was reachable through the local port-forward and that authentication completed successfully.

![ArgoCD Dashboard Access Validation](../screenshots/task-02-argocd/task-02-argocd-dashboard-login.png)

Caption: ArgoCD Dashboard Access Validation

## Screenshots

The screenshots embedded above provide validation evidence for namespace preparation, ArgoCD component readiness, and dashboard access.

## Lessons Learned

To be completed during implementation.
