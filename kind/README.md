# Propósito
Criar um cluster para estudos de Kuberntes através do Kind

# Pré-requisítos
Docker
Helm

# Começando
Para inicialiazar o cluster, use o comando abaixo

kind create cluster --name "nome_cluster" -- config cluster.yaml

Será criado um cluster com 4 nodes, sendo um Control Plane e três works

Após sua instalação, é muito importante ter instalado o Metrics Server, para isso, execute a linha abaixo:

helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server \
helm repo update \
helm upgrade --install --set args={--kubelet-insecure-tls} metrics-server metrics-server/metrics-server --namespace kube-system
