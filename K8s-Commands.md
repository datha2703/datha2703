

# Kubenates Services
1. ClusterIP - provides IP address and communication within the cluster.
1. NodePort - Allocates port, IP address to allow external caller to make call to Pod.
1. LoadBalancer - Balances load, exposes service to external caller, can be combined with cloud provider load balancer. ehind the scene, this service sets up NodePort and ClusterIP service. Nginx is type of loadbalancer.
1. ExternalName - sets up alias for external service. This acts as proxy for external service.
1. kubectl get ing --> view ingress services.
1. Port forwarding
 1. kubectl port-forward di-appcenter-logprocessor-api 8090:80
 1. kubectl port-forward deployment/di-appcenter-logprocessor-api 8090:80
 1. kubectl port-forward service/di-appcenter-logprocessor-api 8090:80
1. Cluster IP Services
  1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.ClusterIpService.yml  --dry-run=client --validate=true --> Only validates and dry run
  1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.ClusterIpService.yml --> Now `k exec di-appcenter-logprocessor-api-6fb5594f8b-2h5w6 -- curl http://di-appcenter-logprocessor-api-cluster-ip:8090/WeatherForecast` will get results from service.
1. NodePort Services
  1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.NodePort.yml
  1. Open browser and type http://localhost:31000/WeatherForecast
  1. kubectl delete -f .\DI.AppCenter.LogProcessor.Api.NodePort.yml --> delete nodeport
1. LoadBalancer Services
  1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.LoadBalancer.yml
  1. Open browser and type http://localhost/WeatherForecast
  1. kubectl delete -f .\DI.AppCenter.LogProcessor.Api.NodePort.yml --> delete nodeport

# Injecting Settings for Pods
1. Use ConfigMaps and Secrets, are shared across pods.
1. Types of config maps
 1. Store in file where file name is key , content can be json, xml etc.
 1. Provide on command line
 1. ConfigMap manifest as yaml, loaded as env variable or ConfigMap volume.
1. `kubectl apply -f .\DI.AppCenter.LogProcessor.Api.ConfigMap.yml` creates config map from file. Config map also created from env type of file and from command line.

# Useful kubectl Commands
1. Set-Alias -Name k -Value kubectl
1. kubectl version
1. kubectl cluster-info
1. kubectl get all
1. kubectl get services
1. kubectl run [container-name] --image=[image-name]
1. kubectl expose ...
1. kubectl create -f create-namespace.yml
1. k exec di-appcenter-logprocessor-api -it sh --> To get bash shell
1. kubectl logs [container-name]

# kubectl pods (Draft)
1. k describe pod di-appcenter-logprocessor-api
1. kubectl run di-appcenter-logprocessor-api --image=repo:label  --> this will create pod called 'di-appcenter-logprocessor-api' using container image 'repo:label'
1. kubectl port-forward di-appcenter-logprocessor-api 8090:80 --> where 8090 is external port and 80 is internal port. http://localhost:8090/WeatherForecast
1. kubectl delete pod di-appcenter-logprocessor-api
1. Pods have their own IP address
1. kubectl port-forward [pod] [ports]
1. kubectl get pods -->List all pods
1. kubectl port-forward pods\di-appcenter-logprocessor-api 8090:80 --> where 8090 is external port and 80 is internal port. http://localhost:8090/WeatherForecast
1. kubectl port-forward pod/di-appcenter-logprocessor-api-6fb5594f8b-5x442 8090:80 --> Magic number at the end of the pod name comes when replicas are setup.
1. kubectl create -f .\DI.AppCenter.LogProcessor.Api.Pod.yml --dry-run=client --validate=true  --> Only validates and dry run
1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.Pod.yml --> Creates pod
1. kubectl apply -f .\DI.AppCenter.LogProcessor.Api.Pod.yml --save-config --> Creates annotation, applies specific delta changes in yml
1. kubectl delete -f .\DI.AppCenter.LogProcessor.Api.Pod.yml

# kubectl deployments
1. kubectl create -f .\DI.AppCenter.LogProcessor.Api.Deploy.yml  --dry-run=client --validate=true  --> Only validates and dry run
1. kubectl get deployments
1. kubectl get deployments --show-labels
1. kubectl get deployments -l app=di-appcenter-logprocessor-api-app
1. kubectl scale deployments di-appcenter-logprocessor-api --replicas=2
kubectl scale deployments -f .\DI.AppCenter.LogProcessor.Api.Deploy.yml --replicas=2
1. kubectl scale deployments -f  --replicas=2
1. k describe deployment di-appcenter-logprocessor-api
1. kubectl port-forward deployment/di-appcenter-logprocessor-api 8090:80
1. k get deployment
1. k get deployments --show-labels
1. k scale -f DI.AppCenter.LogProcessor.Api.Deploy.yml --replicas=2
1. k delete -f DI.AppCenter.LogProcessor.Api.Deploy.yml

# kubectl namespace
1. Switch context `kubectl config use-context context-clxtwe5tvwq`
1. policyservicedev (root)/spectra/spectra-authorization_authz_alpha context-clxtwe5tvwq
1. policyservicedev (root)/spectra/spectra-authorization_authz_beta context-csazdsjrzia
1. policyservicedev (root)/spectra/spectra-authorization_authz_gamma context-cxoohkpuvva
1. policyservicedev (root)/spectra/sps_alpha context-csyksvfyjva
1. kubectl get ns
1. kubectl describe namespace datha
1. kubectl config set-context --current --namespace=datha
1. kubectl delete ns datha

# Helm Charts
1. helm lint ./mycharts/ --> where `mycharts` is location of my charts directory. Checks for lint errors and syntax.
1. helm install --dry-run --debug ./mycharts/ --generate-name --> this is dry run of the charts.shows how `deployment.yml` will be rendered.
1. helm install example ./mycharts/ --> deploes application to k8s cluster.
1. helm list --> Show list of installed helm charts.
