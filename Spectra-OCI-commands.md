
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