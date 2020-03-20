# gitops-lab

 * Formation:  https://learn.openshift.com/introduction/gitops-introduction/?extIdCarryOver=true&sc_cid=701f2000001Css5AAC
 


## Installer Operateur OCP4 ArgoCD

* Creer un projet ArgoCD

```shell
oc new-project argocd
```

* Argo CD Provioded by Argocd Community

Community Operators are operators which have not been vetted or verified by Red Hat. Community Operators should be used with caution because their stability is unknown. Red Hat provides no support for Community Operators.

* Creer une instance Argo CD

```shell
apiVersion: argoproj.io/v1alpha1
kind: ArgoCD
metadata:
  name: example-argocd
  namespace: argocd
spec: {}
```

* !!! A Vérifier si nécessaire !!!
```shell
oc adm policy add-cluster-role-to-user cluster-admin -z argocd-application-controller -n argocd
```

* En prerequis il faut créer le projet de l'application
```shell
oc new-project reverse-words
```
* Se connecter à l'application

https://example-argocd-server-argocd.apps.cluster-????.sandbox????.opentlc.c
User = admin
Password (nom du pod argocd-server) = example-argocd-server-5dbbc86f74-jvj8zom/settings/clusters

## Creer une application

* Ajouter le repo-git
https://github.com/Gigilamalice/lab-ocp4-argocd.git

* Ajouter le cluster
https://kubernetes.default.svc

* Creer l'application
```shell
argocd app create --project default --name reverse-words-app \
 --repo https://github.com/Gigilamalice/lab-ocp4-argocd.git \
 --path simple-app/reversewords_app/ \
 --dest-server https://kubernetes.default.svc \
 --dest-namespace reverse-words \
 --revision master --sync-policy automated
 ```
 

