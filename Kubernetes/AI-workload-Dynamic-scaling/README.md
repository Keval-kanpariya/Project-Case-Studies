# 🎯 Dynamic AI Workload Scaling on AWS EKS using Karpenter

Author: [Keval Kanpariya](https://techanek.com/author/keval/)  
Date: September 25, 2024  
Tech Stack: AWS, Kubernetes, Karpenter, GPU Workloads

---

## 🚀 Overview

In today’s AI-driven landscape, efficient resource management is key to optimizing both performance and cost. This project demonstrates how to achieve **dynamic GPU node provisioning** for AI workloads on AWS EKS using **Karpenter**, an open-source autoscaler.

Karpenter provisions nodes based on workload needs in real-time, ensuring that resources are used efficiently and unnecessary cloud costs are avoided—an ideal fit for **AI workloads with unpredictable GPU usage patterns**.

---

## 📌 Objectives

- Dynamically allocate GPU resources in response to AI workload demands
- Minimize cost by using spot instances and scaling down idle nodes
- Automatically integrate GPU-based EC2 nodes into EKS
- Use **Karpenter** as a scalable, intelligent provisioning solution

---

## 🛠️ Prerequisites

Ensure the following resources and configurations are in place:

- ✅ AWS CLI installed and configured
- ✅ Existing EKS cluster
- ✅ VPC, Subnets, and Security Groups configured
- ✅ IAM OIDC Provider for EKS service accounts
- ✅ Helm installed for Karpenter deployment

Set the following environment variables before proceeding:

```bash
export KARPENTER_NAMESPACE=kube-system
export CLUSTER_NAME=<cluster-name>
export AWS_PARTITION="aws"
export AWS_REGION="$(aws configure list | grep region | tr -s " " | cut -d" " -f3)"
export OIDC_ENDPOINT="$(aws eks describe-cluster --name "${CLUSTER_NAME}" --query "cluster.identity.oidc.issuer" --output text)"
export AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query 'Account' --output text)
export K8S_VERSION=1.30
export GPU_AMI_ID="$(aws ssm get-parameter --name /aws/service/eks/optimized-ami/${K8S_VERSION}/amazon-linux-2-gpu/recommended/image_id --query Parameter.Value --output text)"
