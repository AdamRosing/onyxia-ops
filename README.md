kubectl create namespace argocd

kubectl apply -n argocd --server-side --force-conflicts `
  -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

  kubectl apply -f .\argocd\bootstrap.yaml