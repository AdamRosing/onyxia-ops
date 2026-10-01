kubectl create namespace argocd

kubectl apply -n argocd --server-side --force-conflicts `
  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

  kubectl port-forward svc/argocd-server -n argocd 8080:443

  kubectl apply -f .\argocd\bootstrap.yaml

  $encoded = kubectl -n argocd get secret argocd-initial-admin-secret -o "jsonpath={.data.password}"
[Text.Encoding]::UTF8.GetString([Convert]::FromBase64String($encoded))