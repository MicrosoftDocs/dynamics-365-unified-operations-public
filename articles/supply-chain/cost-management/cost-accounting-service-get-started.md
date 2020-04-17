---
# required metadata

title: Get started with the cost accounting service
description: Licensing details and installation instructions for the cost accounting service
author: AndersGirke
manager: tfehr
ms.date: 04/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: aevengir
ms.search.validFrom: 2020-04-17
ms.dyn365.ops.version: Release 10.0.12
---

# Get started with the cost accounting service

[!INCLUDE [banner](../includes/banner.md)]

> [!IMPORTANT]
> The functionality noted in this topic is available as part of a private preview release. The content and the functionality are subject to change. For more information about preview releases, see [One version service updates FAQ](../../fin-ops-core/fin-ops/get-started/one-version.md).

The cost accounting service doesn't currently support all of the cost-management features built into Dynamics 365 Supply Chain Management. Therefore, it's important that you evaluate whether the currently available feature set will meet your requirements.

The cost accounting service is an add-in, which must be installed from Dynamics Lifecycle Services (LCS) to make its features available. Therefore, you can choose to evaluate this feature on a test environment before it's turned on for production environments.

The cost accounting service enables you to do multiple inventory accounting in the cost accounting ledgers that you have set up. You will associate each of these cost accounting ledgers with a convention, which is a collection of the following types of accounting policies:

- Cost object
- Input measurement basis
- Cost flow assumption
- Cost element

> [!NOTE]
> Even after you have enabled the cost accounting service, you will still be able to do standard inventory accounting in Dynamics 365 Supply Chain Management as usual.

## Licensing

The cost accounting service is licensed together with the standard accounting inventory features available for Dynamics 365 Supply Chain Management. You don't have to purchase an additional license to use the cost accounting service.

## Install the add-in

> [!IMPORTANT]
> To use the cost accounting service, you must have an LCS-enabled high-availability environment (not a OneBox environment), and you must be running Dynamics 365 Supply Chain Management version 10.0.11 (or higher).

To use the Cost accounting service, install the cost accounting service add-in for Dynamics 365 Supply Chain Management, as described in the following procedure.

To install the cost accounting service add-in:

1. Sign in to Dynamics Lifecycle Services (LCS).
1. Go to **Preview feature management**.
1. Select the plus sign.
1. Enter your **Add-in beta key** for the cost accounting service (your key should have been sent to you in email).
1. Select **Unblock**.
1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. Scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Cost accounting service**.
1. Follow the installation guide and agree to the terms and conditions.
1. Select **Install**.
1. On the **Environment add-ins** FastTab, you should see that the cost accounting service is installing.
1. After a few minutes, the status should change from **Installing** to **Installed** (you may need to refresh the page). 
1. The cost accounting service is ready for use.

## Verify the integration

You can verify the integration between the cost accounting service and Dynamics 365 Supply Chain Management by going to **Cost management > Cost accounting service > Setup > Cost accounting service parameters**.

## Related resources

[Cost accounting service home page](cost-accounting-service-home.md)