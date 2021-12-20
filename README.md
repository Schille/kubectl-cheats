# kubectl-cheats
A collection of useful `kubectl` commands.


## Running a PostgreSQL client within a Kubernetes cluster
`kubectl run psql -i --tty --image=jbergknoff/postgresql-client --restart=Never --command --namespace=<mynamespace> -- bash`   
[...]  
`kubectl delete pod psql --namespace=<mynamespace>`  

## Delete all Jobs from a Namespace
`kubectl delete jobs --namespace=<mynamespace> $(kubectl get jobs --namespace=<mynamespace> -o custom-columns=:.metadata.name)`

## Delete all completed Pods from a Namespace
`kubectl delete pods --namespace <namespace> --field-selector=status.phase==Succeeded`

## Delete old replica sets
`kubectl --namespace <namespace> delete $(kubectl --namespace <namespace> get all | grep replicaset.apps | grep "0         0         0" | cut -d' ' -f 1)`

## Delete CRDs in case of missing finalizers
`kubectl patch crd/<CRD> -p '{"metadata":{"finalizers":[]}}' --type=merge`
and then delete all objects.
