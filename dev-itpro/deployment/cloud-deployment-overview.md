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
Working with Microsoft to deploy Microsoft Dynamics 365 for Operations in the cloud requires that you understand the environment and subscription that you are deploying to, who can perform which tasks, and the data and customizations that you need to manage. 
We recommend that you sign up for the Full Microsoft FastTrack for Dynamics 365 to help speed your deployment and implementation - it's a program that provides training and consulting to help you realize business value faster. For more information, see [Microsoft FastTrack for Dynamics 365 overview](../get-started/fasttrack-dynamics-365-overview.md). If you choose to use the Essentials FastTrack program instead, you will be using the Implementation Project Methodology in Lifecycle Services (LCS) to help you manage your implementaiton project. 

## Customer lifecycle, subscriptions, and deployment topologies
Microsoft assumes that all customers will follow a lifecycle similar to the following for all cloud deployments, and therefore need different environment topologies at each phase. 

- Evaluate
- Develop customizations, if needed
- Deploy and test customizations and partner solutions in a small sandbox
- Test customizations and partner solutions in a production sandbox
- Deploy to a live environment with high availability

At some phases of a project, you may have all of the environments live at once. For more information, about the default licenses and tiers that are available, see the [Dynamics 365 Licensing Guide](http://download.microsoft.com/documents/en-us/dynamics/pricing/Dynamics_365_Enterprise_edition_Licensing_Guide.pdf).

You may hear the terms, Customer, Partner, and Microsoft subscriptions. A *customer or partner subscription* means that the customer or partner brings their own Azure subscription and deploys Dynamics 365 for Finance and Operations environments to it, for evaluation and development purposes only. The customer or partner pays for the resources deployed to their Azure subscription based on the Azure price list. 
A *Microsoft subscription* means that the customer purchases Dynamics 365 for Finance and Operations licenses which will then allow them to deploy environments to an Azure subscription which is managed by Microsoft, therefore, the customer has no separate Azure billing. Three environments are included by default and more can be purchased as add-ons:

- One Tier-1 sandbox which is a one-box - customers can choose to deploy it as either a demonstration or a dev/build environment. This environment is managed by the customer.
- One Tier-2 highly-available (HA) sandbox. This environment is managed by the customer or partner, until the customer is live in production. After going live in production, Microsoft DSE may be required to perform some tasks, such as helping move production data into the sandbox environment. 
- One HA production deployment. This environment is managed and operated by Microsoft.

For information about licensing and what is included in Microsoft Dynamics 365, see the [Microsoft Dynamics 365 Enterprise edition licensing guide](http://download.microsoft.com/documents/en-us/dynamics/pricing/Dynamics_365_Enterprise_edition_Licensing_Guide.pdf).

Here's how the lifecycle maps to the available environments.

| Lifecycle phase               | Environment                               | Subscription                                        |
|-------------------------------|-------------------------------------------|-----------------------------------------------------|
| Evaluation and analysis       | Demo, one-box                             | Customer or partner subscription                               |
| Customize                     | Dev/build, one-box                        | Microsoft subscription |
| User acceptance testing (UAT) | High availability (HA) sandbox, multi-box | Microsoft subscription                              |
| Go live                       | Production, multi-box                     | Microsoft subscription                              |

## Features of the Finance and Operations production instance
The Finance and Operations application production instance has the following capabilities.

### Security and compliance
Dynamics 365 for Operations is PA-DSS 3.1 certified which means that all communications between components are secured out-of-the-box. 

All Dynamics 365 for Operations front-end virtual machines in Microsoft Azure are configured during deployment to only accept TLS 1.2. 

### Availability
The guaranteed uptime for Dynamics 365 for Finance and Operations is 99.5%. Planned downtime occurs once a month and lasts no longer than eight hours. Because the work completed during the downtime doesn’t always take eight hours, we will always communicate the estimated amount of time that your environments will be down. [Find support for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition and Dynamics Lifecycle Services](../lifecycle-services/lcs-support.md).

### High-availability features
To ensure service availability, all production environments are protected by using default Azure high availability (HA) features. HA functionality provides ways to avoid downtime caused by the failure of a single node within a datacenter, and DR features protect against outages broadly impacting an entire datacenter. Dynamics 365 for Operations cloud architecture uses Azure availability sets for the compute tier to prevent single-point-of-failure events. For more information about Azure availability sets, see [Azure availability sets guidelines for Windows VMs](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/infrastructure-availability-sets-guidelines).
High availability for databases is supported through Azure SQL. For more information, see [Overview of business continuity with Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-business-continuity).

### Disaster recovery features
Finance and Operations production environments are configured with Azure disaster recovery support that includes the following:
- Azure SQL active-geo replication for primary databases, with a Recovery Point Estimate (RPO) of < 5 seconds. For more information, see [Overview: Failover groups and active geo-replication](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-geo-replication-overview). 
- Geo-redundant copies of Azure blob storage (containing document attachments) in other Azure regions. For more information, see [Geo-redundant storage](https://docs.microsoft.com/en-us/azure/storage/storage-redundancy#geo-redundant-storage).
- Same secondary region for the Azure SQL and Azure blog storage replication.  

Only primary data stores are supported by replication. This means that some Finance and Operations application components, such as Management Reporter, and Entity store, which use transformed data from the primary database, must be generated after the recovery site has been set up and the service has started. Customer code artifacts and recovered data stores are used to re-deploy the site, with a Recovery Time Objective (RTO) of 10 hours and a Recovery Point Objective of 5 minutes. For more information, see [Azure SQL Database Point in Time Restore](https://azure.microsoft.com/en-us/blog/azure-sql-database-point-in-time-restore/).

## Service availability 


## Supported deployment scenarios
### Deploy a demo environment
A demo environment includes only Microsoft demo data. You can use a demo environment to explore default features and functionality. For more information, see [Deploy a demo environment](deploy-demo-environment.md).

### Test on a sandbox
The following topics provide information about setting up a sandbox for testing. 

#### Move your customizations to a sandbox
- [Create a deployable package of your models in order to apply it to a runtime environment](create-apply-deployable-package.md)
- [Apply a deployable package to a Finance and Operations environment](apply-deployable-package-system.md)
- [Install a deployable package](../install-deployable-package.md)

To migrate your code to Dynamics 365 for Operations, use the “Migrate and Create Dynamics 365 for Operations Solutions” methodology in Lifecycle Services.

#### Load data in a sandbox
- [Develop an entity for data migration](data-entities/develop-entity-for-data-migration.md)
    
#### Import data from Production into a sandbox
- [Copy a Microsoft Dynamics 365 for Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md)

## Move to production


## Frequently asked questions
### How do I move my customizations between environments?
A customer can request a backup of their Finance and Operations database. For more information, see [Copy a Finance and Operations database from Azure SQL Database to a SQL Server environment](../database/copy-database-from-azure-sql-to-sql-server.md).

### Can I bring my own domain name?
You can bring your own domain name if it is running Azure Active Directory (AAD), and the administrator of your AAD instance has enabled the Finance and Operations application within their AAD. This is usually done through the office email, after you buy a license. When you click the link to acccept the offer, AAD is set up for you.

### Can I add guest AAD accounts as Finance and Operations users?
You can add guest AAD accounts if you have correctly configured them within Azure Active Directory, and enabled the Finance and Operations application within your AAD. 

