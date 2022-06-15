# AirAsia-Tasks-5
Setup Alerts and monitoring on the CPU/Memory for the cluster using Prometheus/Grafana.

## This Task is dobe via Helm

## Steps to perform

## Steps to Install Prometheus:
--------------------------------

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/prometheus
kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext
minikube service prometheus-server-ext


## Steps to install Grafana:
--------------------------

helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install grafana stable/grafana
kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext
minikube service grafana-ext

To get user name and password in Grafana:

kubectl get secret --namespace default grafana -o yaml
echo "<Encrypted_Pwd>" | openssl base64 -d ; echo

or 

kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
----------------------------------------------------------

Dashboard  to be used: https://grafana.com/grafana/dashboards/6417
