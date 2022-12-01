https://www.padok.fr/en/blog/argocd-image-updater#The_Helm_Umbrella_Charts

kubectl port-forward svc/argocd-server -n argocd 8080:443
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo




helm package apps
helm repo add --username gitlab+deploy-token-1547805 --password SA_qtYcP2y9q-qhy68Zm myargo_registry https://gitlab.com/api/v4/projects/40594299/packages/helm/stable
helm repo list
helm cm-push Chart-task-01-0.1.0.tgz  myargo_registry 




 helm repo add --username gitlab+deploy-token-1547805 --password SA_qtYcP2y9q-qhy68Zm myargo_registry https://gitlab.com/api/v4/projects/40594299/packages/helm/stable


helm install prod-argo-application myargo_registry/Chart-task-01 -n argocd