---

# required metadata

title: Go-live FAQ
description: This topic lists frequently asked questions about how to go live with a Dynamics 365 Human Resources implementation project. 
author: raprofit
manager: tfehr
ms.date: 10/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# Go-live FAQ 

This topic lists frequently asked questions about how to go live with a Dynamics 365 Human Resources implementation project. 

## When can I configure and request my production environment? 

Typically, a production environment is deployed after meeting the following criteria:

- All customizations are code-complete.
- User acceptance testing (UAT) is complete.
- The customer has signed off on the solution.
- There are no blocking issues for go-live. 

When qualified customers are at this stage, the Microsoft FastTrack team will work with the project team to do a go-live assessment. 

## What are the prerequisites to deploying a production environment? 

For a list of the prerequisites, see [Prepare for go-live](/human-resources/hr-admin-go-live-prepare.md). 

## What is a go-live assessment?  

The go-live assessment is part of the [Microsoft FastTrack program](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/fasttrack-dynamics-365-overview). During this review, a solution architect assesses whether an implementation project is ready for a successful cutover and go-live. This review is mandatory for every implementation project before you can request to go live in a production environment. 

## Our Sandbox environments are deployed in the Central US datacenter. We want our Production environments to be deployed in the West US datacenter. Can I select West US as the datacenter in my Production configuration? 

LCS doesn't restrict you from selecting a different data center when you deploy a Human Resources environment, but we strongly recommend not selecting a different data center.  

If you want your Production environment to be in the West US datacenter, you should first redeploy your Sandbox environments to the West US datacenter, test them, and sign off. 

For information about selecting the correct datacenter, see [Network requirements](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/system-requirements#network-requirements). 

## What level of access do I have to the Azure resources for my Human Resources environments?  

Access to the Human Resources environments is limited. You can't access the virtual machine (VM) or Microsoft Internet Information Services (IIS). You also can't access the database through Microsoft SQL Server Management Studio. 

Although you can't access your Azure resources or Dynamics 365 Human Resources environment directly, there are additional features you can use to access your data:

- You can deploy an Azure SQL database in your own Azure tenant and use the Bring Your Own Database (BYOD) feature to synchronize data. For more information, see [Bring your own database (BYOD)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/export-entities-to-your-own-database).

- You can use Common Data Service integration to synchronize select entities into the Common Data Service database. For more information, see [Common Data Service entities](hr-developer-entities.md). 

## How often is my production database backed up? 

Databases are protected by automatic backups at the following frequencies:

| Type of backup | Frequency |
| --- | --- |
| Full database backup | Weekly |
| Differential database backup | Every 12-24 hours |
| Transaction log backup | Every 5 to 10 minutes |

Microsoft retains sufficient backups to allow for Point in Time Restore (PITR) within the last seven days. 

For more information, see [Learn about automatic SQL Database backups](https://docs.microsoft.com/azure/azure-sql/database/automated-backups-overview?tabs=single-database). 

## Can I request a copy of the backup of my production database? 

No. You can submit a database refresh service request to copy your Production environment to your Sandbox environment, however. You can deploy an Azure SQL database in your own Azure tenant and use the BYOD feature to synchronize data from your Production environment. For more information, see [Bring your own database (BYOD)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/export-entities-to-your-own-database). 

## How do I move my Sandbox environment to Production for go-live? 

Because a copy feature isn't available to move your environment from a Sandbox to a Production environment, you must use data packages to move data into your Production environment.  

We recommend maintaining a clear list of entities configured in your Sandbox throughout the project. Then test the process of cutover and migration of any data packages needed for your go-live. You must manually move any data packages into the Production environment when you are ready to go live. 

## What should I do if my Production environment is down? 

To report a Production outage, follow the process described in [Report a production outage](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/report-production-outage). 

 ## See also

 [Prepare for go-live](hr-admin-go-live-prepare.md)