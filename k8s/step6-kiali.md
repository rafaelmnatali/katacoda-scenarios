# View the dashboard

Istio integrates with several different telemetry applications. These can help you gain an understanding of the structure of your service mesh, display the topology of the mesh, and analyze the health of your mesh.

Use the following instructions to deploy the Kiali dashboard, along with Prometheus, Grafana, and Jaeger.

Install Kiali and the other addons and wait for them to be deployed.

- `kubectl apply -f samples/addons`{{execute}}
- `kubectl rollout status deployment/kiali -n istio-system`{{execute}}

Access the Kiali dashboard by initializing in the terminal and then accessing the UI using the url below.

- `istioctl dashboard kiali --address=0.0.0.0 --browser=false`{{execute}}

https://[[HOST_SUBDOMAIN]]-20001-[[KATACODA_HOST]].environments.katacoda.com