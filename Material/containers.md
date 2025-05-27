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

## Terminologia
- **Registry**: Serviço para armazenar imagens de containers
- **Repository**: Grupo de imagens de containers relacionados
- **Image**: Snapshot pontual de um container compatível com Docker
- **Container**: Aplicação com suas dependências executando em um ambiente isolado

## Trabalhando com Containers no Azure

### Azure Container Registry - ACR
Seviço baseado em docker que realiza o armazenamento e gestão de imagens de container privado, que permite criar, armazenar e gerenciar imagens de container em uma plataforma privada para qualquer tipo de implementação de container. Ele é essencial para o desenvolvimento e implementação de aplicações em contêineres, facilitando o acesso e a gestão de imagens e artefatos relacionados.

   Demais características:
   - Integração com Pipelines de Desenvolvimento e Implementação: Pode ser usado com os pipelines de desenvolvimento e implementação de contêineres existentes.
   - Tarefas de Build Automática: Permite construir imagens de contêiner a pedido ou automatizar a construção com base em atualizações de código fonte, atualizações de imagem base ou temporizadores. 
   - Requisitos de Rede: Permite definir regras de rede para controlar o acesso ao registro de contêineres e implementar segurança. 
   - Replicação Geográfica: Suporta a replicação geográfica em várias regiões Azure, aumentando a disponibilidade e a resiliência. 
   - Assinatura de Imagens: Permite assinar imagens com o Docker Content Trust, garantindo a integridade e autenticidade.
   - Formas de criar
     - Azure CLI
     - Azure Portal
     - APIs
     - Extensões como o Docker Extension e Azure Account Extension para Visual Studio Code
     - Suporte a imagens tanto de Windows quanto de Linux. 
   - Namespaces de Repositórios: Permite o compartilhamento de um registro entre grupos ou equipes, com suporte a namespaces aninhados para isolamento. 
   - Criação de Imagens: Oferece suporte à criação automatizada de imagens de contêineres com o comando `az acr build`.
  
  ### Azure Container Instances - ACI
   Utilizado para implantar containers rapidametne sem ter que tratar infraestrutura adicional

 ### Azure Container Apps
   Serviço Gerenciado para rodar aplicativos baseados em containers com recursos de escalabilidade automática e arquitetura Event-Driven (Orientada a eventos)

 ### Azure Kubernetes Service - AKS
   Plataforma gerenciada para execução e gerenciamento de clusters Kubernetes

 ### Docker
   Utilizado principalmente como ferramenta de desenvolvimento local, criação e teste das imagens de aplicações antes do
   deploy no Azure

 ### CLI 
   Interface de linha de comando oferecida pela Microsoft para gerenciar recursos do Azure de maneira rápida, scriptável e
   automatizada. Ela não é exclusiva para containers, mas é amplamente usada para gerenciar serviços e ambientes de
   containers no Azure
