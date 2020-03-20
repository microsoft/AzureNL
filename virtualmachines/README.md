# Virtual machines

https://docs.microsoft.com/en-us/cli/azure/azure-cli-vm-tutorial?tutorial-step=2&view=azure-cli-latest

## Introduction
This script will help you create a virtual machine in Azure and its dependencies. A virtual machine lives in a subnet in a virtual network and it can be reached using a public ip address. For simplicity this is the first approach.

A security best practice is to not connect directly to over SSH/RDP but use a jumpbox like Azure Bastion in between. This will be the second approach.

## Resource group

``` 
rgname=azvm
location=westeurope
az group create -n $rgname -l $location 
```

## Virtual network

Text

``` 
vnetname=azvnet
az network vnet create -g $rgname -n $vnetname
```

## Public IP

Text

``` az network public-ip create ```

## Bastion

Text

``` az network bastion create ```

## VM

Text

(DevTest Labs)