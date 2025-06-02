# Flask-GLAction-Argo
Learning Gitlab actions and ArgoCD

## What does this repo do ?

This is just a simple project to try out Github Actions. It also has a directory called manifests that hold K8S yaml file to deploy the docker image in a cluster.

app.py - simple python webservice listening to port 5000

The Github Actions will: 
* Check the linting of the code
* Docker build
* Docker push to docker hub
* Update the manifests/deployment.yaml file with the new docker image tag

The project also contains a yaml file to deploy an application to Argo which will have this repo/manifest directory as the source.