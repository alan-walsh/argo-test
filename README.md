# argo-test
Testing ArgoCD

## Gen3 ArgoCD Application

This repository contains an ArgoCD application deployment for [Gen3-Helm](https://github.com/uc-cdis/gen3-helm).

### Quick Deploy

To deploy the Gen3 application directly to your ArgoCD cluster:

```bash
kubectl apply -f gen3-application.yaml
```

### Helm Chart Approach

The `common1/` directory contains a Helm chart that generates the ArgoCD application:

```bash
# Install the application using Helm
helm install gen3-app ./common1

# Or generate the manifest
helm template gen3-app ./common1 > gen3-app-manifest.yaml
kubectl apply -f gen3-app-manifest.yaml
```

### Configuration

The application is configured to:
- Deploy Gen3 using the official [gen3-helm](https://github.com/uc-cdis/gen3-helm) chart
- Use custom values from this repository (`values/values.yaml` and `values/fence.yaml`)
- Deploy to the `default` namespace
- Enable automatic sync with self-healing

### Customization

You can customize the deployment by:
1. Modifying the values files in `common1/values/`
2. Updating the Helm chart values in `common1/values.yaml`
3. Editing the standalone application in `gen3-application.yaml`
