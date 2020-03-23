# AzureNL  

## Introduction
This repo contains Azure samples of all sorts. 

## People
This repo is a team effort, mostly by Microsoft employees in the Netherlands who work with Azure. Here you see an overview of [Users](./users.md).

# Content
## Getting started
To follow along in this repo you will be interacting with an Microsoft Azure subscription and the Azure resource manager (ARM) API. 

* Azure subscription
* Access to Azure Powershell, Azure command-line interface or Azure Cloud Shell. To see them in action, have a look at https://youtu.be/qBS_Knxaz5A.

testing 
<iframe width="420" height="315" src="http://www.youtube.com/embed/qBS_Knxaz5A" frameborder="0" allowfullscreen></iframe> 
or 
[![Video](http://img.youtube.com/vi/qBS_Knxaz5A/0.jpg)](http://www.youtube.com/watch?v=qBS_Knxaz5A) 
or 
<a href="http://www.youtube.com/watch?feature=player_embedded&v=qBS_Knxaz5A
" target="_blank"><img src="http://img.youtube.com/vi/qBS_Knxaz5A/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a> 
Or 
{media}(youtube::qBS_Knxaz5A::420) 
or 
[![Test](https://img.youtube.com/vi/qBS_Knxaz5A/0.jpg)](https://www.youtube.com/watch?v=qBS_Knxaz5A) 

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
