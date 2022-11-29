1. kubectl --namespace argocd apply -filename https://raw.githubusercontent.com/argoproj-labs/argocd-image-updater/stable/manifests/install.yaml

2. kubectl --namespace argocd logs --selector app.kubernetes.io/name=argocd-image-updater

3. kubectl --namespace argocd logs \
    --selector app.kubernetes.io/name=argocd-image-updater \
    --follow


5. kubectl port-forward -n argocd svc/argocd-server 8889:443
Get a password : ``` kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo```





helm install my-argo-cd argo/argo-cd --version 4.5.8

```
vovka@DESKTOP-9JUS0U9:~/education/learn-terraform-provision-gke-cluster/argohelm$ helm install my-argo-cd argo/argo-cd --version 4.5.8
NAME: my-argo-cd
LAST DEPLOYED: Tue Nov 29 14:48:44 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
In order to access the server UI you have the following options:

1. kubectl port-forward service/my-argo-cd-argocd-server -n default 8080:443

    and then open the browser on http://localhost:8080 and accept the certificate

2. enable ingress in the values file `server.ingress.enabled` and either
      - Add the annotation for ssl passthrough: https://github.com/argoproj/argo-cd/blob/master/docs/operator-manual/ingress.md#option-1-ssl-passthrough
      - Add the `--insecure` flag to `server.extraArgs` in the values file and terminate SSL at your ingress: https://github.com/argoproj/argo-cd/blob/master/docs/operator-manual/ingress.md#option-2-multiple-ingress-objects-and-hosts


After reaching the UI the first time you can login with username: admin and the random password generated during the installation. You can find the password by running:

kubectl -n default get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

(You should delete the initial secret afterwards as suggested by the Getting Started Guide: https://github.com/argoproj/argo-cd/blob/master/docs/getting_started.md#4-login-using-the-cli)

```