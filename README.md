# AzureNL  

## Introduction
This repo contains Azure samples of all sorts. 

## People
This repo is a team effort, mostly by Microsoft employees in the Netherlands who work with Azure. Here you see an overview of [Users](./users.md).

# Content
## Getting started
To follow along in this repo you will be interacting with Microsoft Azure, and specifically the Azure resource manager (ARM) API. 

0. Prerequisites

Azure subscription

[Azure Active Directory Service Principal](https://docs.microsoft.com/en-us/azure/aks/kubernetes-service-principal)

1.	Installation

Services in Azure are bundled in resource groups, which can be created, deployed, deleted, managed as one. 

See this for more info on [Azure regions](https://azure.microsoft.com/en-us/global-infrastructure/locations/)

```
resourcegroupname=myrg
region=westeurope
az group create --name=$resourcegroupname --location=$region

```


## Azure Services
The repo contains sections/folders grouped by Azure service. Each of these sections are independent and describe how you can get started themselves.
* [VM](./virtualmachines)
* [AKS](./aks)
* [App service](./appservice)
* Etc

## Third party solutions

* [Pega on AKS](./3rdparty/pega)

# Contribute
Feel free to contribute. Create an issue or pull request.  
When you want to create a new section for a missing service, please reuse the [Template](./_template).
