# View the dashboard

Istio integrates with several different telemetry applications. These can help you gain an understanding of the structure of your service mesh, display the topology of the mesh, and analyze the health of your mesh.

Install Prometheus addon. 

- `kubectl apply -f samples/addons/prometheus.yaml`{{execute}}

Install the latest version of Kiali Server using a Helm Chart. 

- `helm install --namespace istio-system --set auth.strategy="anonymous" --repo https://kiali.org/helm-charts kiali-server kiali-server`{{execute}}

Access the Kiali dashboard by initializing in the terminal and then accessing the UI using the url below.

- `istioctl dashboard kiali --address=0.0.0.0 --browser=false`{{execute}}

https://[[HOST_SUBDOMAIN]]-20001-[[KATACODA_HOST]].environments.katacoda.com