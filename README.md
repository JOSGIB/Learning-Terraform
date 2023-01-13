# [TERRAFORM](https://www.terraform.io/)
> An open-source tool used for provisioning and managing cloud infrastructure

<br/>

| Terraform Providers           | Documentation                                                                           |
| :---------------------------: | :-----------:                                                                           |
| Amazon Web Services [AWS]     | [click here](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)         |
| Microsoft Azure               | [click here](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)     |
| Google Cloud Platform [GCP]   | [click here](https://registry.terraform.io/providers/hashicorp/google/latest/docs)      |
| Kubernetes                    | [click here](https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs)  |
| GitHub                        | [click here](https://registry.terraform.io/providers/integrations/github/4.2.0/docs)    |
| Splunk                        | [click here](https://registry.terraform.io/providers/splunk/splunk/1.0.0/docs)          |
| Docker                        | [click here](https://registry.terraform.io/providers/kreuzwerker/docker/2.8.0/docs)     |
| Oracle Cloud Infrastructure   | [click here](https://registry.terraform.io/providers/oracle/oci/latest/docs)            |

<br/>

*How Does Terraform Work?* 
> Creates and manages resource with your selected provider using Terraform to call the API interfaces. As well, the selected provider allows you to work with the platform or service that has an API that is accessible.

*Terraform Stages*
- Write
  - Define the infrastructure within a Terraform Config file
- Plan
  - Review changes that will be conducted
- Apply
  - Provision your infrastructure and update the state file

*Terraform Workflow* 
- Step 1 [**Terraform Init**]
    - Used to initialize the working directory that contains the Terraform configuration files
- Step 2 [**Terraform Plan**]
  - Terraform will create an execution plan. You can see the changes Terraform is going to make to your infrastructure based on the configuration file
- Step 3 [**Terraform Apply**]
  - Execute the actions in the Terraform plan
- Step 4 [**Terraform Destroy**]
  - Destory your infrastructure objects based on the Terraform configuration 

#### Terraform Configuration File
> Tells Terraform how to manage the infrastructure

#### Terraform Blocks
> Used to represent the configuration of an object

#### Terraform Resource Block
> Used to represent the infrastructure you want to deploy

---

##### Terraform using Mircosoft Azure
```
  terraform {
    required_providers {
        azurem = {
            source = "hashicorp/azurerm"
            version = "2.92.0"
        }
    }
  }  

  provider "azurerm" {
    subscription_id = "AZURE_SUBSCRIPTION_ID"
    client_id       = "AZURE_CLIENT_ID"
    client_secret   = "AZURE_CLIENT_SECRET"
    tenant_id       = "AZURE_TENANT_ID"
    features {}
  }

  resource "azurerm_resource_group" "app-grp" {
    name = "app-grp"
    location = "North Europe"
  }
```
