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

## Introducing Dynamics 365 for Finance and Operations, Enterprise edition
Users and developers will see an updated product name ("Microsoft Dynamics 365 for Finance and Operations, Enterprise edition") and product icon in the web client. Some platform components (for example, the developer tools and the mobile application) that are shared by Dynamics 365 for Finance and Operations, Dynamics 365 for Retail, and Dynamics 365 for Talent will now appear as "Dynamics 365 Unified Operations." 

## Development and customization - Changing the extended data type (EDT) on a table field using table extensions
Using table extensions, a developer can change the **Extended Data Type** (EDT) property of a table field. Developers can only select EDTs that are derived from the current one. For more information, see [Customize with extensions and overlayering](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/extensibility/customization-overlayering-extensions).

## Development and customization - Compliance properties on table fields
A new property named General Data Protection Regulation (GDPR) is now available on table fields for the developer to set. It is used to classify the data field for compliance with GDPR.

Available options are:
- Access control data - Data used to manage and access to administrative roles or sensitive functions.
- Customer content - Content directly provided/created by admins and users. This is the default value.
- End User Identifiable Information (EUII) - Data that identifies or could be used to identify the user of a Microsoft service. EUII does not contain Customer content.
- End User Pseudonymous Information (EUPI) - An identifier created by Microsoft tied to the user of a Microsoft service. When EUPI is combined with other information, such as a mapping table, it identifies the end user. EUPI does not contain information uploaded or created by the customer (Customer content or EUII).
- Support data - Data provided to Microsoft as part of Support activities.
- Account data - Customer billing information and payment instrument information. Administrator contact information, such as tenant administrator’s name, address, or phone number. 
- Public personal data - Publicly available information that Microsoft obtains from external sources. Public personal data is not Customer content, EUII, or EUPI since the data was not input by the customer.
- Organization Identifiable Information (OII) - Data that can be used to identify a tenant, generally config or usage data. This data is not linkable to a user and does not contain Customer content.
- System metadata - Data generated while running the service, not linkable to a user or tenant. 
- Public non-personal data - Publicly available information that Microsoft obtains from external sources.  Does not contain Public personal data.

## Table browser is now in read-only mode
The table browser form is now in read-only mode on runtime environments (Sandbox Tier-2 and Production).

The table browser form is designed for developers to quickly create and edit test data on development environments. It was also available to system administrators on runtime environments. As of Platform update 8, system administrators can only access the table browser in read-only mode on runtime environments, this is in reaction to live incidents caused by human error when system administrators inadvertently edited or removed live system data.

## Deployment option - Local business data
Some organizations are not ready to store their company’s mission critical data in the cloud. This requirement, in many cases, is due to industry regulations, country or geographic cloud adoption, recent data center investments, or an organization’s enterprise standards. For these customers, we are excited to announce a new deployment option that will not require business data to be stored in the cloud.
This deployment option, “local business data,” supports running your business processes on-premises, supporting local transactions and storage of local business data, without replication of your business data to the Microsoft cloud. In these cases, the typical replication of business data in the Microsoft cloud (referenced in the cloud and edge scenario) is simply switched off.

Cloud synchronization of data enables Microsoft to embed intelligence into business processes – embedded analytics, machine learning, and a vast range of capabilities are best served from the Microsoft cloud. With this option, customers now have a choice – an option to turn on or turn off cloud synchronization of their business data. If customers turn off cloud synchronization, no business data leaves their trustee’s boundaries. Also, functions like embedded Power BI, Aggregated Views, and Azure Machine Learning services-based efficiencies are not available when cloud data synchronization is turned off. Customers can choose to take advantage of the embedded intelligence functions by simply turning on data synchronization to the cloud. 

An environment with both local business data and cloud data synchronization is referred to as a Cloud + Edge deployment option. Refer to the table for a closer comparison of differences between these options.

Our cloud-based Application Lifecycle Management (ALM) functions, including diagnostics, monitoring, usage telemetry, and production updates, are provided through Microsoft Dynamics Lifecycle Services (LCS). LCS is required for efficient upkeep and operation of your Dynamics 365 for Finance and Operations solutions in all deployment options. After nearly a year of operating the cloud service, we have seen that LCS-based management leads to more predictable deployments and provides customers with a better support and service experience. All deployment options for Finance and Operations require LCS for their operation.

For the “local business data” deployment scenario, the application servers and SQL database will run in a customer’s or partner’s data center. Customers and partners manage the application lifecycle through LCS in the Microsoft cloud, including designing the business processes, creating and deploying the software image to deploy onto the on-premises nodes, monitoring the on-premises nodes in a system health dashboard, and keeping up with innovation from Microsoft.

For more information, see [The right cloud option for your business](https://community.dynamics.com/b/msftdynamicsblog/archive/2017/02/06/the-right-cloud-option-for-your-business).

GET UPDATED SCREENSHOT FROM JESPER
