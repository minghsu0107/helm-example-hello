# Helm Example Hello World

Example Helm chart.

## Usage
Initialize a new project:
```bash=
mkdir charts && cd charts/
helm create hello-world
```

Installation:
```bash
export DEPLOY_NAMESPACE=test
export VALUE_FILE=my/path/to/values.yaml
export DOCKER_TAG=latest
export RELEASE_NAME=hello
helm --kube-context mycluster upgrade --install --namespace $DEPLOY_NAMESPACE \
	--values $VALUE_FILE \
	--set image.tag=$DOCKER_TAG \
	$RELEASE_NAME \
	charts/hello-world
	# --debug --dry-run
```

Check installation:
```bash
helm ls -n test
helm get all $RELEASE_NAME -n test
```

Uninstallation:
```bash
helm uninstall $RELEASE_NAME -n test
```
