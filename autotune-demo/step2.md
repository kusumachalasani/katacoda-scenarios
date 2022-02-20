# Access Autotune tunables


`AUTOTUNE_PORT=$(kubectl -n monitoring get svc autotune --no-headers -o=custom-columns=PORT:.spec.ports[*].nodePort)`{{execute}}

`MINIKUBE_IP=$(minikube ip)`{{execute}}

`TECHEMPOWER_PORT=$(kubectl -n default get svc petclinic-service --no-headers -o=custom-columns=PORT:.spec.ports[*].nodePort)`

View the sample list of tunables:
`curl http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/listAutotuneTunables`{{execute}}

Access the techempower benchmark metrics `http://${MINIKUBE_IP}:${TECHEMPOWER_PORT}/metrics`

Autotune is monitoring these apps http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/listStacks
List Layers in apps that Autotune is monitoring http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/listStackLayers
Tunables in apps that Autotune is monitoring http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/listStackTunables
Autotune searchSpace at http://${MINIKUBE_IP}:${AUTOTUNE_PORT}/searchSpace

Access autotune objects using: 
`kubectl -n default get autotune`{{execute}}

Access autotune tunables using: 
`kubectl -n monitoring get autotuneconfig`{{execute}}



