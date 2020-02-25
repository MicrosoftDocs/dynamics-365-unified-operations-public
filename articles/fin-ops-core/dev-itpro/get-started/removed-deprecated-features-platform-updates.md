---
# required metadata

title: Removed or deprecated features in Platform updates
description: This topic describes features that have been removed, or that are planned for removal in Platform updates of Finance and Operations apps.
author: sericks007
manager: AnnBe
ms.date: 02/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-02-29 
ms.dyn365.ops.version: Platform update 33

---

# Removed or deprecated features in Platform updates

[!include [banner](../includes/banner.md)]

This topic describes features that have been removed, or that are planned for removal in Platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!Note]
> Detailed information about objects in Finance and Operations can be found in the [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep). You can compare the different versions of these reports to learn about objects that have changed or been removed in each version of Finance and Operations apps.

## Platform update 32

### Workflow request change dialog adjusted to remove user selection dropdown to secure and simplify
|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This was a security issue since the request for change could be sent to a user that it shouldn't be. This was also a usability issue since it forced the user to determine who the workflow originator was and manually select them.  |
| **Replaced by another feature?**   | No |
| **Product areas affected**         | Workflow |
| **Deployment option**              | All |
| **Status**                         | The user selection drop-down list was removed from the request change dialog as of Platform update 32. Request change requests will be automatically sent to the originator as intended and as documented in [Actions in workflow approval processes](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/workflow-actions?toc=%2Fdynamics365%2Fcommerce%2Ftoc.json#request-change) |

## Previous annoucements about removed or deprecated features
To learn more about features that have been removed or deprecated in previous releases, see [Removed or deprecated features for Finance and Operations](../migration-upgrade/deprecated-features.md).

