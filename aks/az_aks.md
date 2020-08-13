# Azure Kubernetes Service 

## Introduction
This is a walkthrough of creating an Azure Kubernetes Cluster through the command-line interface.

## Getting Started
The easiest way to do this is to use the Azure cloud shell, either available through the icon at the top bar in the [Azure portal](https://portal.azure.com) or at https://shell.azure.com

# Simple deployment
[Azure Active Directory Service Principal](https://docs.microsoft.com/en-us/azure/aks/kubernetes-service-principal)

At this point you want to make some choices regarding the details of your cluster. I am going to go with a default setup that I like, and you can have your own requirements or preferences.

One thing to do is to check the latest and other supported versions of Kubernetes in AKS. 

```
az aks get-versions --location $region --output table

```
And then set the version in your script

```
kubernetesversion=1.16.7

az aks create --resource-group $resourcegroupname --name $aksname --generate-ssh-keys --kubernetes-version $kubernetesversion --node-vm-size Standard_B2ms --node-count 2 
```

# Advanced deployments

Lots of things in development. See a list of all features available:
```
az feature list -o table --query "[?contains(name, 'Microsoft.ContainerService')].{Name:name,State:properties.state}"
```

# TODO

agic managed
bastion
aad v2

azure policy 
auth ip ranges

See this for more info on [choosing vm sizes](./choose_vm_size.md).

# Software dependencies

All dependencies are managed by the Azure cloud shell, so no need to do anything. If you want to do this the hard way, follow instructions in references below at aks create walkthrough. 

# References
- [az aks create](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-create)
- [aks best practices](https://docs.microsoft.com/en-us/azure/aks/best-practices)
- [aks networking](https://docs.microsoft.com/en-us/azure/aks/concepts-network)
- [aks create walkthrough](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough)
