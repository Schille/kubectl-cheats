# kubectl-cheats
A collection of useful `kubectl` commands.


## Running a PostgreSQL client within a Kubernetes cluster
`kubectl run psql -i --tty --image=jbergknoff/postgresql-client --restart=Never --command --namespace=<mynamespace> -- bash`   
[...]  
`kubectl delete pod psql --namespace=<mynamespace>`  
