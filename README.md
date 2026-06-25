# k8s-gitops-practice

GitOps practice repository for Kubernetes add-ons managed by Argo CD.

## Prometheus Stack

This repo includes a Helm wrapper chart for
`prometheus-community/kube-prometheus-stack`.

```text
charts/prometheus-stack
argocd/applications/prometheus-stack.yaml
```

Before applying the Argo CD `Application`, replace the placeholder below with
the Git repository URL that you registered in Argo CD.

```yaml
repoURL: REPLACE_WITH_YOUR_REGISTERED_GIT_REPO_URL
```

Local validation commands:

```sh
helm dependency build charts/prometheus-stack
helm lint charts/prometheus-stack
helm template prometheus-stack charts/prometheus-stack --namespace monitoring
```

Apply the Argo CD application when you are ready:

```sh
kubectl apply -f argocd/applications/prometheus-stack.yaml
```

The application installs into the `monitoring` namespace and uses
`CreateNamespace=true`.
