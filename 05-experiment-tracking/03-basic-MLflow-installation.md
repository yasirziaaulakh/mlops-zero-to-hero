Section 5 (Experiment Tracking)
22. Basic MLflow Installation [Non-Production, Demo purpose]

install mlflow in local environment

mkdir mlflow-basic-install

cd mlflow-basic-install

python3 -m venv .venv

source .venv/bin/activate

python3 -m pip install mlflow

mlflow ui --backend-state-uri sqlite://mlflow.db --port 7006 (sqlite is provided by python buildtin module, no addition installation is needed.)




Please refer to the below documentation for this lecture.

https://mlflow.org/docs/2.4.2/quickstart.html#install-mlflow
