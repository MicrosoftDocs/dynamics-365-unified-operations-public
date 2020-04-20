---
# required metadata

title: Get started with the cost accounting service
description: This topic provides licensing details and installation instructions for the cost accounting service.
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
> The functionality that is described in this topic is available as part of a private preview release. The content of this topic and the functionality that it describes are subject to change. For more information about preview releases, see [One version service updates FAQ](../../fin-ops-core/fin-ops/get-started/one-version.md).

The cost accounting service lets you do multiple inventory accounting in the cost accounting ledgers that you've set up. You associate each cost accounting ledger with a *convention*. A convention is a collection of the following types of accounting policies:

- Cost object
- Input measurement basis
- Cost flow assumption
- Cost element

> [!NOTE]
> Even after you've turned on the cost accounting service, you can still do standard inventory accounting in Microsoft Dynamics 365 Supply Chain Management, as usual.

The cost accounting service is an add-in. To makes its features available, you must install it from Microsoft Dynamics Lifecycle Services (LCS). Therefore, you can choose to evaluate it in a test environment before you turn it on for production environments.

The cost accounting service doesn't currently support all the cost management features that are built into Dynamics 365 Supply Chain Management. Therefore, it's important that you evaluate whether the set of features that is currently available will meet your requirements.

## Licensing

The cost accounting service is licensed together with the standard accounting inventory features that are available for Supply Chain Management. You don't have to purchase an additional license to use the cost accounting service.

## Install the add-in

> [!IMPORTANT]
> To use the cost accounting service, you must have an LCS-enabled high-availability environment (not a OneBox environment), and you must be running Dynamics 365 Supply Chain Management version 10.0.11 or later.

To use the cost accounting service, install the cost accounting service add-in for Supply Chain Management as described in the following procedure.

1. Sign in to LCS.
1. Go to **Preview feature management**.
1. Select the plus sign (**+**).
1. In the **Code** field, enter your add-in beta key for the cost accounting service. (You should have received your key by email.)
1. Select **Unblock**.
1. Open the LCS environment where you want to add the service.
1. Go to **Full details**.
1. Scroll down to the **Environment add-ins** FastTab.
1. Select **Install a new add-in**.
1. Select **Cost accounting service**.
1. Follow the installation guide, and agree to the terms and conditions.
1. Select **Install**.

    On the **Environment add-ins** FastTab, you should see that the cost accounting service is being installed. After a few minutes, the status should change from **Installing** to **Installed**. (You might have to refresh the page to see this change.) At that point, the cost accounting service is ready for use.

## Set up the integration

To set up the integration between the cost accounting service and Dynamics 365 Supply Chain Management:

1. Go to **System administration > Feature Management**.
1. Select **Check for updates**.
1. Open the **All** tab and search for the feature named *Cost accounting service*.
1. Select **Enable now**.
1. Go to **Cost management > Cost accounting service > Setup > Cost accounting service parameters > Integrations parameters**.
1. In the **Application ID** field, enter the following:<br> 08231eb2-a501-4edb-b3c5-aede5e5e0c3f
1. In the **Data service endpoint** field, enter the following:<br>https://operationsdataservice.operations365.dynamics.com/    
1. In the **Cost accounting service endpoint** field, enter the following:<br>https://costaccountingservice.operations365.dynamics.com/
1. The cost accounting service is now ready for use.

## Related resources

[Cost accounting service home page](cost-accounting-service-home.md)
