# Open the application to outside traffic

The Bookinfo application is deployed but not accessible from the outside. To make it accessible, you need to create an Istio Ingress Gateway, which maps a path to a route at the edge of your mesh.

Associate this application with the Istio gateway:

- `kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml`{{execute}}

Ensure that there are no issues with the configuration:

- `istioctl analyze`{{execute}}

Determine the `gateway` port:

- `export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].nodePort}')`{{execute}}

- `echo "$INGRESS_PORT"`{{execute}}

Open the following link in your browser. Please, replace the port `80` in the URL with the value of `INGRESS_PORT` from the previous command:

https://[[HOST_SUBDOMAIN]]-80-[[KATACODA_HOST]].environments.katacoda.com/productpage