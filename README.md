# gitops-lab




## Installer Operateur OCP4 ArgoCD

* Creer un projet ArgoCD

```shell
oc new-project argocd
```

* Argo CD Provioded by Argocd Community

Community Operators are operators which have not been vetted or verified by Red Hat. Community Operators should be used with caution because their stability is unknown. Red Hat provides no support for Community Operators.

* Deployer 

## Vérifier si nécessaire
```shell
oc adm policy add-cluster-role-to-user cluster-admin -z argocd-application-controller -n argocd
```

## En prerequis il faut créer le projet de l'application
oc new-project reverse-words


## Ajouter le repo-git
https://github.com/Gigilamalice/lab-ocp4-argocd.git

## Ajouter le cluster
https://kubernetes.default.svc

## 
