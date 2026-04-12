# Geth Helm Chart

Helm chart for deploying Ethereum nodes (Geth) on Kubernetes.

## Overview

This chart deploys a Geth node with configurable network settings, persistent storage, and service discovery.

## Prerequisites

- Kubernetes cluster
- Helm 3+
- Sufficient storage capacity for blockchain data

## Installation

```bash
# Deploy to mainnet
helm install geth-node ./geth-node -f geth-node/values.mainnet.yaml

# Deploy to local network
helm install geth-node ./geth-node -f geth-node/values.local.yaml

# Deploy to GKE
helm install geth-node ./geth-node -f geth-node/values.gke.yaml
```

## Configuration

Values files available:
- `values.yaml` - Default configuration
- `values.mainnet.yaml` - Mainnet settings
- `values.local.yaml` - Local network settings
- `values.gke.yaml` - Google Kubernetes Engine settings

## Chart Structure

- `templates/` - Kubernetes resource templates
  - `statefulset.yaml` - Geth node StatefulSet
  - `service.yaml` - Service definition
  - `jwt-secret.yaml` - JWT authentication
  - `serviceaccount.yaml` - RBAC configuration
- `charts/` - Dependencies
- `infra/` - Infrastructure setup scripts

## RBAC

RBAC configurations available for:
- Mainnet: `infra/helm-deployer-rbac-mainnet.yaml`
- Sepolia: `infra/helm-deployer-rbac-sepolia.yaml`

## Uninstall

```bash
helm uninstall geth-node
```
