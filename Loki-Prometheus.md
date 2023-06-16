1. Loki query to view Traefik logs
`{namespace=“spectra-platform”,container=“traefik”,dom_env=“beta”} |= “/authz”`
`{namespace=“spectra-platform”,container=“traefik”,dom_env=“beta”} |= “/authz” | json | request_Oci_Original_Url=`https://speccdrm01-dc1.beta.spectra.us-phoenix-1.ocs.oc-test.com/api/authz/decision/v1/authorize``

1. Loki query to identity new deployment request
`{cluster="<cluster_id>", container=~"decision|management|job",namespace="eldd"} != "/live" != "/ready" |= "method=POST url=/v1/deployments"`

1. Loki Query to Identify DB User
{cluster="<cluster_id>", container=~"decision|management|job", namespace="<namespace>} |= "connection started for user"
{dom_env="<stage_name>", container=~"decision|management|job", namespace="<namespace>} |= "connection started for user"
All SAS logs from cluster 
{cluster="<cluster_id>", container=~"management|decision|job", namespace="<namespace>} != "/live" != "/ready"

1. Loki Query for Errors
{cluster="<cluster_id>", container=~"decision|management|job", namespace="<namespace> } |="level=error" != "/live" != "/ready"

1. Loki Query to fetch logs for name space
{cluster="<cluster_id>", container=~"decision|management|job", namespace="<namespace>"} != "/live" != "/ready"

1. Loki query for query with certain string `IRC_ACCESS_MY_CANDIDATE` and without certain string `role not found`:
{cluster="<cluster_id>", namespace="<namespace>", container=~"decision|management|job", namespace="<namespace>} != "/live" != "/ready" != "role not found" |= "IRC_ACCESS_MY_CANDIDATE"

1. Loki query to identify default deployment by 'Decision'
{cluster="<cluster_id>", container=~"decision", namespace="<namespace>"} != "/live" != "/ready" |= "Default deployment from latest records"

1. Loki query to identify last cache refresh by 'Decision'

{cluster="<cluster_id>", container=~"decision", namespace="<namespace>"} != "/live" != "/ready" |= "total time of get all policies from DB (seconds)"

1. Loki query to view APM logs
{container=~"apm",namespace="ehji"}
OSSP Provisioning Debug Dashboard

1. Alpha
Cluster ID: cluster="ocid1.cluster.oc1.phx.aaaaaaaaafaoeblla2eegicngiwofeqwzof4v7hazzngorr2bclxtwe5tvwq" 
Cluster label:  dom_env="alpha"
Env=Alpha Namespace=SAS Excludes live and ready
Alpha Cluster="ocid1.cluster.oc1.phx.aaaaaaaaafaoeblla2eegicngiwofeqwzof4v7hazzngorr2bclxtwe5tvwq"

1. Beta
Cluster ID: ocid1.cluster.oc1.phx.aaaaaaaal7jqrhnjuold72i5j662gmeketyragk4us7aqqjbqcsazdsjrzia
Cluster label:  dom_env="beta"
Env=Beta Namespace=SAS Excludes live and ready
Beta Cluster="ocid1.cluster.oc1.phx.aaaaaaaal7jqrhnjuold72i5j662gmeketyragk4us7aqqjbqcsazdsjrzia"

1. Gamma
Cluster ID: ocid1.cluster.oc1.phx.aaaaaaaal7naqd4lkyjxfjjfotx5ij5qbjkrrvkmk6t3ro34gcxoohkpuvva
Cluster label: dom_env="gamma"
Gamma Cluster="ocid1.cluster.oc1.phx.aaaaaaaal7naqd4lkyjxfjjfotx5ij5qbjkrrvkmk6t3ro34gcxoohkpuvva" 