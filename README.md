# sandbox-helm-charts

Shared Helm charts for the Sandbox platform.

## Structure

- charts/sandbox-nginx/ - example application chart used by Flux
- charts/sandbox-redis/ - Redis chart used by Flux for in-cluster Redis deployments
- charts/sandbox-vllm/ - vLLM inference chart with post-install/post-upgrade smoke test hook

## Workflow

1. Update or add a chart here.
2. Commit and push the changes.
3. Reference the chart from the cluster configuration repository.

## Flux reconcile commands

After pushing chart changes, trigger Flux to refresh sources and apply updated HelmRelease manifests.

```bash
# Reconcile GitRepository sources
flux reconcile source git sandbox-helm-charts -n flux-system
flux reconcile source git sandbox-cluster-config -n flux-system

# Reconcile main cluster kustomization
flux reconcile kustomization sandbox-cluster-config -n flux-system --with-source

# Optional: reconcile env values source and selected env overlay
flux reconcile source git sandbox-env-values -n flux-system
flux reconcile kustomization sandbox-env-values-dev -n flux-system --with-source
```
