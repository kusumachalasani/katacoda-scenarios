# Step 1 - Install Kruize Autotune

We are using minikube to install Autotune.

Start minikube
`minikube start --cpus=8 --memory=16384M`{{execute}}

Clone the Autotune and benchmarks repositories
`git clone git@github.com:kruize/autotune.git`{{execute}}

`git clone git@github.com:kruize/benchmarks.git`{{execute}}

Set-up prometheus:

`cd autotune`{{execute}}
`$ ./scripts/prometheus_on_minikube.sh -as` {{execute}}

Deploy Autotune

`./deploy.sh -c minikube -i autotune:test`{{execute}}
