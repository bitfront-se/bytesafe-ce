# Example configuration for Kubernetes

This example is intended to be used with some local Kubernetes cluster like the one included in Docker Desktop or
Minikube.

```bash
# First we create a name space
kubectl create namespace bytesafe
# Then we create a secret for the data-encryption key
kubectl create secret generic -n bytesafe data-encryption-key --from-literal=DATA_ENCRYPTION_KEY=$(cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | fold -w 50 | head -n 1)
# Then we create admin password for postgres
export PG_ADMIN_PASSWORD=$(cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | fold -w 15 | head -n 1)
kubectl create secret generic -n bytesafe postgres-password --from-literal=POSTGRES_PASSWORD=${PG_ADMIN_PASSWORD} --from-literal=DB_ADMIN_PASSWORD=${PG_ADMIN_PASSWORD}
# Apply using kustomize
kubectl apply -k ./
```

## Note on minikube usage
The Docker Desktop will use `localhost` for the LoadBalancer "External-IP". If you use Minikube it can happen
that the "External-IP" is set to some other private ip address like `10.98.171.XX`. If that is the case you need to
update the URL_PREFIX. In this case it is recommended that you set the like this `URL_PREFIX="http://bytesafe.
example:8081"` in `kustomization.yml` and let `bytesafe.example` point to the internal IP address using `/etc/hosts`
or similar.
