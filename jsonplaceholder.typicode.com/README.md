####

```
kubectl create ns jsonplaceholder

kubectl apply -f jsonplaceholder.typicode.com/serviceentry.yaml 

kubectl edit cm whereami-frontend -n frontend # reference the URL in the whereami-frontend configmap

# redeploy frontend 
kubectl -n frontend rollout restart deployment/whereami-frontend

# keep calling frontend 
while true; do curl https://frontend.endpoints.mc-e2m-01.cloud.goog; sleep 0.5; done

# enable access logging 
cat <<EOF | kubectl apply -f -
apiVersion: v1
data:
  mesh: |-
    accessLogFile: /dev/stdout
    defaultConfig:
      tracing:
        stackdriver: {}
kind: ConfigMap
metadata:
  name: istio-asm-managed-rapid
  namespace: istio-system
EOF
```