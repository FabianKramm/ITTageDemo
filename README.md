## Install Chart

```
cd 01-Helm
helm3 create awesomeapp
k create ns helm-test
helm3 install awesomeapp ./awesomeapp -n helm-test
```

## Add Mysql to chart

```
cp Chart.yaml awesomeapp/Chart.yaml
cp values.yaml awesomeapp/values.yaml
helm3 upgrade awesomeapp ./awesomeapp -n helm-test
```
