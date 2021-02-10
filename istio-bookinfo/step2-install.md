# Installing Istio in the Minikube Cluster

For this installation, we use the `demo` configuration profile. It’s selected to have a good set of defaults for testing, but there are other profiles for production or performance testing.

`istioctl install --set profile=demo -y`{{execute}}

Add a namespace label to instruct Istio to automatically inject Istio configuration when you deploy your application later.

`kubectl label namespace default istio-injection=enabled`{{execute}}