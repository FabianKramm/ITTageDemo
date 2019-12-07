## Install Chart

```
cd 01-Helm
helm3 create awesomeapp
k create ns helm-test
helm3 install awesomeapp ./awesomeapp -n helm-test

# Access the app
export POD_NAME=$(kubectl get pods -l "app.kubernetes.io/name=awesomeapp" -n helm-test -o jsonpath="{.items[0].metadata.name}")
kubectl port-forward $POD_NAME 8080:80 -n helm-test
```

## Add Mysql to chart

```
cp Chart.yaml awesomeapp/Chart.yaml
cp values.yaml awesomeapp/values.yaml
helm3 repo add stable https://kubernetes-charts.storage.googleapis.com
helm3 dependency update ./awesomeapp
helm3 upgrade awesomeapp ./awesomeapp -n helm-test

## Rollback release
helm3 rollback awesomeapp -n helm-test
```

## Skaffold

```
cd 02-Skaffold
k delete ns helm-test
k create ns helm-test
helm init --tiller-namespace helm-test
skaffold dev --port-forward -n helm-test
```

# DevSpace

```
cd 03-DevSpace
k delete ns helm-test
k create ns helm-test
```
