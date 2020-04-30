---
# required metadata

title: Removed or deprecated features in Dynamics 365 Supply Chain Management
description: This topic describes features that have been removed, or that are planned for removal in Dynamics 365 Supply Chain Management.
author: kamaybac
manager: tfehr
ms.date: 03/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kamaybac
ms.search.validFrom: 2020-03-03 
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated features in Dynamics 365 Supply Chain Management

[!include [banner](../includes/banner.md)]

This topic will be updated as new removed or deprecated features are documented for Dynamics 365 Supply Chain Management.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning.

> [!NOTE]
> Detailed information about objects in Finance and Operations apps can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Features removed or deprecated in the Supply Chain Management 10.0.11 release

## Use of built-in Supply Chain Management master planning engine for distribution scenarios.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | To enhance performance and minimize the SQL database load during master planning runs, the built-in Supply Chain Management master planning engine is being replaced by Planning Optimization. Planning Optimization allows for fast planning runs that can be performed even during office hours. This enables planners to react immediately to changes in demand or planning parameters. |
| **Replaced by another feature?**   | Yes, Planning Optimization will replace the existing built-in Supply Chain Management master planning engine. |
| **Product areas affected**         | Supply Chain Management - Master planning |
| **Deployment option**              | Cloud only. Planning Optimization is not supported with on-premises deployments. |
| **Status**                         | Deprecated. As per April 1, 2021, distribution scenarios will no longer be supported with the built-in Dynamics 365 Supply Chain Management master planning engine. For distribution scenarios, customers must use Planning Optimization for master planning calculations. Find more information in the related [Planning Optimization documentation](https://go.microsoft.com/fwlink/?linkid=2105830). Customers with on-premises deployments of Dynamics 365 Supply Chain Management may continue to use the Supply Chain Management master planning engine for distribution scenarios after April 1, 2021. However, no more feature enhancements will be provided. |

## Previous announcements about removed or deprecated features

To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features in previous releases](../../fin-ops-core/dev-itpro/migration-upgrade/deprecated-features.md).
