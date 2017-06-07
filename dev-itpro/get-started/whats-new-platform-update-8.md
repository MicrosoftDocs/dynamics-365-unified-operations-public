---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8 (June 2017)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8. This version was released in June 2017.
author: tonyafehr
manager: AnnBe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 
ms.search.scope: Operations Platform
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8

---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8 (June 2017)

[!include[banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8. This version was released in June 2017 and has a build number of 7.0.XXXX.XXXXX.

## Development and customization - Changing the EDT type on a table field using table extensions
Using table extensions, a developer can change the Extended Data Type (EDT) property of a table field. Developers can only select EDTs that are derived from the current one. For more information, see [Customize with extensions and overlayering](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/extensibility/customization-overlayering-extensions).

## Templates for configuration data projects 
A set of default configuration templates provides the necessary entities and sequencing to be able to copy configuration data from one instance to another instance in a single step, using a configuration data project. 

## Deployment option - Local business data
Some organizations are not ready to store their company’s mission critical data in the cloud. This requirement, in many cases, is due to industry regulations, country or geographic cloud adoption, recent data center investments, or an organization’s enterprise standards. For these customers, we are excited to announce a new deployment option that will not require business data to be stored in the cloud.
This deployment option, “local business data,” supports running your business processes on-premises, supporting local transactions and storage of local business data, without replication of your business data to the Microsoft cloud. In these cases, the typical replication of business data in the Microsoft cloud (referenced in the cloud and edge scenario) is simply switched off.

Cloud synchronization of data enables Microsoft to embed intelligence into business processes – embedded analytics, machine learning, and a vast range of capabilities are best served from the Microsoft cloud. With this option, customers now have a choice – an option to turn on or turn off cloud synchronization of their business data. If customers turn off cloud synchronization, no business data leaves their trustee’s boundaries. Also, functions like embedded Power BI, Aggregated Views, and Azure Machine Learning services-based efficiencies are not available when cloud data synchronization is turned off. Customers can choose to take advantage of the embedded intelligence functions by simply turning on data synchronization to the cloud. 

An environment with both local business data and cloud data synchronization is referred to as a Cloud + Edge deployment option. Refer to the table for a closer comparison of differences between these options.

Our cloud-based Application Lifecycle Management (ALM) functions, including diagnostics, monitoring, usage telemetry, and production updates, are provided through Microsoft Dynamics Lifecycle Services (LCS). LCS is required for efficient upkeep and operation of your Dynamics 365 for Finance and Operations solutions in all deployment options. After nearly a year of operating the cloud service, we have seen that LCS-based management leads to more predictable deployments and provides customers with a better support and service experience. All deployment options for Finance and Operations require LCS for their operation.

For the “local business data” deployment scenario, the application servers and SQL database will run in a customer’s or partner’s data center. Customers and partners manage the application lifecycle through LCS in the Microsoft cloud, including designing the business processes, creating and deploying the software image to deploy onto the on-premises nodes, monitoring the on-premises nodes in a system health dashboard, and keeping up with innovation from Microsoft.

For more information, see [The right cloud option for your business](https://community.dynamics.com/b/msftdynamicsblog/archive/2017/02/06/the-right-cloud-option-for-your-business).

GET UPDATED SCREENSHOT FROM JESPER
