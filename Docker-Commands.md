

# Prerequisites
1. Docker Desktop
1. Install Nginx `kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.41.2/deploy/static/provider/cloud/deploy.yaml`.
    * This one did not work for me, but suppose to be latest `kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.0/deploy/static/provider/cloud/deploy.yaml`
1. Pull these two images.
   * `docker pull containerregistry.azurecr.io/aspnet-runtime:3.1.6`
   * `docker pull containerregistry.azurecr.io/dotnet-build:3.1.6`

# AZ Commands
1. Login to AKS cluster
   1. az account set --subscription DevOps-Dev-Test2
   1. az aks get-credentials --resource-group rgp-usw-icsp-test2-aks-kayaks --name aks-usw-icsp-test2-aks-kayaks
   1. az aks get-credentials --resource-group rgp-usw-ide-test2-aks-canoes --name aks-usw-ide-test2-aks-canoes
1. Login to ACR
   1. az login
   1. az acr login --name <container registry>

# Docker Commands (Draft)
1. Set-Alias -Name d -Value docker
1. Two ways to solve Nuget Config Auth Issue
    1. Add this to Dockerfile `ARG SYSTEM_ACCESSTOKEN=...`. Steps to create PAT token described in [Use personal access tokens](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page).
    1. Add below section to `Nuget.Config`
    ```
    <packageSourceCredentials>
      <Cloud.Platform>
        <add key="Username" value="<user name>" />
        <add key="ClearTextPassword" value="..." />
      </Cloud.Platform>
    </packageSourceCredentials>
    ```
1. 'docker build' command by Visual Studio. VS runs this command as part of build task.
   1. `docker build -f "Dockerfile" --force-rm -t helloworld:dev --target base  --label "com.microsoft.created-by=visual-studio" --label "com.microsoft.visual-studio.project-name=helloworld" "DI.AppCenter.LogProcessor"` - This was the command Visual Studio showed in `Container Tools` window.
   1. `docker build . -t di.appcenter.logprocessor.api:1.0` --> Here Dockerfile is present in current directory, create build with repository as `di.appcenter.logprocessor.api` and label as `1.0`.
   1. `docker build . -f source\DI.AppCenter.LogProcessor.Api\Dockerfile -t di.appcenter.logprocessor.api:1` - Make sure you build from place where Nuget config is placed.
   1. `docker build --tag prms .` - Build docker image with tag called prms
1. docker pull azurecr.io/dotnet-build:3.1.2
1. docker images --> List container images
1. docker image prune --> Remove all dangling images.
1. docker image prune -a --> If -a is specified, will also remove all images not referenced by any container.
1. docker image rm dc349298ea5a --> delete image by id
1. docker image rm webapplication1:dev --> delete image by referencing REPOSITORY and TAG.
1. docker rmi --force a5b814602eb1 --> remove by force
1. docker container ls --> List containers
1. docker image history <repository>:<tag>
1. docker system events
1. Docker push
   1. docker login docker-master.cdaas.oraclecloud.com
   1. docker push myimage:latest
1. docker run
   1. docker run docker run -e my_env_var="my_env_var_value" alpine:3.12
   1. docker run -i -t <REPOSITORY>:<TAG> sh
   1. docker run -i -t alpine:3.12 sh
   1. docker run -i -t alpine:3.12 ping google.com
   1. docker run -idt -p 16000:16000 --name fb ubuntu bash
   1. docker run --publish  8090:8090 alpine:3.12 --> Port forwarding from host to container
   1. docker run -v /HostPath:/ContainerPath  -it alpine:3.12  sh  --> Run and mount host directory path `/HostPath` as `/ContainerPath`. Any changes made in host directory is available to container directory when container is running.
1. Docker Exit Status
  1. docker ps -a  --> shows column for 'status'.
  1. docker ps -a | grep sas-test:latest --> Show only for images with name contains sas-test:latest.

# docker-compose
1. The `image:` keyword is used to specify the image from dockerhub for our mysql and nginx containers
1. Here is sample from docker portal that builds `web` using `Dockerfile` present in the `.` , pull Redis from Docker hub, and starts two services by command `docker compose up`.
```
version: "3.9"
services:
  web:
    build: .
    ports:
      - "8000:5000"
  redis:
    image: "redis:alpine"
```
