# Installing Istio in the Minikube Cluster

For this installation, we use the `demo` configuration profile. It’s selected to have a good set of defaults for testing, but there are other profiles for production or performance testing.

`istioctl install --set profile=demo -y`{{execute}}

Add a namespace label to instruct Istio to automatically inject Istio configuration when you deploy your application later.

`kubectl label namespace default istio-injection=enabled`{{execute}}

To confirm the installation was successful execute the following commands:

- `kubectl get namespaces default --show-labels`{{execute}}

it should return information similar to this:

```
NAME      STATUS   AGE   LABELS
default   Active   62s   istio-injection=enabled
```

- `istioctl version`{{execute}}

it should return information similar to this:

```
client version: 1.9.0
control plane version: 1.9.0
data plane version: 1.9.0 (2 proxies)
```