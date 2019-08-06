# jenkins-x-kubernetes
Kubernetes Build Pack extends the Classic Build Pack to add opinionated CI+CD for Kubernetes Environments with GitOps based promotion

Enhanced to set the pipeline to generate unit tests, run tests, generate test report, coverage report and security scan the code

integated with istio for progressive delivery into production to route trafic to new deployments partially...etc..

Install JX Addons

jx create addon istio
jx create addon prometheus
jx create addon flagger

This will enable Istio in the jx-production namespace for metrics gathering.


Get the ip of the Istio ingress and point a wildcard domain to it (e.g. *.example.com), 
so we can use it to route multiple services based on host names.
 The Istio ingress provides the routing capabilities needed for Canary releases (traffic shifting) 
 that the traditional Kubernetes ingress objects do not support.
 
kubectl -n istio-system get service istio-ingressgateway \
-o jsonpath='{.status.loadBalancer.ingress[0].ip}'

The cluster is configured.

