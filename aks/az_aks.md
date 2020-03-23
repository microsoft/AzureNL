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

1. Multiple node pools

Multiple node pools using Virtual Machine Scale Sets is interesting since it enables lots of additional features. VMSS allow autoscaling of cluster nodes. Multiple pools of nodes allow combining different vm sizes, for specific workloads like GPU, and also different operating systems, like adding Windows workers. It also allows for different Kubernetes upgrade paths and rhythms, where a temporary pool can be used to test the workload on a newer Kubernetes version. Finally you can add Azure Container Instances as virtual nodes to a cluster to get serverless workers.

https://docs.microsoft.com/en-us/azure/aks/use-multiple-node-pools
```
az aks create \
    --resource-group $resourcegroupname \
    --name $aksname \
    --vm-set-type VirtualMachineScaleSets \
    --node-count 2 \
    --generate-ssh-keys \
    --kubernetes-version 1.14.8 \
    --load-balancer-sku standard
```
This results in a cluster with one node pool as VM Scale Set. You can then create another node pool with a different vm size to accommodate specific requirements for a workload. 

```
az aks nodepool list --resource-group $resourcegroupname --cluster-name $aksname

az aks show --resource-group $resourcegroupname --name $aksname --query agentPoolProfiles

az aks scale --resource-group $resourcegroupname --name $aksname --node-count 4

az aks scale --resource-group $resourcegroupname --name $aksname --node-count 2 --nodepool-name nodepool1

az aks nodepool add --resource-group $resourcegroupname --cluster-name $aksname --name nodepool2 --node-count 1 --kubernetes-version 1.14.7 --node-vm-size Standard_D2s_v3
```

# TODO

This section needs additional work, since it requires the Azure network plugin + subnets

2. Virtual nodes

https://docs.microsoft.com/en-us/azure/aks/virtual-nodes-cli

```
az aks enable-addons --resource-group $resourcegroupname --name $aksname --addons virtual-node 
--subnet-name myVirtualNodeSubnet
```

3. Windows

https://docs.microsoft.com/en-us/azure/aks/windows-container-cli

PASSWORD_WIN="enter here"

```
az aks create --resource-group $resourcegroupname --name $aksname --node-count 2 --enable-addons monitoring --kubernetes-version 1.14.8 --generate-ssh-keys --windows-admin-password $PASSWORD_WIN --windows-admin-username azureuser --vm-set-type VirtualMachineScaleSets --load-balancer-sku standard --network-plugin azure
```


policies

devspaces

agwic





See this for more info on [choosing vm sizes](./choose_vm_size.md).

2.	Software dependencies

All dependencies are managed by the Azure cloud shell, so no need to do anything. If you want to do this the hard way, follow instructions in references below at aks create walkthrough. 

# References
- [az aks create](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-create)
- [aks best practices](https://docs.microsoft.com/en-us/azure/aks/best-practices)
- [aks networking](https://docs.microsoft.com/en-us/azure/aks/concepts-network)
- [aks create walkthrough](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough)