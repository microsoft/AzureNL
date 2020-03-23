# AzureNL  

## Introduction
This repo contains Azure samples of all sorts. 

## People
This repo is a team effort, mostly by Microsoft employees in the Netherlands who work with Azure. Here you see an overview of [Users](./users.md).

## Getting started
To follow along in this repo you will be interacting with an Microsoft Azure subscription and the Azure resource manager (ARM) API. 

* Azure subscription
  * Use [your existing subscription](https://portal.azure.com)
  * Create [a trial subscription](https://azure.microsoft.com/free)
  * Use [my visual studio benefits](https://my.visualstudio.com/Benefits)
* Access to Azure Powershell, Azure command-line interface or Azure Cloud Shell. To see them in action, have a look at [Accessing Microsoft Azure using powershell or cli from Windows and Linux in Windows Terminal](https://youtu.be/qBS_Knxaz5A).

<a href="http://www.youtube.com/watch?feature=player_embedded&v=qBS_Knxaz5A
" target="_blank"><img src="http://img.youtube.com/vi/qBS_Knxaz5A/0.jpg" 
alt="Accessing Microsoft Azure using powershell or cli from Windows and Linux in Windows Terminal" width="960" height="720" border="10" /></a> 

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
