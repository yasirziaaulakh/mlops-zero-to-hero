------------------------------------------------------
Install MlFlow on k8s for non proudction environment
-------------------------------------------------------
kind create cluster --name=basic-mlflow-cluster

you can install mf-flow using k8s manifest files or using helm charts

there is no official mlflow but community helm Charts for open source projects (https://community-charts.github.io/). now click on browse charts and then you see ml-flow chart

some-of steps are wrong in the above, so follow the github repo which i fork

copy this command for the above link

helm repo add community-charts https://community-charts.github.io/helm-charts

helm repo update

helm install mlflow-community community-charts/mlflow 

kubectl get pods

kubectl port-forward pod/pod-name-which-copy-from-above 7006:5000 --address 0.0.0.0 #7006 is host port and 5000 is the internal pod port of mlflow and --address use to bind with

in localpc localhost:7006 # you see mlflow is running

Please refer to the below documentation for this lecture.

https://community-charts.github.io/docs/charts/mlflow/basic-installation
