# Tech Challenge Fase 3 - Order System App

Bem-vindo ao repositório do **Order System App**, uma aplicação para gerenciamento de pedidos em uma lanchonete. Este projeto utiliza diversos serviços da AWS, como EKS, DocumentDB, Lambda e ECR, integrados através de scripts Terraform e pipelines de CI/CD com GitHub Actions.

Este guia fornecerá uma visão geral da infraestrutura, explicará como a aplicação está configurada e fornecerá um passo a passo de como você pode rodar este projeto em sua própria conta AWS.

## Sumário

- [Visão Geral da Arquitetura](#visão-geral-da-arquitetura)
- [Pré-requisitos](#pré-requisitos)
- [Configuração Inicial](#configuração-inicial)
- [Deploy da Infraestrutura](#deploy-da-infraestrutura)
  - [1. Deploy do DocumentDB](#1-deploy-do-documentdb)
  - [2. Deploy do EKS Cluster](#2-deploy-do-eks-cluster)
- [Deploy das Aplicações](#deploy-das-aplicações)
  - [3. Deploy da Função Lambda de Autenticação](#3-deploy-da-função-lambda-de-autenticação)
  - [4. Build e Push da Imagem Docker para o ECR](#4-build-e-push-da-imagem-docker-para-o-ecr)
  - [5. Deploy da Aplicação no Kubernetes](#5-deploy-da-aplicação-no-kubernetes)
- [Testando a Aplicação](#testando-a-aplicação)
- [Limpeza](#limpeza)
- [Considerações Finais](#considerações-finais)

---

## Visão Geral da Arquitetura

A aplicação é composta pelos seguintes componentes:

- **DocumentDB**: Banco de dados compatível com MongoDB para armazenamento dos dados da aplicação.
- **EKS (Elastic Kubernetes Service)**: Cluster Kubernetes gerenciado onde a aplicação é executada.
- **AWS Lambda**: Função Lambda para autenticação de clientes.
- **ECR (Elastic Container Registry)**: Registro de container para armazenar a imagem Docker da aplicação.
- **Order System App**: Aplicação Node.js que gerencia clientes, produtos e pedidos.
- **GitHub Actions**: Pipelines de CI/CD para automatizar o deploy da infraestrutura e da aplicação.

---

## Pré-requisitos

Antes de começar, certifique-se de ter:

- **Conta AWS**: Uma conta ativa na AWS com permissões suficientes para criar recursos como VPCs, clusters EKS, DocumentDB, etc.
- **AWS CLI**: Instalado e configurado com suas credenciais.
- **Terraform**: Instalado na versão 1.5.0 ou superior.
- **Kubectl**: Instalado para interagir com o cluster Kubernetes.
- **Node.js**: Versão 20.x instalada para executar scripts Node.js.
- **Docker**: Instalado para construir imagens Docker.
- **Git**: Para clonar os repositórios.

---

## Configuração Inicial

1. **Clone o Repositório Principal**

   ```bash
   git clone https://github.com/seu-usuario/tech_challenge_fase_3.git
   cd tech_challenge_fase_3
