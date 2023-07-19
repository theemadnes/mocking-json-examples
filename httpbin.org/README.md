```
kubectl apply -f httpbin.org/serviceentry.yaml
kubectl apply -f httpbin.org/destinationrule.yaml

kubectl edit cm whereami-frontend -n frontend # reference the URL http://httpbin.org/json in the whereami-frontend configmap

# redeploy frontend 
kubectl -n frontend rollout restart deployment/whereami-frontend
```