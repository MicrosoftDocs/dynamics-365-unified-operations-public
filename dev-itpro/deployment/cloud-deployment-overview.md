---
# required metadata

title: Dynamics 365 for Finance and Operations, Enterprise edition cloud deployment overview 
description: Dynamics 365 for Finance and Operations, Enterprise edition now supports running business processes in the cloud.
author: kfend
manager: AnnBe
ms.date: 06/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.2.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---
# Dynamics 365 for Finance and Operations, Enterprise edition cloud deployment overview 
Getting ready to deploy Microsoft Dynamics 365 for Operations requires that you understand the environment and subscription that you are deploying to, who can perform tasks on the subscription, and the data and customizations that you need to load. 
Using Microsoft FastTrack for Dynamics 365 can help speed your deployment and implementation - it's a program that provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack for Dynamics 365 overview](../get-started/fasttrack-dynamics-365-overview.md).

## Topologies - Note that there is more information about this in the licensing guide
Topologies used are based on the customer lifecycle and your subscription. 
The following topologies are available:

- Demo (one-box topology) (Tier 1 sandbox)
- Dev/Build (one-box topology) (Tier 1 sandbox)
- High Availability (HA) (Multi-box) (Tier 2 sandbox) (Production sandbox) 

## Subscriptions and licensing
There are two types of subscriptions that you can have, Customer and Microsoft. 
A customer subscription means the customer brings their own Azure subscription and deploys Dynamics 365 for Operations environments to it. The customer will pay for the resources deployed to their Azure subscription based on Azure price list. This customer subscription approach only allows demo and dev/build topologies to be deployed. It is intended for evaluating Dynamics 365 for Operations.
A Microsoft subscription means that the customer purchases Dynamics 365 for Operations licenses which will then allow them to deploy environments to an Azure subscription which is managed by Microsoft, this means that the customer has no separate Azure billing. Three environments are included by default and more can be purchased as add-ons:

- One tier-1 sandbox which is a one-box - customers can choose to use it for either demo or dev build – managed by customer
- One Tier-2 HA sandbox which is a multi-box 
- One HA production deployment. managed and operated by Microsoft

For information about licensing and what is included in Microsoft Dynamics 365, see the [Microsoft Dynamics 365 Enterprise edition licensing guide](http://download.microsoft.com/documents/en-us/dynamics/pricing/Dynamics_365_Enterprise_edition_Licensing_Guide.pdf).

## Customer lifecycle
We assume that most customers follow a lifecycle of evaluate, analyze/design, develop/test, go-live. We recommend that you use the XXX   methodology in Microsoft Dynamics Lifecycle Services to help you manage your process. Here's how the lifecycle maps to the available environments.

| Lifecycle phase               | Environment                               | Subscription                                        |
|-------------------------------|-------------------------------------------|-----------------------------------------------------|
| Evaluation and analysis       | Demo, one-box                             | Customer subscription                               |
| Customize                     | Dev/build, one-box                        | Customer subscription and/or Microsoft subscription |
| User acceptance testing (UAT) | High availability (HA) sandbox, multi-box | Microsoft subscription                              |
| Go live                       | Production, multi-box                     | Microsoft subscription                              |

## Security and compliance
Dynamics 365 for Operations is PA-DSS 3.1 certified which means that all communications between components are secured out-of-the-box. 
All Dynamics 365 for Operations front-end VMs (in Microsoft Azure) are configured during deployment to only accept TLS 1.2. 
To ensure accessibility of the service, all production environments are protected through high availability (HA) and disaster recover (DR) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages broadly impacting an entire datacenter. Dynamics 365 for Operations cloud architecture uses Azure availability sets for the compute tier to prevent single-point-of-failure events. For more information about Azure availability sets, see [Azure availability sets guidelines for Windows VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/infrastructure-availability-sets-guidelines).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-business-continuity).

The Dynamics 365 for Operations production environments are configured with disaster recovery support that includes the following:
•	Azure SQL active-geo replication for primary databases, with a Recover Point Estimate (RPO) of < 5 seconds. For more information, see [Overview: Failover groups and active geo-replication](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-geo-replication-overview). 
•	Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Geo-redundant storage](https://docs.microsoft.com/en-us/azure/storage/storage-redundancy#geo-redundant-storage).
•	Same secondary region for the Azure SQL and Azure blog storage replications.  
The primary data stores are supported for replication. This means that the application components, such as Management Reporter, and Entity store, use transformed data from the primary database, which need to be generated after the recovery site has been set up and the service has started. Customer code artifacts and recovered data stores are used to re-deploy the site, with a Recovery Time Objective (RTO) of 10 hours. This enables state replication of the compute nodes along with networking and other components to set up the secondary site using the recovered data stores. For more information, see [Azure SQL Database Point in Time Restore](https://azure.microsoft.com/en-us/blog/azure-sql-database-point-in-time-restore/).

## Availability 
The guaranteed uptime for Dynamics 365 for Operations is 99.5%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn’t always take eight hours, we will always communicate the estimated amount of time that your environments will be down. For more information, see [Find support for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics Lifecycle Services](../lifecycle-services/lcs-support.md).

## Service availability 


## Deploy a demo environment
A demo environment includes only Microsoft demo data. You can use a demo environment to explore default features and functionality. For more information, see [Deploy a demo environment](deploy-demo-environment.md).

## Test on a sandbox
The following topics provide information about setting up a sandbox for testing. 
- Move your customizations to a sandbox
    - [Create a deployable package of your models in order to apply it to a runtime environment](create-apply-deployable-package.md)
    - [Apply a deployable package to a Finance and Operations environment](apply-deployable-package-system.md)
    - [Install a deployable package](../install-deployable-package.md)

To migrate your code to Dynamics 365 for Operations, use the “Migrate and Create Dynamics 365 for Operations Solutions” methodology in Lifecycle Services. 
- Load data in a sandbox
    - [Develop an entity for data migration](data-entities/develop-entity-for-data-migration.md)
- Import data from Production into a sandbox
    - [Copy a Microsoft Dynamics 365 for Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md)

## Move to production



