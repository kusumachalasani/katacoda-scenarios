# Step 1 - Install Autotune

Currently we are using scripts to install kruize-autotune.
But, later we will incorporate individual steps without the need of scripts.
`minikube version`

Clone the Autotune and benchmarks repositories
`git clone git@github.com:kruize/autotune.git`

`git clone git@github.com:kruize/benchmarks.git`

Set-up minikube and prometheus:

`cd autotune`
`$ ./scripts/prometheus_on_minikube.sh -as` 

Build autotune docker image

`./build.sh -i autotune:test`

Deploy Autotune

`./deploy.sh -c minikube -i autotune:test`
