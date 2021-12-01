# kubectl-cheats
A collection of useful `kubectl` commands.


## Running a PostgreSQL client within a Kubernetes cluster
`kubectl run psql -i --tty --image=jbergknoff/postgresql-client --restart=Never --command --namespace=<mynamespace> -- bash`   
[...]  
`kubectl delete pod psql --namespace=<mynamespace>`  

## Delete all jobs from a namespace
`kubectl delete jobs --namespace=<mynamespace> $(kubectl get jobs --namespace=<mynamespace> -o custom-columns=:.metadata.name)`
