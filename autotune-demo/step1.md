# Step 1 - Install Kruize Autotune

In this demo, We are using minikube to install Autotune.

Start minikube
`minikube start`{{execute}}

Clone Autotune repository.
`git clone https://github.com/kruize/autotune.git`{{execute}}

Currently, Autotune use prometheus as datasource to collect the metrics.
To set-up prometheus,

`cd autotune && ./scripts/prometheus_on_minikube.sh -as`{{execute}}

To apply autotune on an application, let's 

Clone the benchmarks repo
`cd .. && git clone https://github.com/kruize/benchmarks.git`{{execute}}

Deploy TechEmpower benchmark

`kubectl apply -f benchmarks/techempower/manifests`{{execute}}

Deploy Autotune

Get the version of Autotune
`AUTOTUNE_VERSION="$(grep -A 1 "autotune" pom.xml | grep version | awk -F '>' '{ split($2, a, "<"); print a[1] }')"`


`cd autotune && ./deploy.sh -c minikube -i dinogun/autotune_operator:0.0.8_mvp -o kruize/autotune_optuna:${AUTOTUNE_VERSION}`{{execute}}

Install autotune objects

`cd ../benchmarks/techempower && kubectl apply -f autotune/autotune-http_resp_time.yaml`{{execute}}

Set-up of autotune and TechEmpower benchmark complete.
