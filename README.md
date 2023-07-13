# Viking

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.1.4.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.

## Docker Commnands
### Build Image
docker run -p 8080:80 viking:v1

### Run Container
 docker run --rm -it -d -p 8080:80 viking:v1

 ### Remove all stopped container
docker container prune

### list all containers
docker ps --all

### List docker images
docker images

### Delete docker image
docker rmi viking


## GC Commands
### Install the gcloud CLI
(New-Object Net.WebClient).DownloadFile("https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe", "$env:Temp\GoogleCloudSDKInstaller.exe")

& $env:Temp\GoogleCloudSDKInstaller.exe


### To set up authentication to Docker repositories in the region
gcloud auth configure-docker europe-west4-docker.pkg.dev


docker pull us-docker.pkg.dev/google-samples/containers/gke/hello-app:1.0

### Tag the image for the repository

 docker tag viking:v1 europe-west4-docker.pkg.dev/gcds-oht33885u6-2023/viking-infy/viking:latest

### Push image to the repository
 docker push europe-west4-docker.pkg.dev/gcds-oht33885u6-2023/viking-infy/viking:latest
    
### Pull image from repository
 docker pull europe-west4-docker.pkg.dev/gcds-oht33885u6-2023/viking-infy/viking:latest


 ## GKE Cluster
 ### Install the authentication plugin using the gcloud CLI 
   gcloud components install gke-gcloud-auth-plugin


### Create Cluster
gcloud container clusters create viking-cluster --enable-ip-alias --cluster-ipv4-cidr=10.0.0.0/20 --services-ipv4-cidr=10.4.0.0/19 --create-subnetwork=name=vikingsubnet2023,range=10.5.32.0/27 --default-max-pods-per-node=110 --region=europe-west4   --num-nodes 3

### Delete cluster
gcloud container clusters delete viking-cluster --region=europe-west4

### Get cluster credentials
gcloud container clusters get-credentials viking-cluster --region=europe-west4


## Setup Ingress controller
### Add the ingress-nginx repository
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

### Use Helm to deploy an NGINX ingress controller
helm install nginx-ingress ingress-nginx/ingress-nginx `
    --set controller.replicaCount=2 `
    --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux `
    --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux `
    --set controller.admissionWebhooks.patch.nodeSelector."beta\.kubernetes\.io/os"=linux

### Helm install
helm install  viking viking

### Helm Uninstall
helm uninstall viking
