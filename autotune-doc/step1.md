# Step 1 - Install Autotune

Currently we are using scripts to install kruize-autotune.
But, later we will incorporate individual steps without the need of scripts.
Install minikube
`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`{{execute}}
`chmod +x kubectl`{{execute}}
`export PATH=${PWD}:$PATH`{{execute}}

Install minikube
`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`{{execute}}
`sudo install minikube-linux-amd64 /usr/local/bin/minikube`{{execute}}

Start minikube
`minikube start --cpus=8 --memory=16384M`{{execute}}


`minikube version`

Clone the Autotune and benchmarks repositories
`git clone git@github.com:kruize/autotune.git`{{execute}}

`git clone git@github.com:kruize/benchmarks.git`{{execute}}

Set-up minikube and prometheus:

`cd autotune`{{execute}}
`$ ./scripts/prometheus_on_minikube.sh -as` {{execute}}

Build autotune docker image

`./build.sh -i autotune:test`{{execute}}

Deploy Autotune

`./deploy.sh -c minikube -i autotune:test`{{execute}}
