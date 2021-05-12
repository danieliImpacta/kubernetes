# ESD21 - Infrastructure and Cloud Computing::: Kubernetes


### Aluna: 
##### Danieli Silva dos Santos


## Atividade:
Subir dois pods, nginx e mysql, mapeando a porta 80 do nginx para acesso externo ao cluster e permitir que o contêiner do nginx tenha comunicação de rede no contêiner mysql pela porta 3306. 
A atividade pode ser feita localmente (minikube), AKS (Azure), EKS (AWS) ou no GKE (GCP). 
Se quiser criar o cluster nuvem Kubernetes com Terraform é opcional. 

#### Tecnologias utilizadas:::
* Editor: Visual Studio Code
* Sistema operacional: Ubuntu
* Banco de dados: MySQL

#### Pré-requisitos:::
* Ter instalado o Terraform;
* Ter instalado Kubernetes;
* Ter Assinatura do Azure;
* Ter instalado a CLI do Azure.

#### Como Executar:::
## Provisionando o Cluster na Azure com Terraform:
* 1º - Efetue o clone do projeto com o seguinte comando: git clone https://github.com/danieliImpacta/Kubernetes.git;
* 2º - Navegue até o diretório clonado;
* 3º - Logar na conta azure: az login -u <email> -p <senha>;
* 4º - No terminal dentro do diretório clonado inicialize o projeto com o comando: terraform init;
* 5º - Após iniciar o projeto, no terminal digite terraform plan para efetuar a validação do código;
* 6º - A seguir digite terraform apply -auto-approve para criar a infraestrutura no Azure.
* 7º - Na conta da Azure verifique se o resource group e o cluster foram criados respectivamente, 'ResourceGroup' e 'KubernetesCluster'.

## Realizando deploy no Cluster criado:
* 1º - No terminal, conecte-se ao cluster criado na azure: az aks get-credentials --resource-group ResourceGroup --name KubernetesCluster;
* 2º - Suba os deployments criados a partir dos arquivos yaml: kubectl apply -f .\deployments\;
* 3º - Suba os serviços criados a partir dos arquivos yaml: kubectl apply -f .\services\;
* 4º - Execute o comando para verificar o status dos Pods: kubectl get all;
* 5º - No navegador, acesse o IP obtido no passo anterior, em caso de sucesso nos procedimentos anteriores, o navegador deverá redirecionar a pagina para a home do nginx.

