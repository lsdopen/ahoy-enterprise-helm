# ahoy-enterprise-helm
Ahoy Enterprise Helm Charts

## Install

### Helm repo

```commandline
helm repo add ahoy-enterprise https://lsdopen.github.io/ahoy-enterprise-helm
helm repo update
```

### Enterprise image

In order for the Ahoy Enterprise server image to be pulled, a secret with the correct docker registry credentials to access
the enterprise image will need to be created.

For example:

```commandline
kubectl create secret docker-registry ahoy-enterprise-image-registry --namespace ahoy --docker-server https://docker.io/ --docker-username <username> --docker-password <password>
```

The name of the secret then needs to be updated in the values file:

```yaml
imagePullSecrets:
  - name: ahoy-enterprise-image-registry
```

### Helm install

```commandline
helm install ahoy-enterprise --namespace ahoy-enterprise --create-namespace --values values.yaml ahoy-enterprise/ahoy-enterprise
```