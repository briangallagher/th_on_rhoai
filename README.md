# training_hub_on_rhoai_2

### Apply the training hub sft runtime to the cluster
kubectl apply -f training-hub-sft-runtime.yaml

### RBAC for cluster training runtimes
SA_NAME=<my-sa> SA_NAMESPACE=<my-namespace> envsubst < rbac-runtimes.yaml | kubectl apply -f -

### RBAC for trainjobs
SA_NAME=<my-sa> SA_NAMESPACE=<my-namespace> envsubst < rbac-trainjobs.yaml | kubectl apply -f -

### Let the pod run as root
oc adm policy add-scc-to-user anyuid -z default -n test-sdk

