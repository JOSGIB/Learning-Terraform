### [Terraform with Azure [ARM Templates]](https://github.com/hashicorp/terraform-provider-azurerm/tree/main/examples)

*Azure ARM Templates*
> With Azure you can have templates called **ARM [Azure Resource Manager]** that are formatted files, using JSON or YAML, to define the infrastructure and configuration of the Azure solution

*Using ARM with Terraform*
1. Use Terraform to delpoy ARM templates
2. Use ARM templates to deploy Terraform configuration file
3. Use Terraform to manage ARM template resources

<br/>

##### ARM template in YAML
```
  # Define template schema and version
  $schema: "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#"
  contentVersion: "1.0.0.0"

  # Define variables used in the template
  variables:
    storageAccountName: "mystorageaccount"
    containerName: "mycontainer"

  # Define resources that will be created
  resources:
  - type: "Microsoft.Storage/storageAccounts"
    name: "[variables('storageAccountName')]"
    apiVersion: "2019-06-01"
    location: "West US"
    sku:
      name: "Standard_LRS"
    kind: "StorageV2"

  - type: "Microsoft.Storage/storageAccounts/blobServices/containers"
    name: "[concat(variables('storageAccountName'), '/default/', variables('containerName'))]"
    apiVersion: "2019-06-01"
    properties:
      publicAccess: "Container"

  # Outputs that can be queried after deployment
  outputs:
    storageAccountName:
      value: "[variables('storageAccountName')]"
    containerName:
      value: "[variables('containerName')]"
```