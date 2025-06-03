# Simplek8s
Learning Gitlab actions and ArgoCD

## Install ArgoCD
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


## Install ImageUpdater from Helm
helm repo add argo https://argoproj.github.io/argo-helm
helm install my-argocd-image-updater argo/argocd-image-updater --version 0.12.2

## What does this directory do ?
This directory holds yaml file to create an ArgoCD application that monitors a public docker hub image for minor and patch version changes. As soon as it detects those changes, that image will be pulled and new pods will be created.
This also keep an eye at a public gitlab repo for changes and deploys pods based on them.

Note:  Ofcourse it is not safe to do follow this process in Production. 

### ArgoCD Write back approach

"argocd-image-updater.argoproj.io/write-back-method: git" 
can be used to write the image tag changes back to git and then ArgoCD will follow the usual process for identifying and applying git changes to K8s.

Make sure to add the necessary gitlab/github secret in ArgoCD namespace for ArgoCD process to authenticate and write the changes to git.
