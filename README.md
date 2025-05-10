# AZ-204 - Guia de Estudo

## Resumo Rápido (TL;DR)

Este repositório foi criado com base nos meus estudos durante a preparação para a certificação Microsoft AZ-204. Ele reúne um guia prático e objetivo, com o intuito de ajudar outras pessoas a se prepararem de forma eficiente para o exame. Abaixo estão os tópicos cobrados no exame, distribuídos por área de conhecimento.

# Desenvolvendo Soluções para Microsoft Azure (AZ-204)

## 🔷 1. Desenvolver soluções de computação no Azure (25–30%)

### ▸ Implementar soluções conteinerizadas

- Criar e gerenciar imagens de container
- Publicar uma imagem no Azure Container Registry
- Executar containers usando Azure Container Instance
- Criar soluções com Azure Container Apps

### ▸ Implementar Azure App Service Web Apps

- Criar uma Web App no Azure App Service
- Configurar e implementar diagnósticos e logs
- Fazer deploy de código e containers
- Configurar TLS, configurações de API e conexões com serviços
- Implementar autoscaling
- Configurar deployment slots

### ▸ Implementar Azure Functions

- Criar e configurar um Azure Function App
- Implementar input e output bindings
- Implementar triggers com operações de dados, timers e webhooks

## 🟦 2. Desenvolver para armazenamento no Azure (15–20%)

### ▸ Desenvolver soluções que utilizam Azure Cosmos DB

- Realizar operações em containers e itens com SDK
- Definir nível de consistência apropriado para operações
- Implementar notificações com change feed

### ▸ Desenvolver soluções que utilizam Azure Blob Storage

- Definir e recuperar propriedades e metadados
- Realizar operações em dados utilizando SDK apropriado
- Implementar políticas de armazenamento e gerenciamento de ciclo de vida

## 🔐 3. Implementar segurança no Azure (15–20%)

### ▸ Implementar autenticação e autorização de usuários

- Autenticar e autorizar usuários utilizando Microsoft Identity Platform
- Autenticar e autorizar usuários e apps com Microsoft Entra ID
- Criar e implementar shared access signatures
- Implementar soluções que interajam com Microsoft Graph

### ▸ Implementar soluções seguras no Azure

- Proteger dados de configuração com App Configuration ou Azure Key Vault
- Desenvolver código que utilize chaves, segredos e certificados armazenados no Azure Key Vault
- Implementar Managed Identities para recursos do Azure

## 📈 4. Monitorar, diagnosticar e otimizar soluções no Azure (10–15%)

### ▸ Implementar cache para soluções

- Configurar políticas de cache e expiração com Azure Cache for Redis
- Implementar padrões seguros e otimizados de cache, considerando tamanho de dados, conexões, criptografia e expiração
- Implementar endpoints e perfis com Azure Content Delivery Network (CDN)

### ▸ Diagnosticar soluções com Application Insights

- Monitorar e analisar metrics, logs e traces
- Implementar testes e alertas com Application Insights
- Configurar um app ou serviço para usar Application Insights

## 🌐 5. Conectar e consumir serviços Azure e de terceiros (15–20%)

### ▸ Implementar API Management

- Criar uma instância do Azure API Management
- Criar e documentar APIs
- Configurar acesso às APIs
- Implementar políticas para APIs

### ▸ Desenvolver soluções baseadas em eventos

- Implementar soluções com Azure Event Grid
- Implementar soluções com Azure Event Hub

### ▸ Desenvolver soluções baseadas em mensagens

- Implementar soluções com Azure Service Bus
- Implementar soluções com filas do Azure Queue Storage

## 📚 Tópicos de Referência

- [Azure App Service Web Apps](https://docs.microsoft.com/en-us/azure/app-service/)
- [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/)
- [Azure Container Solutions](https://learn.microsoft.com/en-us/azure/containers/)
  - [Azure Container Registry](https://docs.microsoft.com/en-us/azure/container-registry/)
  - [Azure Container Instance](https://docs.microsoft.com/en-us/azure/container-instances/)
  - [Azure Container Apps](https://docs.microsoft.com/en-us/azure/container-apps/)
- [Azure Blob Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/)
- [Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/)
- [Microsoft Identity Platform](https://learn.microsoft.com/en-us/entra/identity-platform/)
  - [Azure Managed Identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
  - [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/)
- [Microsoft Graph](https://learn.microsoft.com/en-us/graph/)
- [Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/)
- [Azure App Configuration](https://learn.microsoft.com/en-us/azure/azure-app-configuration/)
- [Azure API Management](https://docs.microsoft.com/en-us/azure/api-management/)
- [Azure Cache for Redis](https://docs.microsoft.com/en-us/azure/azure-cache-for-redis/)
- [Azure CDN](https://docs.microsoft.com/en-us/azure/cdn/)
- [Azure Application Insights](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
- [Azure Event Grid](https://docs.microsoft.com/en-us/azure/event-grid/)
- [Azure Event Hub](https://docs.microsoft.com/en-us/azure/event-hubs/)
- [Azure Service Bus](https://docs.microsoft.com/en-us/azure/service-bus-messaging/)
- [Azure Queue Storage](https://docs.microsoft.com/en-us/azure/storage/queues/)

## 📌 Documentação das APIs

- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/reference-index?view=azure-cli-latest)
- [.NET API](https://learn.microsoft.com/en-us/dotnet/api/)
- [PowerShell](https://learn.microsoft.com/en-us/cli/azure/reference-index?view=azure-cli-latest)

## 📝 Preparação para o Exame

- [Simulador do Exame](https://aka.ms/examdemo)
- [Avaliações Práticas Microsoft](https://learn.microsoft.com/en-us/certifications/exams/az-204/practice/assessment?assessment-type=practice&assessmentId=35)
- [MeasureUp](https://www.measureup.com/catalogsearch/result/?q=az-204)
- [WhizLabs](https://www.whizlabs.com/microsoft-azure-certification-az-204/)
- [Learn Azure App](https://learnazure.app/)

## 📘 Recursos de Estudo

- [Trilha Oficial Microsoft Learn](https://learn.microsoft.com/en-us/certifications/exams/az-204/)
- [Repositório GitHub MicrosoftLearning AZ-204](https://github.com/MicrosoftLearning/AZ-204-DevelopingSolutionsforMicrosoftAzure)
- Exam Readiness Zone:
  - [Compute](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-204-develop-azure-compute-solutions-1-of-5)
  - [Storage](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-204-develop-for-azure-storage-segment-2-of-5)
  - [Security](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-204-implement-azure-security-segment-3-of-5)
  - [Monitoring](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-204-monitor-troubleshoot-and-optimize-azure-solutions-segment-4-of-5)
  - [API e Integrações](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/preparing-for-az-204-connect-to-and-consume-azure-services-and-third-party-services-segment-5-of-5)
- [Microsoft Applied Skills](https://learn.microsoft.com/en-us/credentials/browse/?credential_types=applied%20skills)
- [Azure Sandbox Environment](https://github.com/Azure-Samples/azuresandbox) *(requer pagamento)*
