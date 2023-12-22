

# Kubenates Services
1. ClusterIP - provides IP address and communication within the cluster.
1. NodePort - Allocates port, IP address to allow external caller to make call to Pod.
1. LoadBalancer - Balances load, exposes service to external caller, can be combined with cloud provider load balancer. ehind the scene, this service sets up NodePort and ClusterIP service. Nginx is type of loadbalancer.
1. ExternalName - sets up alias for external service. This acts as proxy for external service.
1. kubectl get ing --> view ingress services.
1. Port forwarding
 1. kubectl port-forward my-api 8090:80
 1. kubectl port-forward deployment/my-api 8090:80
 1. kubectl port-forward service/my-api 8090:80
1. Cluster IP Services
  1. kubectl apply -f .\my-api.ClusterIpService.yml  --dry-run=client --validate=true --> Only validates and dry run
  1. kubectl apply -f .\my-api.ClusterIpService.yml --> Now `k exec my-api-6fb5594f8b-2h5w6 -- curl http://my-api-cluster-ip:8090/WeatherForecast` will get results from service.
1. NodePort Services
  1. kubectl apply -f .\my-api.NodePort.yml
  1. Open browser and type http://localhost:31000/WeatherForecast
  1. kubectl delete -f .\my-api.NodePort.yml --> delete nodeport
1. LoadBalancer Services
  1. kubectl apply -f .\my-api.LoadBalancer.yml
  1. Open browser and type http://localhost/WeatherForecast
  1. kubectl delete -f .\my-api.NodePort.yml --> delete nodeport

# Injecting Settings for Pods
1. Use ConfigMaps and Secrets, are shared across pods.
1. Types of config maps
 1. Store in file where file name is key , content can be json, xml etc.
 1. Provide on command line
 1. ConfigMap manifest as yaml, loaded as env variable or ConfigMap volume.
1. `kubectl apply -f .\my-api.ConfigMap.yml` creates config map from file. Config map also created from env type of file and from command line.
1. View config map `kubectl describe configmaps spectra-jaeger-agent-config -n spectra-platform`

# Useful kubectl Commands
1. Setting alias for Kubectl
  1. Set-Alias -Name k -Value kubectl - Windows Powershell
  1. alias k='kubectl' - Mac ZShell
1. kubectl version
1. kubectl cluster-info
1. kubectl get all
1. kubectl get all  -l app.kubernetes.io/instance=authz-management
1. kubectl get services
1. kubectl run [container-name] --image=[image-name]
1. kubectl expose ...
1. kubectl create -f create-namespace.yml
1. k exec my-api -it sh --> To get bash shell
1. kubectl -c management exec --stdin --tty authz-management-5984849cf5-2rnt4 -- sh --> Gets shell of pod called `authz-management-5984849cf5-2rnt4`.
1. `kubectl -c management exec --stdin --tty authz-management-84b7fb6456-vgjjv -- printenv` - print all environment vars for specified pod
1. kubectl logs [container-name]
1. kubectl logs [pod-name] -c [container-name]

# kubectl pods
1. kubectl get pods -->List all pods
1. kubectl get pods  -l app.kubernetes.io/instance=authz-management
1. k describe pod my-api
1. kubectl run my-api --image=repo:label  --> this will create pod called 'my-api' using container image 'repo:label'
1. kubectl port-forward my-api 8090:80 --> where 8090 is external port and 80 is internal port. http://localhost:8090/WeatherForecast
1. kubectl delete pod my-api
1. Pods have their own IP address
1. kubectl port-forward [pod] [ports]
1. kubectl port-forward pods\my-api 8090:80 --> where 8090 is external port and 80 is internal port. http://localhost:8090/WeatherForecast
1. kubectl port-forward pod/my-api-6fb5594f8b-5x442 8090:80 --> Magic number at the end of the pod name comes when replicas are setup.
1. kubectl create -f .\my-api.Pod.yml --dry-run=client --validate=true  --> Only validates and dry run
1. kubectl apply -f .\my-api.Pod.yml --> Creates pod
1. kubectl apply -f .\my-api.Pod.yml --save-config --> Creates annotation, applies specific delta changes in yml
1. kubectl delete -f .\my-api.Pod.yml
1. List container images
```
kubectl get pods -o jsonpath="{.items[*].spec.containers[*].image}" |\
tr -s '[[:space:]]' '\n'

```

# kubectl deployments
1. kubectl create -f .\my-api.Deploy.yml  --dry-run=client --validate=true  --> Only validates and dry run
1. kubectl get deployments
1. kubectl get deployments --show-labels
1. kubectl get deployments -l app=my-api-app
1. kubectl scale deployments authz-decision --replicas=1
1. kubectl scale deployments -f .\my-api.Deploy.yml --replicas=2
1. kubectl scale deployments -f  --replicas=2
1. k describe deployment my-api
1. kubectl port-forward deployment/my-api 8090:80
1. k get deployment
1. k get deployments --show-labels
1. k scale -f my-api.Deploy.yml --replicas=2
1. k delete -f my-api.Deploy.yml

# kubectl namespace
1. Switch context `kubectl config use-context context-clxtwe5tvwq` or `kubectl config use-context rancher-desktop`
1. policyservicedev (root)/spectra/spectra-authorization_authz_alpha context-clxtwe5tvwq
1. policyservicedev (root)/spectra/spectra-authorization_authz_beta context-csazdsjrzia
1. policyservicedev (root)/spectra/spectra-authorization_authz_gamma context-cxoohkpuvva
1. policyservicedev (root)/spectra/sps_alpha context-csyksvfyjva
1. kubectl get ns
1. kubectl describe namespace dathav1
1. kubectl config get-contexts --> list all contexts
1. kubectl config set-context --current --namespace=dathav1
1. kubectl delete ns datha

# Helm Charts
1. helm lint ./mycharts/ --> where `mycharts` is location of my charts directory. Checks for lint errors and syntax.
1. helm install --dry-run --debug ./mycharts/ --generate-name --> this is dry run of the charts.shows how `deployment.yml` will be rendered.
1. helm install example ./mycharts/ --> deploys application to k8s cluster.
1. helm list --> Show list of installed helm charts.

# Association Service
1. kubectl -n eloj apply -f <filename>.yaml 
1. kubectl -n eloj get associations
1. kubectl -n eloj edit associations spectraauthz-associations
  Increase version number 'version: "100"' to reapply associations
1. kubectl get secrets -n eloj
1. kubectl get crd 
1. kubectl get crd associations.oracle.fa.secassoc
1. kubectl describe crd associations.oracle.fa.secassoc
