
# OCI Commands
1. Connect to Alpha, Set 'policyservicedev' as default in '/Users/datkrish/.oci/config' `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaaafaoeblla2eegicngiwofeqwzof4v7hazzngorr2bclxtwe5tvwq --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0`
1. Connect to Beta, Set 'policyservicedev' as default in '/Users/datkrish/.oci/config' `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaal7jqrhnjuold72i5j662gmeketyragk4us7aqqjbqcsazdsjrzia --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0 `
1. Connect to Gamma Phoenix, Set 'policyservicedev' as default in '/Users/datkrish/.oci/config' `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaal7naqd4lkyjxfjjfotx5ij5qbjkrrvkmk6t3ro34gcxoohkpuvva --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0`
1. Connect to Gamma Ashburn `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.iad.aaaaaaaamn5lalid2e5kqxw7g4nqplvmgvvkslfxwycx5bvwychmmrysituq --file $HOME/.kube/config --region us-ashburn-1 --token-version 2.0.0 `
1. Connect to Prod, set prod section as default in '/Users/datkrish/.oci/config' `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.phx.aaaaaaaafwk6zagqp4qjpn4gfhrpzqmnxuiwgb3hhtj63acrkcf2wmksocpq --file $HOME/.kube/config --region us-phoenix-1 --token-version 2.0.0`
1. Melbourne `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ap-melbourne-1.aaaaaaaauyq7ugmai5jzdwxw5c2vupzboaloyt6gk4fds5yrlcnhaxevzfoq --file $HOME/.kube/config --region ap-melbourne-1 --token-version 2.0.0` 
1. Mumbai oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ap-mumbai-1.aaaaaaaa7b43uhujcv3flv4ujx7x27vtsg3yympfs4bbyrkh7c52vtptwpkq --file $HOME/.kube/config --region ap-mumbai-1 --token-version 2.0.0 
1. Sydney `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ap-sydney-1.aaaaaaaasl3yqgulnqsz7b2f6ju3mix4536vjfxt2wfzxxan6ct6kzs7t4da --file $HOME/.kube/config --region ap-sydney-1 --token-version 2.0.0 `
1. Montreal `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ca-montreal-1.aaaaaaaauo4lp7qk42yz2pidsurg7thunupkeppye3nz6ilgocszzh5labfa --file $HOME/.kube/config --region ca-montreal-1 --token-version 2.0.0 `
1. Toronto `oci ce cluster create-kubeconfig --cluster-id ocid1.cluster.oc1.ca-toronto-1.aaaaaaaabomuxntmbn5ohwrw4ymbi24xzedzsgym5v4pxdqrbctvzxcww3na --file $HOME/.kube/config --region ca-toronto-1 --token-version 2.0.0`


# Spectra cli
1. spectra-cli instance delete  --instance-name dathav1 --stage-name alpha --service-name authz --org-name spectra-authorization --region us-phoenix-1
1. spectra-cli instance create --filename=/Users/sahithi/Desktop/rc-integration-main-instance.yaml
1. spectra-cli stage create --filename out/gamma.yaml --verbosity-level 100  --> used in oke and spectra cli image upgrade.
1. spectra-cli-windows-amd64-0.2.35.exe  instance get --instance-name dathav1 --stage-name alpha --service-name authz --org-name spectra-authorization --region us-phoenix-1
