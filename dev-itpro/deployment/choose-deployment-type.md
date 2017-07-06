---
# required metadata

title: Microsoft Dynamics 365 for Finance and Operations, Enterprise edition deployment options 
description: Microsoft Dynamics 365 for Finance and Operations, Enterprise edition now supports running business processes in the cloud or on-premises. This topic provides information about the different deployment options. 
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
# Microsoft Dynamics 365 for Finance and Operations, Enterprise edition deployment options
You can now deploy Microsoft Dynamics 365 for Finance and Operations, Enterprise edition in the cloud or on-premises. Cloud deployments offer an ERP service that is fully managed by Microsoft, while on-premises deployments are deployed locallay within a customer's data center. 

Cloud deployments also include high availability, disaster recovery, sandbox environments, and application lifecycle management combined with cloud-based systems of intelligence, infrastructure, compute, and database services in a single offering. 

On-premises deployments serve as a system of record and support by running an organization’s business processes locally, supporting local transactions, and storing local business data. There is no replication of business data to the cloud, unless otherwise configured by, or on behalf of, the customer. Application lifecycle management in this scenario requires connectivity to Microsoft Dynamics Lifecycle Services (LCS) in the cloud. 

The following table provides a comparison of the capabilities provided by the two deployment options.

[![Deployment options table](./media/deployment-options.PNG)](./media/deployment-options.PNG)


## Why cloud


## Why on-premises
With an on-premises deployment, existing data center investments can be leveraged. Customers can also configure their enterprise preferences to meet the regulatory and compliance needs of their business, comply with data sovereignty rules in regions where there are no Azure Data Centers, or ensure business continuity in areas with limited public infrastructure. 

A customer’s business data and processes are disconnected from the cloud and are stored and run locally in the customer’s or their partner’s data center. Some connectivity is required for system management and updates which are enabled through Microsoft Dynamics Lifecycle Services (LCS), a cloud-based application lifecycle management service. Customer data that is related to the configuration and application customization may be stored in the cloud. 

For customers that choose to run Finance and Operations in their own data center, the on-premises deployment option will have a similar user-interface and application functionality as other deployment options. However, customers must taks some additional steps to configure the following capabilities in their own environments:

- High-availability and disaster recovery solutions 
- Sand-box environments

The additional costs to deploy and manage these capabilities might lead to higher deployment costs and a greater Total Cost of Ownership (TCO). The customer or their partner must also manage the infrastructure and software packages for the on-premises deployments. This includes standing up their own Windows 2016 and SQL Server 2016 environments and servicing them. Tools for deploying the Finance and Operations software and updates will be available to partners and customers via Lifecycle Services. Unlike the cloud deployment option, Azure Machine Learning services and embedded Power BI are not included in the on-premises deployment option. 
For more information, see [Features not implemented in on-premises deployments](../get-started/features-not-implemented-on-prem.md).

