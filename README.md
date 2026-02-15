# Cloud DevOps — Orchestrating Containers and Microservices

O projeto simula uma aplicação chamada **Loja Veloz**, dividida em três microsserviços:

- **Pedidos**
- **Pagamentos**
- **Estoque**
<br>

## Objetivo

O Objetivo deste repositório é apresentar a parte prática do trabalho de **Cloud DevOps**, com foco em **microsserviços**, **containerização**, **orquestração**, **CI (GitHub Actions)** e **Infraestrutura como Código (Terraform)**.

- Arquitetura baseada em **microsserviços**
- **Dockerfiles** para cada serviço
- Orquestração local com **Docker Compose**
- Orquestração em cluster com **Kubernetes**
- Pipeline de CI com **GitHub Actions**
- Estrutura de IaC com **Terraform**

<br>

## Estrutura do Projeto

```txt
DevOps/
│
├─ services/
│   ├─ pedidos/
│   │   ├─ Dockerfile
│   │   └─ index.js
│   ├─ pagamentos/
│   │   ├─ Dockerfile
│   │   └─ index.js
│   └─ estoque/
│       ├─ Dockerfile
│       └─ index.js
│
├─ k8s/
│   ├─ pedidos-deployment.yaml
│   ├─ pedidos-service.yaml
│   ├─ pagamentos-deployment.yaml
│   ├─ pagamentos-service.yaml
│   ├─ estoque-deployment.yaml
│   ├─ estoque-service.yaml
│   ├─ configmap.yaml
│   ├─ secret.yaml
│   └─ hpa.yaml
│
├─ infraestrutura/
│   └─ terraform/
│       ├─ main.tf
│       ├─ outputs.tf
│       └─ variables.tf
│
├─ .github/
│   └─ workflows/
│       └─ ci.yml
│
└─ docker-compose.yml
```
<br>

## 🛠️ Tecnologias Utilizadas

- Docker
- Docker Compose
- Kubernetes (Docker Desktop)
- HPA (Horizontal Pod Autoscaler)
- ConfigMap & Secret
- Arquitetura baseada em microsserviços

<br>

## 💻 Como Executar Localmente (Docker Compose)

🔹 Pré-requisitos

- Docker Desktop instalado
- Docker Compose habilitado

🔹 Subir ambiente local

Na raiz do projeto:

```bash
docker compose up -d --build
```

Verificar containers:

```bash
docker ps
```

Acessar serviços:

Pedidos → http://localhost:3000

Pagamentos → http://localhost:3001

Estoque → http://localhost:3002

🔹 Parar ambiente

```bash
docker compose down
```

## ☸️ Executando no Kubernetes

🔹 Pré-requisitos

Docker Desktop com Kubernetes habilitado

kubectl instalado

Verificar cluster:

```bash
kubectl get nodes
```

🔹 Deploy da aplicação

Aplicar manifests:

```bash
kubectl apply -f k8s/
```

Verificar pods:

```bash
kubectl get pods
```

Verificar deployments:

```bash
kubectl get deployments
```

Verificar services:

```bash
kubectl get svc
```

Verificar HPA:

```bash
kubectl get hpa
```

🔹 Acessar aplicação (Port Forward)

```bash
kubectl port-forward svc/pedidos-service 3000:3000
```

Acessar:

http://localhost:3000

🔹 Remover aplicação do cluster

```bash
kubectl delete -f k8s/
```
<br>

## 🏗️ Terraform

A estrutura Terraform está localizada em:

```
infraestrutura/terraform/
```

Comandos:

```bash
cd infraestrutura/terraform
terraform init
terraform validate
```
