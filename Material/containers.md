# Containers

## Definição  - O que é um container?
De modo simples, é um unidade isolada de software, nela tem somente as dependências, código e arquivos de configuração 
que uma aplicação precisa para funcionar. Os containers permitem que aplicações possam rodar de maneira rápida e confiável 
em qualquer ambiente computacional sem que precise de um sistema operacional completo.
Em um container essencialmente temos:
 - Código da aplicação
 - Libs e dependências
 - Ambiente de execução (_runtime_)

## Características
Os containers podem ser executados em qualquer ambiente desde que tenha um runtime compatível como o Docker por exemplo. 
Os containers proporcionam maior segurança e controle isolando as aplicações entre si e do sistema operacional, e também são 
mais leves que VMs, pois seu início é mais rápido e por utilizar menos recursos.

## Trabalhando com Containers no Azure
 - **Azure Container Registry - ACR**: 
   Seviço baseado no Docker, utilizado para armazenar e gerenciar imagens Docker já existentes ou também para criar novas
   imagens no Azure
 - **Azure Container Instances - ACI**: 
   Utilizado para implantar containers rapidametne sem ter que tratar infraestrutura adicional
 - **Azure Container Apps**: 
   Serviço Gerenciado para rodar aplicativos baseados em containers com recursos de escalabilidade automática e arquitetura Event-Driven (Orientada a eventos)
 - **Azure Kubernetes Service - AKS**:
   Plataforma gerenciada para execução e gerenciamento de clusters Kubernetes
 - **Docker**:
   Utilizado principalmente como ferramenta de desenvolvimento local, criação e teste das imagens de aplicações antes do
   deploy no Azure
 - **CLI**: 
   Interface de linha de comando oferecida pela Microsoft para gerenciar recursos do Azure de maneira rápida, scriptável e
   automatizada. Ela não é exclusiva para containers, mas é amplamente usada para gerenciar serviços e ambientes de
   containers no Azure
