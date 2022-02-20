# Access Autotune tunables


`AUTOTUNE_PORT=$(kubectl -n monitoring get svc autotune --no-headers -o=custom-columns=PORT:.spec.ports[*].nodePort)`{{execute}}

`MINIKUBE_IP=`minikube ip``{{execute}}

View the sample list of tunables:
`curl http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/listAutotuneTunables`{{execute}}




