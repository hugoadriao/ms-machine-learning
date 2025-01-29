# Passo a passo para utilizar o Azure Machine Learning

## Passo 1: Criar o recurso do Azure Machine Learning

### 1.1 Acessar o portal do Azure
- [https://portal.azure.com/](https://portal.azure.com/)

### 1.2 Criar um novo recurso
- ![Criar um novo recurso](assets/new_resource_options.png)

### 1.3 Pesquisar por "Azure Machine Learning" no Marketplace
- ![Marketplace](assets/marketplace_ml.png)

### 1.4 Criar o tipo de recurso "Azure Machine Learning"
- ![Create Azure Machine Learning](assets/create_azure_ml.png)

### 1.5 Preencher os campos obrigatórios
- No primeiro acesso não haverá um "Resource Group", basta criar um novo em "Create new" e inserir
o nome desejado.
- ![Fill required fields](assets/fill_required_fields.png)
- Insira o nome do Workspace, deixe a região como "East US".
- Os campos "Storage account", "Key Vault" e "Application Insights" serão preenchidos
automaticamente após editar o nome do recurso, dessa maneira não é necessário preencher.
- "Container registry" é o repositório de imagens do Docker, deixe como "None".
- As outras abas não precisam de alterações, basta clicar em "Review + create" e "Create".
- Agora é só esperar a criação dos recursos.
- ![Wait for resources](assets/wait_for_resources.png)
- Basta acessar o recurso criado clicando em "Go to resource" e depois em "Launch Studio".
- ![Go to resource](assets/go_to_resource.png)
- ![Launch Studio](assets/launch_studio_3.png)
- Também é possível acessar o Studio através de "All resources" e acessar o recurso criado.
- ![Launch Studio](assets/launch_studio.png)
- ![Launch Studio 2](assets/launch_studio_2.png)

## Passo 2: Criar um novo Trabalho de Machine Learning

### 2.1 Criar um novo "Job"
- Selecionar "Jobs" no menu lateral.
- ![Select Jobs](assets/left_menu_jobs.png)
- Clicar em "Create" e em "Automated ML job".
- ![Create a new job](assets/create_new_job.png)

#### 2.1.1 Select data asset
- Caso já exista um data asset, selecione-o e clique em "Next".
- ![Select data asset](assets/select_data_asset.png)
- Para criar um novo data asset, clique em "Create" e seguir os passos de 2.1.1.1 a 2.1.1.7.
- ![Create data asset](assets/create_data_asset.png)

##### 2.1.1.1 Data Type
- Preencha o campo "Name" com o nome desejado e clique em "Next".
- ![Fill data asset name](assets/data_asset_1.png)

##### 2.1.1.2 Data Source
- Na tela seguinte, selecione "From local files" e clique em "Next".
- ![Select data source](assets/data_source_local_files.png)

##### 2.1.1.3 Destination storage type
- Em "Datastore type" deixe como "Azure Blob Storage".
- E em seguida selecione o blob do workspace e clique em "Next".
- ![Destination storage type](assets/destination_storage_type.png)

##### 2.1.1.4 File or folder selection
- Faça o download do arquivo .zip contendo um arquivo CSV e um arquivo MLTable do link
[https://aka.ms/bike-rentals](https://aka.ms/bike-rentals)
- Faça a extração da pasta.
- Selecione "Upload files or folder" e em seguida clique em "Upload files". Navegue até a pasta
extraída no passo anterior e selecione o arquivo CSV. Clique em "Next" e finalize a carga dos dados.
- ![File or folder selection](assets/file_or_folder_selection.png)

##### 2.1.1.5 Settings
- Em "File format" deixe como "Delimited".
- Em "Delimiter" deixe como "Comma".
- Em "Encoding" deixe como "UTF-8".
- Em "Column headers" deixe como "Only first file has headers".
- Em "Skip rows" deixe como "None".
- ![Settings](assets/data_settings.png)
- Clique em "Next".

##### 2.1.1.6 Schema
- Não é necessário alterar nada.
- Clique em "Next".

##### 2.1.1.7 Review
- Clique em "Create".

#### 2.1.2 Configure job
- Dê um nome para o experimento em "New experiment name".
- Selecione a coluna "rentals" como "Target column".
- Selecione o cluster em "Select Azure ML compute cluster"
- ![Configure job](assets/configure_job.png)
- Clique em "Next".
- Caso não exista um cluster, clique em "New" e siga os passos de 2.1.2.1 a 2.1.2.2.
- ![New cluster](assets/new_cluster.png)

##### 2.1.2.1 Virtual Machine
- Selecione as opções como na imagem abaixo.
- ![Virtual Machine](assets/virtual_machine.png)
- Clique em "Next".

##### 2.1.2.2 Advanced Settings
- Dê um nome para o cluster em "Compute name" e clique em "Create".
- ![Advanced Settings](assets/advanced_settings.png)
- Clique em "Next".

#### 2.1.3 Select task and settings
- Basta selecionar "Regression" e em seguida "View additional configuration settings". Faça o mesmo
que descrito no passo 2.1.3.1 e em seguida clique em "Next".
- ![Select task and settings](assets/select_task_and_settings.png)

##### 2.1.3.1 Additional configuration settings
- Selecione as opções como na imagem abaixo.
- ![Additional configuration settings](assets/additional_configuration_settings.png)
- Clique em "Save".

#### 2.1.4 Validate and test
- Altere "Validation type" para "Train-validation split", "Percentage validation of data" deixe em
"10" e "Test data asset (preview)" deixe em "No test data asset required".
- ![Validate and test](assets/validate_and_test.png)
- Clique em "Finish".
- E é só aguardar o término do trabalho.
- ![Job finished](assets/job_finished.png)

## Passo 3: Criar Endpoints
### Problemas:
- Erro no processo de criar subscrição free tier.
- ![Erro free tier](assets/error_free_tier.png)
- Devido esse problema fui obrigado a criar uma subscrição de estudante.
- ![Subscrição de estudante](assets/student_subscription.png)
- Essa subscrição não permite criar endpoints.
- ![Erro endpoints azure](assets/error_endpoints_azure.png)
- Ao seguir todos os passos da documentação encontrada no [link](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-deploy-online-endpoints?view=azureml-api-2&tabs=python) tive o mesmo erro ao tentar criar um endpoint.
- ![Erro endpoints](assets/error_endpoints.png)
- Foi aberto um ticket de suporte para corrigir o erro da criação do free tier a fim de criar um endpoint de teste do modelo. Mediante a resolução do problema central este projeto será atualizado.
