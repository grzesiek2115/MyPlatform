# My DevOps engineering platform


## Bootstrapping k8s cluster

- Look at `kind-cluster.yaml`

## Bootstrapping argocd on k8s cluster

- Take from `https://github.com/argoproj/argoproj-deployments/blob/master/argocd/kustomization.yaml`, the kustomization.yaml and resources/namespace.yaml
- `kustomize build . | kubectl apply -f -` run it in kustomization.yaml dir or `k apply -k . --server-side`
- `k get po -n argocd`
- To port-forward argocd to local browser, use this command `k port-forward svc/argocd-server -n argocd 8080:80`
- To decode admin password for argocd UI, use `k get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d`
- Then please run `k apply -f argocd-bootstrap.yaml -n argocd`
