# Download Istio

Download and extract the release 1.9.0 with the following command:

`curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.9.0 TARGET_ARCH=x86_64 sh -`{{execute}}

Move to the Istio package directory:

`cd istio-1.9.0`{{execute}}

Add the `istioctl` client to your path:

`export PATH=$PWD/bin:$PATH`{{execute}}