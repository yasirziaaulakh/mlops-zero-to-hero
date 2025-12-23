-------------------------------------------------
How to install mlflow in production environment
-------------------------------------------------
First to setup posgresql on rds on aws

kind create cluster --name=prod-mlflow-cluster # you can use eks also

kubectl create ns mlflow

helm install mlflow community-charts/mlflow \
--namespace mlflow \
--set backendStore.databaseMigration=true \
--set backendStore.postgres.enabled=true \
--set backendStore.postgres.host=your-postgres-hostname \
--set backendStore.postgres.port=5432 \
--set backendStore.postgres.database=dbname \
--set backendStore.postgres.user=dbusername \
--set backendStore.postgres.password=yourpassword  # for security, we can use secrets or usw aws system store parameter store

kubect get pods -n mlflow 

kubect get pods -n mlflow -w

kubectl edit pod/pod-name-whcih-you-get-from-above-command -n mlflow # now you see there is 2 containers. 1 is init containter which responsibility is to check the connectivity of mlflow pod connected to rds postgress db or not. if not connected, it goes not crash loopback state-uri

#if we are running eks then we need to create the ingress resource and then thorugh loadbalancer we expose the service.
#but i am doing this on my localpc so i need to to the below step
kubectl -n mlflow port-forward pod/pod-name-which-copy-from-above 7006:5000 --address 0.0.0.0 #7006 is host port and 5000 is the internal pod port of mlflow and --address use to bind with

in localpc localhost:7006 # you see mlflow is running


Please refer to the below document for the next lecture

https://community-charts.github.io/docs/charts/mlflow/postgresql-backend-installation
