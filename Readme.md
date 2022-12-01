https://www.padok.fr/en/blog/argocd-image-updater#The_Helm_Umbrella_Charts

kubectl port-forward svc/argocd-server -n argocd 8080:443
Get a password : ``` kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo```