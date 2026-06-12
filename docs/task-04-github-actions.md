# 🚀 Task 04 - GitHub Actions CI Pipeline

## 🎯 Objective

Implement a production-style CI pipeline using GitHub Actions.

The pipeline will automatically validate application code, perform security scanning, build a Docker image, and publish the image to Docker Hub.

## 📖 Background

The CI pipeline validates application quality and packaging before deployment configuration is synchronized by the GitOps platform.

## 🏗️ Architecture Diagram

![Task 04 - GitHub Actions CI Pipeline Diagram](../diagrams/task-04-github-actions-diagram.png)

This diagram summarizes the workflow and technical scope for task 04 - github actions ci pipeline.

## 📋 Prerequisites

* Sample microservice repository available.
* GitHub Actions enabled.
* Docker Hub repository available.
* Docker Hub credentials configured as GitHub secrets.

## ⚙️ Implementation Steps

### Step 1: Create GitHub Actions Workflow

A GitHub Actions workflow was implemented to automate application validation, security scanning, Docker image creation, container image scanning, and Docker Hub publication.

The workflow executes on repository changes and provides repeatable CI validation before application deployment through the GitOps platform.

### Step 2: Run Build, Test, and Filesystem Security Scan

The pipeline validates the application source code by installing dependencies, executing the build and test stages, and running a Trivy filesystem scan against the repository contents.

This stage provides early feedback for application correctness and source-level vulnerability detection before container image creation.

#### Screenshot Evidence: Build, Test, and Trivy Filesystem Scan Completion

The workflow execution evidence confirms that the CI job completed successfully, including build and test validation and the Trivy filesystem scan stage.

![Build, Test, and Trivy Filesystem Scan Completion](../screenshots/task-04-github-actions/task-04-build-test-scan-success.png)

Caption: Build and test stage completion with Trivy filesystem scan execution

### Step 3: Build, Scan, and Publish Docker Image

After source validation completed successfully, the workflow built the Docker image, scanned the resulting image with Trivy, authenticated to Docker Hub, and pushed the image to the remote registry.

This stage confirms that the application can be packaged consistently and published for downstream GitOps deployment workflows.

#### Screenshot Evidence: Docker Image Build, Trivy Image Scan, and Docker Hub Push

The Docker pipeline evidence confirms successful image build, Trivy container image scan execution, and image publication to Docker Hub.

![Docker Image Build, Trivy Image Scan, and Docker Hub Push](../screenshots/task-04-github-actions/task-04-docker-build-push-success.png)

Caption: Docker image build, Trivy image scan, and Docker image push to Docker Hub

### Step 4: Validate Docker Hub Repository Tags

The Docker Hub repository was validated after the workflow completed to confirm that the published image tags were available for GitOps deployment references.

#### Screenshot Evidence: Docker Hub Repository Tags

The Docker Hub repository evidence confirms that the CI pipeline published image tags successfully and that the image is available from the container registry.

![Docker Hub Repository Tags](../screenshots/task-04-github-actions/task-04-dockerhub-image-tags.png)

Caption: Docker Hub repository tags published by the GitHub Actions workflow

## Pipeline Stages
1. Source Code Checkout
2. Node.js Environment Setup
3. Dependency Installation
4. Application Testing
5. Trivy Filesystem Security Scan
6. Docker Image Build
7. Trivy Container Image Scan
8. Docker Hub Authentication
9. Docker Image Publication

## Why This Pipeline?
The CI pipeline provides:

* Automated validation
* Security scanning
* Consistent image creation
* Repeatable deployments
* Reduced deployment risk

## ⚙️ Commands Executed

Pipeline commands are represented by the GitHub Actions workflow stages documented below, including build, test, Trivy scans, Docker build, and Docker push operations.

## ✅ Validation

The following validation checks were performed:

* GitHub Actions workflow execution completed successfully.
* Build and test stages completed successfully.
* Trivy filesystem scan executed successfully.
* Docker image build completed successfully.
* Trivy image scan executed successfully.
* Docker image push to Docker Hub completed successfully.
* Docker Hub repository tags were verified.

## 📸 Screenshots

### Task 04 Build Test Scan Success

![Task 04 Build Test Scan Success](../screenshots/task-04-github-actions/task-04-build-test-scan-success.png)

Caption: Task 04 CI pipeline, image build, scan, push, and Docker Hub validation evidence.

### Task 04 Docker Build Push Success

![Task 04 Docker Build Push Success](../screenshots/task-04-github-actions/task-04-docker-build-push-success.png)

Caption: Task 04 CI pipeline, image build, scan, push, and Docker Hub validation evidence.

### Task 04 Dockerhub Image Tags

![Task 04 Dockerhub Image Tags](../screenshots/task-04-github-actions/task-04-dockerhub-image-tags.png)

Caption: Task 04 CI pipeline, image build, scan, push, and Docker Hub validation evidence.

## 🎉 Key Outcomes

The GitHub Actions CI workflow completed successfully and published validated container images to Docker Hub.

## 📚 Lessons Learned

CI validation is most useful when build, test, security scanning, image creation, and registry publication are handled as one repeatable workflow.

Publishing validated images to Docker Hub creates a reliable handoff point for downstream GitOps deployment automation.

## 🏁 Conclusion

The Task 04 - GitHub Actions CI Pipeline phase is complete and validated with documented operational evidence.
