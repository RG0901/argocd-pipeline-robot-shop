# CI/CD Pipeline for Robot Shop (My Fork)

This repository contains my *custom CI/CD pipeline* built around a fork of the original **instana/robot-shop** project. The goal of this implementation is to showcase that *I personally designed and configured* a complete GitOps-driven CI/CD workflow using **GitHub Actions** and **ArgoCD**.

## 🚀 Overview

I extended the base Robot Shop microservices application by implementing a **fully automated CI/CD pipeline** that:

1. Builds and tests container images on every code push
2. Pushes artifacts to a container registry
3. Uses **ArgoCD (GitOps)** as the Continuous Deployment (CD) engine
4. Ensures Kubernetes manifests are automatically applied to the cluster

This setup demonstrates an end-to-end GitOps workflow where *Git is the source of truth* and ArgoCD *pulls and deploys* changes automatically. :contentReference[oaicite:1]{index=1}

---

## 🛠 What I Did (Step-By-Step)

### 1. Fork and Clone
- Forked the original **instana/robot-shop** repository to my GitHub account
- Cloned my fork locally to begin customization

---

### 2. Container Image CI (GitHub Actions)
- Created a `.github/workflows/ci.yml` pipeline
- Configured it to trigger on `push` events
- Pipeline:
  * Checks out code
  * Builds Docker images for each microservice
  * Pushes images to a container registry (e.g., Docker Hub, GHCR)
- This provides automated build/testing for every commit, enabling **Continuous Integration**. :contentReference[oaicite:2]{index=2}

---

### 3. Kubernetes Manifests / Helm
- Prepared Kubernetes manifests (or Helm charts) for Robot Shop services
- Ensured they reference dynamic image tags
- Committed these to a GitOps folder in the repo
- This enables declarative infrastructure defined as code

---

### 4. Install & Configure ArgoCD
- Installed ArgoCD into my Kubernetes cluster  
- Exposed the ArgoCD UI for access  
- Logged in and configured an ArgoCD *Application* pointing to my GitOps manifests  
- ArgoCD now continuously watches the Git repo and automatically deploys changes — this is the core GitOps CD loop. :contentReference[oaicite:3]{index=3}

---

### 5. GitOps Deployment Flow
With the pipeline complete:
1. Developer pushes code → GitHub Actions builds & pushes images
2. Kubernetes manifests in Git are updated with new image tag
3. ArgoCD *detects change* → syncs and deploys those resources
4. Robot Shop services update automatically in cluster

This pull-based model makes deployments fully automatic and *Git-centric*, eliminating manual `kubectl apply` steps. :contentReference[oaicite:4]{index=4}

---

## 📌 Highlights of What I Built

✅ Forked and adapted Robot Shop for CI/CD  
✅ Automated container builds using GitHub Actions  
✅ GitOps-style CD using ArgoCD  
✅ Declarative deployments with auto-sync on Git changes  
✅ Experience with modern DevOps tooling and cloud-native best practices

---

## 📁 Repo Structure (Example)

├── .github/
│ └── workflows/
│ └── ci.yml # CI pipeline workflow
├── k8s/
│ └── manifests/ # Kubernetes manifests for ArgoCD
├── services/ # Robot Shop microservices
└── README.md # (This file)

---

## 📫 Get Started

1. Clone this repo  
   `git clone https://github.com/<your-username>/robot-shop.git`

2. Configure GitHub Actions secrets (e.g., DOCKER_REG, USER, TOKEN)

3. Install ArgoCD in your Kubernetes cluster

4. Create an ArgoCD application pointing to the `k8s/` folder

5. Push changes and watch deployments auto-sync

---

## 🧠 Learning Outcomes

By doing this, I learned:

- How to wire GitHub with a real microservices project
- How to set up ArgoCD for GitOps CD
- How CI and CD workflows complement each other in Kubernetes environments
- How to maintain a Git-centric deployment model

---

Thank you for checking out my pipeline showcase! 🚀