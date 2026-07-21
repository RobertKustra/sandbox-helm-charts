# sandbox-helm-charts

Shared Helm charts for the Sandbox platform.

## Structure

- charts/sandbox-nginx/ - example application chart used by Flux
- charts/redis/ - Redis chart used by Flux for in-cluster Redis deployments

## Workflow

1. Update or add a chart here.
2. Commit and push the changes.
3. Reference the chart from the cluster configuration repository.
