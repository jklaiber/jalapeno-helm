# Jalapeno Helm Chart

This repository should provide a basic Helm Chart for the Jalapeno project.  
In order to minimize the configuration and maintainance effort, there are also official charts in use (influxdb, grafana and kafka). 

## Limitations
There are some limitations in the moment:

### ArangoDB Root Password
The arangodb operator does not yet let us define a root password.  
Therefore you have to install the helm chart and first set the root password in the UI of Arango.  
After that all crashing pods will be coming in a running state.  
  
The default password of the arangodb is as follows:
```
username: root
password: ""
```

## Prerequisites
You need to install the arangodb operator first. This is the new official recommended way to deploy arango databases on a Kubernetes cluster. 
```
export URLPREFIX=https://github.com/arangodb/kube-arangodb/releases/download/1.2.8
helm install arangodb-crd $URLPREFIX/kube-arangodb-crd-1.2.8.tgz
helm install arangodb-operator $URLPREFIX/kube-arangodb-1.2.8.tgz
```

## Deploy Helm Chart
```
$ helm install -f <path_to_your_values_file> <release-name> jalapeno --namespace <namespace>
```

