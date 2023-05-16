# Example configuration for Kubernetes

1. Download the `bytesafe-ce.yml` file.
2. Modify to provide a unique and secret value for the **DATA_ENCRYPTION_KEY** variable. This value is used to encrypt sensitive data such as credentials.
3. Start with `kubectl apply -f bytesafe-ce.yml`


```bash
$ curl -O https://raw.githubusercontent.com/bitfront-se/bytesafe-ce/master/examples/minikube/bytesafe-ce.yml
$ echo "DATA_ENCRYPTION_KEY='$(cat /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | fold -w 50 | head -n 1)'" 
# Copy above output to configuration file
$ kubectl apply -f bytesafe-ce.yml
```
