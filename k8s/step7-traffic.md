# Request Routing

This task shows you how to route requests dynamically to multiple versions of a microservice.

Run the following command to create default destination rules for the Bookinfo services:

- `kubectl apply -f samples/bookinfo/networking/destination-rule-all.yaml`{{execute}}

To route to one version only, you apply virtual services that set the default version for the microservices. In this case, the virtual services will route all traffic to `v1` of each microservice.

- `kubectl apply -f samples/bookinfo/networking/virtual-service-all-v1.yaml`{{execute}}

Open the Bookinfo site in your browser. Notice that the reviews part of the page displays with no rating stars, no matter how many times you refresh. This is because you configured Istio to route all traffic for the reviews service to the version `reviews:v1` and this version of the service does not access the star ratings service.

Access the Kiali dashboard and confirm the that only `v1` services are appearing in the Graph section.

- `istioctl dashboard kiali --address=0.0.0.0 --browser=false`{{execute}}

https://[[HOST_SUBDOMAIN]]-20001-[[KATACODA_HOST]].environments.katacoda.com