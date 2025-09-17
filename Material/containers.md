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

#### Criando um Container Registry com Azure CLI
Instalar Azue CLI: https://learn.microsoft.com/pt-br/cli/azure/?view=azure-cli-latest

`curl -L https://aka.ms/InstallAzureCli | bash`
```sh
# Login
az login

# (Opcional) Seleciona a subscription
az account set --subscription "<SUBSCRIPTION_ID_OU_NOME>"

# Variáveis
resourceGroup=rg-myapp-dev-eus
location=eastus
registryName=acrmyappdeveus   # minúsculo, único globalmente

# Cria o Resource Group (se não existir)
az group create --name "$resourceGroup" --location "$location"

# (Opcional) Registrar o provider (normalmente já vem registrado)
az provider register --namespace Microsoft.ContainerRegistry

# Cria o ACR (SKU Standard é bom para a maioria dos casos)
az acr create \
  --resource-group "$resourceGroup" \
  --name "$registryName" \
  --sku Standard

# Login no ACR (token do az login ~3h)
az acr login --name "$registryName"

# (Opcional) Regras de rede: negar por padrão e liberar IPs específicos
# az acr network-rule update -n "$registryName" --resource-group "$resourceGroup" --default-action Deny
# az acr network-rule add -n "$registryName" --resource-group "$resourceGroup" --ip-address 203.0.113.10/32

# (Opcional) Política de retenção (ex.: manter 10 tags por repositório, 30 dias)
# az acr config retention update -r "$registryName" --status Enabled --days 30 --type UntaggedManifests
# az acr config retention update -r "$registryName" --status Enabled --days 30 --type TaggedManifests --count 10

# (Opcional) Habilitar Content Trust (assinatura de tags)
# az acr config content-trust update -r "$registryName" --status enabled
```

#### PowerShell
Requisitos: Módulos Az instalados
```sh
Install-Module Az -Scope CurrentUser
```

```sh
# Login
Connect-AzAccount

# (Opcional) Seleciona a subscription
Set-AzContext -Subscription "<SUBSCRIPTION_ID_OU_NOME>"

# Variáveis
$resourceGroup = "rg-myapp-dev-eus"
$location      = "EastUS"
$registryName  = "acrmyappdeveus"   # minúsculo, único globalmente (5-50 chars, [a-z0-9])

# Cria o Resource Group (se não existir)
New-AzResourceGroup -Name $resourceGroup -Location $location | Out-Null

# (Opcional) Registrar o provider (geralmente já vem registrado)
Register-AzResourceProvider -ProviderNamespace "Microsoft.ContainerRegistry" | Out-Null

# Cria o ACR (SKU Standard atende a maioria dos cenários)
New-AzContainerRegistry `
  -ResourceGroupName $resourceGroup `
  -Name $registryName `
  -Sku Standard `
  -Location $location | Out-Null

# --- Login no ACR ---
# Opção recomendada (interativo): usa token (~3h) via Azure CLI
az acr login --name $registryName

# --- Opcionais úteis ---

# (Opcional) Regras de rede / firewall
#   Não há cmdlet Az específico para todas as regras do ACR.
#   Use Azure CLI a partir do PowerShell (se quiser negar acesso por padrão e liberar IPs específicos):
# az acr network-rule update -n $registryName --resource-group $resourceGroup --default-action Deny
# az acr network-rule add    -n $registryName --resource-group $resourceGroup --ip-address 203.0.113.10/32

# (Opcional) Política de retenção (ex.: manter 10 tags por repositório, 30 dias)
# az acr config retention update -r $registryName --status Enabled --days 30 --type UntaggedManifests
# az acr config retention update -r $registryName --status Enabled --days 30 --type TaggedManifests --count 10

# (Opcional) Content Trust (assinatura/verificação de tags)
# az acr config content-trust update -r $registryName --status enabled

# (Opcional) Admin user (⚠️ geralmente manter desabilitado)
# Update-AzContainerRegistry -ResourceGroupName $resourceGroup -Name $registryName -AdminUserEnabled $true
# $cred = Get-AzContainerRegistryCredential -ResourceGroupName $resourceGroup -Name $registryName
# docker login "$($registryName).azurecr.io" -u $($cred.Username) -p $($cred.Password)

# (Opcional) Identidade para CI/CD (ex.: conceder AcrPull/AcrPush a um SP/Managed Identity)
# New-AzRoleAssignment -ObjectId "<OBJECT_ID_DA_IDENTIDADE>" -RoleDefinitionName "AcrPull" -Scope "/subscriptions/<SUB>/resourceGroups/$resourceGroup/providers/Microsoft.ContainerRegistry/registries/$registryName"
# New-AzRoleAssignment -ObjectId "<OBJECT_ID_DA_IDENTIDADE>" -RoleDefinitionName "AcrPush" -Scope "/subscriptions/<SUB>/resourceGroups/$resourceGroup/providers/Microsoft.ContainerRegistry/registries/$registryName"
```
#### Push e Execução de Imagens no ACR
```sh
# Puxa a imagem hello-world do repositório público da Microsoft
docker pull mcr.microsoft.com/hello-world

# Define variáveis
repository=demo
imageName=hello-world
tag=v1

# Marca a imagem com o endpoint do ACR
docker tag mcr.microsoft.com/hello-world $registryName.azurecr.io/$repository/$imageName:$tag

# Faz push da imagem para o ACR
docker push $registryName.azurecr.io/$repository/$imageName:$tag
```
```sh
# Executar localmente (puxando do ACR)
docker run $registryName.azurecr.io/$repository/$imageName:$tag

# Alternativa: executar diretamente via ACR Task
az acr run --registry $registryName \
  --cmd '$registryName.azurecr.io/$repository/$imageName:$tag' /dev/null
```
```sh
# Lista todos os repositórios
az acr repository list --name $registryName --output table

# Lista todas as tags de um repositório específico
az acr repository show-tags --name $registryName --repository $repository --output table
```

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
