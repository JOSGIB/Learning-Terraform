### [Terraform with Azure [Kubernetes]](https://github.com/hashicorp/terraform-provider-kubernetes/tree/main/_examples/aks)

Kubernetes
> Open-source platform for automating the deploymen,scaling, and management of containerized applications
###### Features
- Automatice Scaling
- Self-Healing
- Rolling Updates and Rollbacks
- Service Discovery and Load Balancing
- Automated Rollouts and Rollbacks
- Namespaces
- Custom Resource Definitions
- Multi-Cloud and Hybrid

Kubernetes Cluster
> A set of machines used to run containerized applications. Made of both nodes and control plane componets to manage the state of the cluster
###### Features
- On-Premesis or Cloud
- Deploy, Scale, Manage Containerized Applications
- Applications deployed in the form of "pods"
- Kubernetes Objects
    - Services
    - Replication Controller and Deployment
    - Stateful Sets
    - Daemon Sets

Azure Kubernetes Service [AKS] Cluster
> Kubernetes cluster in the Azure cloud, to deploy and manage containerized applications without the understanding of the underlying infrastructure
###### Features
- Create and Manage Kubernetes Clusters
- Deploy and Scale Applications
- Integrate with Azure Services
    - Azure Container Monitor
    - Azure Container Registry
    - Azure Dev Spaces
- Azure provisions and manages the control plane and worker nodes
- Additional Features
    - Advance Networking, Monitoring, Logging, Security
        - Azure AD Integration
        - Azure Policy for Kubernetes
        - Kubernetes Network Policies

<br/>

##### Terraform Config [create AKS cluster]
```
  provider "azurerm" {
    subscription_id = "YOUR_SUBSCRIPTION_ID"
    client_id       = "YOUR_CLIENT_ID"
    client_secret   = "YOUR_CLIENT_SECRET"
    tenant_id       = "YOUR_TENANT_ID"
  }

  resource "azurerm_resource_group" "example" {
    name     = "example-rg"
    location = "westus2"
  }

  resource "azurerm_kubernetes_cluster" "example" {
    name                = "example-aks"
    location            = azurerm_resource_group.example.location
    resource_group_name = azurerm_resource_group.example.name
    dns_prefix          = "example-aks"

    linux_profile {
      admin_username = "azureuser"

      ssh_key {
        key_data = "YOUR_SSH_PUBLIC_KEY"
      }
    }

    agent_pool_profile {
      name      = "default"
      count     = 1
      vm_size   = "Standard_DS2_v2"
    }
  }
```

###### AKS Cluster using Terraform Settings
- Authentication and Authorization
    - Use Azure Active Directory (AAD)
        - Specify AAD Server app ID
        - Specify AAD Server app Secret
- Node Pools
    - Config multiple node pools
        - Number of nodes
        - Size of nodes
        - Availability Zones
- Kubernetes Version
- Network
    - Virtual Network and Subnet
    - Network Plugins
        - Azure CNI
        - Kubenet
- Add-On
    - Enable or Disable add-ons
        - Kubernetes Dashboard
        - HTTP Application Routing
        - Automatic Sidecar Injection
- Logging and Monitoring
    - Enable logging and monitoring
        - Cluster-Level Logging
        - Container-Level Logging
    - Integrate Azure Monitor for Containers
        - View Metrics
        - View Logs
        - View Traces
- Advanced Networking
    - Configure Advance Networking
        - Network Policies
        - Service Mesh
        - Ingress Controller
- Identity
    - Assign system-assigned identity
- Advance Security
    - Enable AKS Advanced Networking Add-On
        - Enabling Kubernetes Network Policy
        - Enabling Azure Policy for Kubernetes

---

### Kubernetes with Azure Dev Space

Azure Dev Space
> Azure Kubernetes Service [AKS] feature allowing you to develop, test, and debug containerized applications in a Kubernetes cluster

> Allowing developers to create isolated, team-specific development spaces with shared AKS cluster, and work or test code inside a Kubernetes environment.

###### Azure Dev Space Features
- Code Editing and Debugging
    - Developing and Testing inside the Kubernetes cluster
- Instant Feedback
    - See changes they make to thier code in real-time
- Isolation and Collaboration
    - Isolates Development Environment
        - Dev teams works on same cluster without interferences
- Integration with Azure DevOps
    - Test and Debug Code in the Pipline
- Automatic Scaling
    - Scales number of replicas based on demand

###### Azure Dev Space to Manage Kubernetes Cluster Steps
Using tools, such as ARM templets and Terraform

- Create AKS Cluster with ARM Template
    - Creates AKS Cluster
    - Provision Necessary Resources
- Enable Azure Dev Spaces on AKS Cluster
    - Using Azure CLI or Azure Portal
- Create a Dev Space with Terraform
- Use VS Code or Azure DevOps to develop and test application
- Deploy Application to the Dev Space with Terraform
- Debug and Test Application
    - Azure CLI to Debug
    - Dev Space for Testing
- Deploy Application to Production with Terraform

###### Steps Summary
> Use Azure Dev Spaces with ARM templates and Terraform to automate the management of Kubernetes Clusters in Azure
>
> Using ARM templates to provision the resources.
>
> Using Terraform to create and manage the dev spaces, and deply and update the application.