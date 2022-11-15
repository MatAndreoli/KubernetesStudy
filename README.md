
# KubernetesStudy
This repo contains some files for Kubernetes components and a Helm project for study purpose.

## Prerequisites
You must have a cluster running. For that you can use [Minikube](https://minikube.sigs.k8s.io/docs/start/).
Use the following command to start a new cluster:
```shell
minikube start --driver=virtualbox --no-vtx-check --cpus 4 --memory 10000
```
`--driver` [more info.](https://minikube.sigs.k8s.io/docs/drivers/)
You must have [Kubernetes](https://kubernetes.io/docs/home/) (kubectl, [kubens and kubectx are optionals]) installed as well.
You can [click here](https://github.com/MatAndreoli/Programming/blob/master/Programming/Installations.md#kubernetes) for a guide to all these installations. <- (***For Linux Ubuntu users***)

## After all the setup is done, let's get started.

To apply a file's configs to the cluster, run:
```shell
kubectl apply -f path-to/file.[yml | yaml]
```
To see it in the cluster, run:
```shell
kubectl get [component type] [component name]
or
kubectl get pod nginx
or (for all)
kubectl get [pods | svc]
```
`Some component types: [services/svc | deployment/deploy | pods | configmap/cm | secret/sec]`
To delete a component, run:
```shell
kubectl delete [component type] [component name]
kubectl delete service nginx-svc
```

### Using Helm
You must have [Helm](https://github.com/MatAndreoli/Programming/blob/master/Programming/Installations.md#helm) installed as well.
Enter the `Helm/pokemon` folder.
To install/apply a chart to a cluster, run:
```shell
helm install app-name path-to-chart
/Helm/pokemon$ helm install pokemon-app pokemon-app/
/Helm/pokemon/pokemon-app$ helm install pokemon-app .
```
If you are using a values.yml file, you can use `--values values.yml` to specify the file to the installation.

If you have made changes to your `values.yml` file or created another `values2.yml`, and want to apply those changes, run:
```shell
helm upgrade app-name path-to-chart --values values2.yml
```

To delete/remove all the components that were create by the `helm install`, run:
```shell
helm uninstall app-name
```

To test if all the values are correctly placed to a template before applying it to the cluster, you can run:
```shell
helm lint
helm template app-name path-to-chart
```
