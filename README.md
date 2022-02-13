# GitOps

Using Kustomize and ArgoCD to manage deployments via GitOps


Resources
- [Kustomize](https://kustomize.io/)
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/)

# Installation

1. Install argoCD in your cluster: `kustomize build argocd | kubectl apply -f -`
2. Access ArgoCD UI and create hello-world application

### Tips and Tricks

Access ArgoCD UI
- local: `kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'`
- Azure: `kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'`
- Port Forwarding: `kubectl port-forward svc/argocd-server -n argocd 8080:443`

Access admin password
- `kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
