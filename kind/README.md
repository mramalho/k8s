# Propósito
Criar um cluster para estudos de Kuberntes através do Kind

# Pré-requisítos
* Docker \
[https://docs.docker.com/get-docker]
* Kind \
[https://kind.sigs.k8s.io/docs/user/quick-start/#installation]
* Helm \
[https://helm.sh/docs/intro/install]

# Começando
Para inicialiazar o cluster, use o comando abaixo

```bash
kind create cluster --name "nome_cluster" -- config cluster.yaml
```

Será criado um cluster com 4 nodes, sendo um Control Plane e três works
* Caso seja omitido o parâmetro --config, será criado um cluster utilizando a última versão estável do kubernetes
* Para utilizar versões específicas de imagens do kubernetes, acesse o link \
[https://github.com/kubernetes-sigs/kind/releases]

Após sua instalação, é muito importante ter instalado o Metrics Server, para isso, execute a linha abaixo:

```bash
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server \
helm repo update \
helm upgrade --install --set args={--kubelet-insecure-tls} metrics-server metrics-server/metrics-server --namespace kube-system
```
