# Visão Geral - Soluções de Computação no Azure

| Serviço                       | Quando utilizar?                                                                                       | Recursos principais                                                          | Considerações importantes                           |
|-------------------------------|--------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|-----------------------------------------------------|
| **Azure Container Apps**      | Microsserviços modernos e apps baseados em containers, sem necessidade direta do Kubernetes            | Escalabilidade automática, balanceamento embutido, apps orientados a eventos | Sem acesso direto às APIs nativas do Kubernetes     |
| **Azure App Service**         | Hospedagem gerenciada de aplicações web tradicionais (sites e APIs web)                               | Auto-escalabilidade, integração simplificada com Azure, suporte stateful     | Melhor opção para aplicações web convencionais      |
| **Azure Container Instances** | Execução rápida e simples de containers individuais, testes pontuais ou tarefas rápidas                | Container dedicado sem escalabilidade automática ou balanceamento             | Ideal para soluções pontuais e testes rápidos       |
| **Azure Kubernetes Service**  | Aplicações que exigem controle completo e acesso às APIs nativas do Kubernetes                         | Gerenciamento total de Kubernetes, suporta cargas stateful e stateless       | Necessita de conhecimento avançado em Kubernetes    |
| **Azure Functions**           | Aplicações orientadas a eventos, serverless, com execução rápida e curta duração                       | Execução leve, escalabilidade automática por consumo                         | Não é uma solução baseada em containers             |

## Comparações rápidas entre serviços

### Azure Container Apps vs. AKS
- **AKS:** Utilize quando precisar acessar diretamente o controle e as APIs do Kubernetes.
- **Container Apps:** Ideal para simplicidade e menor complexidade de gerenciamento.

### Azure Container Instances vs. Container Apps
- **ACI:** Opção básica e rápida, sem recursos avançados como escalabilidade ou balanceamento de carga.
- **Container Apps:** Oferece recursos avançados como escalabilidade automática e balanceamento embutido.

### Azure Functions vs. Container Apps
- **Functions:** Otimizado para execuções rápidas e breves.
- **Container Apps:** Indicado para cenários mais amplos e processos de maior duração.

## Comparação detalhada por recurso

| Recurso                  | Azure Container Apps       | Azure Container Instances | Azure App Service               | Azure Kubernetes Service (AKS)     | Azure Functions              |
|--------------------------|----------------------------|--------------------------|---------------------------------|------------------------------------|-------------------------------|
| **Escalabilidade**       | Automática                 | Manual apenas            | Automática                      | Automática (Cluster Autoscaler)    | Automática baseada em consumo |
| **Gerenciamento de Estado** | Stateless                  | Stateless                | Stateless e Stateful             | Stateless e Stateful               | Stateless                     |
| **Isolamento de Recursos** | Compartilhado              | Dedicado                 | Compartilhado ou dedicado       | Dedicado                           | Compartilhado                 |
| **Modelo de Custo**      | Pagamento sob demanda      | Pagamento sob demanda    | Fixo + Escala                   | Custos de cluster e nós            | Pagamento sob demanda ou fixo |
| **Suporte Multi-Região** | Não                        | Não                      | Sim                             | Sim                                | Sim                           |

> **Nota:** Azure Functions não é uma solução baseada em containers.

