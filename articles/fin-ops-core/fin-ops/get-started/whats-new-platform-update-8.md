---
title: What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8 (June 2017)
description: This article describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8. This version was released in June 2017.
author: sericks007
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 8
ms.custom: 
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8 (June 2017)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Finance and Operations, Enterprise edition platform update 8. This version was released in June 2017 and has a build number of 7.0.4565.16212.

> [!NOTE]
> Dynamics 365 for Operations (on-premises) is currently being renamed. You will see Dynamics 365 for Operations (on-premises) referenced throughout communications and licensing guides. The in-product name that you will see when deploying the product is Dynamics 365 for Finance and Operations, Enterprise edition. Both of these names refer to the same product.

Go to the [Dynamics 365 Roadmap](https://roadmap.dynamics.com/) to find supplemental information about new features and learn more about what new features are in development. For information about the bug fixes included in Platform update 8, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=852224).

## Introducing Dynamics 365 for Finance and Operations, Enterprise edition

Users and developers will see an updated product name ("Microsoft Dynamics 365 for Finance and Operations, Enterprise edition") and product icon in the web client. Some platform components (for example, the developer tools and the mobile application) that are shared by Dynamics 365 for Finance and Operations, Dynamics 365 for Retail, and Dynamics 365 Human Resources will now appear as "Dynamics 365 Unified Operations."

## Development and customization – Changing the extended data type (EDT) on a table field using table extensions

Using table extensions, a developer can change the **Extended Data Type** (EDT) property of a table field. Developers can only select EDTs that are derived from the current one. For more information, see [Customize through extension and overlayering](../../dev-itpro/extensibility/customization-overlayering-extensions.md).

## Improved viewing experience for Application reports

There is a new and improved viewing experience for customers when interacting with Analytical and Operational reports in Dynamics 365 for Finance and Operations, Enterprise edition. This change offers a streamlined toolbar and clear preview of the document that is produced when rendered as a PDF file or sent directly to the printer. To date, customers have rendered over 1.1 million document reports powered by SQL Server Reporting Services (SSRS). In addition, the Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) includes 20+ analytical reports authored using Power BI Desktop. This feature offers a significantly enhanced viewing experience while interacting with both document and analytical style application reports.
Customer benefits:

- **Reliability** – Customers will now be presented with a view that is consistent with the output when documents are sent directly to the printer. Based on direct feedback, the most common use case for viewing a report on screen is to preview the output that will be shared with others, most often by email. Customs can now rely on a screen rendition that more closely matches the document produced by SSRS.
- **Simplicity** – Customers can fully engage with application reports using mobile devices with relatively small screens. On these devices, every inch of the screen is important. By removing the page caption, users have more screen space with which to view and interact with application reports.

## Table browser is now in read-only mode

The table browser form is now in read-only mode on runtime environments (Sandbox Tier-2 and Production).

The table browser form is designed for developers to quickly create and edit test data on development environments. It was also available to system administrators on runtime environments. As of Platform update 8, system administrators can only access the table browser in read-only mode on runtime environments, this is in reaction to live incidents caused by human error when system administrators inadvertently edited or removed live system data.

## Deployment option (on-premises)

Some organizations are not ready to store their company's mission critical data in the cloud. This requirement, in many cases, is due to industry regulations, country/region or geographic cloud adoption, recent data center investments, or an organization's enterprise standards. For these customers, we are excited to announce a new deployment option that will not require business data to be stored in the cloud.

This deployment option supports running your business processes on-premises, supporting local transactions and storage of local business data, without replication of your business data to the Microsoft cloud. In these cases, the typical replication of business data in the Microsoft cloud (referenced in the cloud and edge scenario) is simply switched off.

Cloud synchronization of data enables Microsoft to embed intelligence into business processes – embedded analytics, machine learning, and a vast range of capabilities are best served from the Microsoft cloud. With this option, customers now have a choice – an option to turn on or turn off cloud synchronization of their business data. If customers turn off cloud synchronization, no business data leaves their trustee's boundaries. Also, functions like embedded Power BI, Aggregated Views, and Azure Machine Learning are not available when cloud data synchronization is turned off. Customers can choose to take advantage of the embedded intelligence functions by simply turning on data synchronization to the cloud.

An environment with both on-premises business data and cloud data synchronization is referred to as a Cloud + Edge deployment option. Refer to the table for a closer comparison of differences between these options.

Our cloud-based Application Lifecycle Management (ALM) functions, including diagnostics, monitoring, usage telemetry, and production updates, are provided through Microsoft Dynamics Lifecycle Services (LCS). LCS is required for efficient upkeep and operation of your Dynamics 365 for Finance and Operations solutions in all deployment options. After nearly a year of operating the cloud service, we have seen that LCS-based management leads to more predictable deployments and provides customers with a better support and service experience. All deployment options for Finance and Operations require LCS for their operation.

For the on-premises deployment scenario, the application servers and SQL database will run in a customer's or partner's data center. Customers and partners manage the application lifecycle through LCS in the Microsoft cloud, including designing the business processes, creating and deploying the software image to deploy onto the on-premises nodes, monitoring the on-premises nodes in a system health dashboard, and keeping up with innovation from Microsoft.

For more information, see [The right cloud option for your business](https://community.dynamics.com/b/msftdynamicsblog/archive/2017/02/06/the-right-cloud-option-for-your-business). This blog post refers to the "local business data" deployment capability. This is the capability that's called "on-premises" in the product and documentation.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
