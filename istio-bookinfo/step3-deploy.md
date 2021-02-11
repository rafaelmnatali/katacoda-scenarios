# Deploy the sample application

Deploy the `Bookinfo` sample application:

`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`{{execute}}

The application will start. As each pod becomes ready, the Istio sidecar will be deployed along with it.

Execute the following commands to confirm:

- `kubectl get services`{{execute}}

it should return something similar to this:

```
NAME          TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
details       ClusterIP   10.0.0.212      <none>        9080/TCP   29s
kubernetes    ClusterIP   10.0.0.1        <none>        443/TCP    25m
productpage   ClusterIP   10.0.0.57       <none>        9080/TCP   28s
ratings       ClusterIP   10.0.0.33       <none>        9080/TCP   29s
reviews       ClusterIP   10.0.0.28       <none>        9080/TCP   29s
```

- `kubectl get pods`{{execute}}

it should return something similar to this:

```
NAME                              READY   STATUS    RESTARTS   AGE
details-v1-558b8b4b76-2llld       2/2     Running   0          2m41s
productpage-v1-6987489c74-lpkgl   2/2     Running   0          2m40s
ratings-v1-7dc98c7588-vzftc       2/2     Running   0          2m41s
reviews-v1-7f99cc4496-gdxfn       2/2     Running   0          2m41s
reviews-v2-7d79d5bd5d-8zzqd       2/2     Running   0          2m41s
reviews-v3-7dbcdcbc56-m8dph       2/2     Running   0          2m41s
```

**Note**: Re-run the previous command and wait until all pods report `READY 2/2` and `STATUS Running` before you go to the next step. This might take a few minutes.

Verify everything is working correctly up to this point. Run this command to see if the app is running inside the cluster and serving HTML pages by checking for the page title in the response:

- `kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"`{{execute}}

it should return:

`<title>Simple Bookstore App</title>`