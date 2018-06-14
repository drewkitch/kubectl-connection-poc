### kubectl-connection-poc

#### Prerequisites
- working connection to K8s cluster on local machine (e.g., `kubectl cluster-info`)

```
kubectl config view --minify --flatten > kubeconfigdata
docker run --rm -it -v $(pwd):/files dkcodeship/env-var-helper cp kubeconfigdata:/root/.kube/config k8s-env
docker run --rm -it -v $(pwd):/files dkcodeship/env-var-helper ls k8s-env
docker run --rm -it -v $(pwd):/files dkcodeship/env-var-helper cat /root/.kube/config k8s-env
docker run --rm -it -v $(pwd):/files dkcodeship/env-var-helper rm /root/.kube/config k8s-env
docker run --rm -it -v $(pwd):/files dkcodeship/env-var-helper cp kubeconfigdata:/root/.kube/config k8s-env

jet encrypt k8s-env k8s-env.encrypted
rm kubeconfigdata k8s-env
jet steps
```

#### Dockerfiles
- [env-var-helper image](https://github.com/drewkitch/env-var-helper-poc)
- [k8s-controller image](https://github.com/drewkitch/k8s-controller-poc)

#### Todo
- `mkdir -p` directories that need to be built out within container before copying file to location
