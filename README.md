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