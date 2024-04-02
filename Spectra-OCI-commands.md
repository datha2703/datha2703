
# OCI Commands
1. oci session authenticate
1. oci iam region list --auth security_token
1. Collected info set environment var as 'OCI_CLI_AUTH=security_token' when using session auth.
1. oci --no-retry --auth instance_principal --region us-phoenix-1 os object put --namespace axzreuakkdwb  --bucket-name slaps_integration --name SPECTRA/<filename> --file <filename>   --output table --force


# Spectra cli
1. spectra-cli instance delete  --instance-name dathav1 --stage-name alpha --service-name authz --org-name spectra-authorization --region us-phoenix-1
1. spectra-cli instance create --filename=gamma.yaml
1. spectra-cli stage create --filename out/gamma.yaml --verbosity-level 100  --> used in oke and spectra cli image upgrade.
1. spectra-cli-windows-amd64-0.2.35.exe  instance get --instance-name dathav1 --stage-name alpha --service-name authz --org-name spectra-authorization --region us-phoenix-1
1. spectra-cli instance rm -g spectra-authorization --service-name authz --instance-name dathav1 --stage-name alpha -region us-phoenix-1
1. spectra-cli list instance 
1. Node rotation - `docker run -v ~/:/root -v ~/:${HOME} docker-master.cdaas.oraclecloud.com/docker-spectra-platform/oke-node-rotation -f -c <YOUR_CLUSTER_CONTEXT> -t <YOUR_KUBE_CONFIG_FILE> -n 2`
1. Deleting name space stuck in terminating
```
(       
NAMESPACE=mahith
kubectl proxy &
kubectl get namespace $NAMESPACE -o json |jq '.spec = {"finalizers":[]}' >temp.json
curl -k -H "Content-Type: application/json" -X PUT --data-binary @temp.json 127.0.0.1:8001/api/v1/namespaces/$NAMESPACE/finalize
)
```

# K8s Cluster Access
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaal7naqd4lkyjxfjjfotx5ij5qbjkrrvkmk6t3ro34gcxoohkpuvva --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0 ` - Gamma
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaaafaoeblla2eegicngiwofeqwzof4v7hazzngorr2bclxtwe5tvwq --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0 ` - Alpha
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaal7jqrhnjuold72i5j662gmeketyragk4us7aqqjbqcsazdsjrzia --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0 ` - Beta
kubectl rollout restart daemonset spectra-jaeger-agent-ds -n spectra-platform
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.iad.aaaaaaaakyyvsvbzzgdfdbrduj5e6ny5ocqk66kga63bywmatc2qblv7ph3a --file $HOME/.kube/config --region us-ashburn-1 --token-version 2.0.0 ` - Prod Ashburn
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaaump35udtrgjobnq4ewimtnogscxx7b26v6gp24yeqcd67eymuq2q --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0 ` - Prod Phx
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ca-montreal-1.aaaaaaaauo4lp7qk42yz2pidsurg7thunupkeppye3nz6ilgocszzh5labfa --file $HOME/.kube/config --region ca-montreal-1 --token-version 2.0.0 ` - Montreal
1. `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.eu-frankfurt-1.aaaaaaaac4gedm4jcod2gf3dyorufy6b5ep5mzuu5fhtr7zfrcobfv74iiba --file $HOME/.kube/config --region eu-frankfurt-1 --token-version 2.0.0` -- Frankfurt Prod