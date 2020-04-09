---
# required metadata

title: Apply updates and extensions to Retail Cloud Scale Unit
description: This topic shows how to apply updates and extensions to cloud-hosted Commerce channel components.
author: AamirAllaq
manager: AnnBe
ms.date: 01/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: aamiral
ms.search.validFrom: 2018-4-30 
ms.dyn365.ops.version: 8.0 
---


# Apply updates and extensions to Retail Cloud Scale Unit

[!include[banner](../includes/banner.md)]

If you are updating a Tier-2 sandbox or production environment on application version 8.1.2 or newer and have initialized Commerce Scale Unit, you will also need to update channel components. This topic shows how to apply updates and extensions to Commerce Scale Unit.

Updates to Commerce Scale Unit are cumulative. This means that any update that you apply will include all previously released changes. Applying a Commerce deployable package for extensions is also a cumulative process and will replace the previously deployed version of the extension.

## Prerequisites

Before you proceed, you must first apply updates and extensions (if applicable) to the environment. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md).

To update Commerce Scale Unit, run the following steps for each:

1. On the **Environment details** page, go to **Environment features > Retail and Commerce**.
2. On the **Commerce deployment setup** page, select **Update**.
3. In the selection panel, select the version to update to.
4. You can choose to update to the newest Service Update to uptake the newest features, or you may choose to update to the latest Quality Update to apply quality improvements for the currently deployed Service Update. For more information see [Quality & Service Updates] (../migration-upgrade/download-hotfix-lcs.md)
5. You can also choose to apply an extension at the same time. 

To apply an extension to a Commerce Scale Unit, run the following steps:

1. On the **Commerce deployment setup** page, select **Apply Extension**.
2. In the selection panel, select the extension to apply.

> [!NOTE]
> You must first upload the Commerce deployable package to the project asset library in Lifecycle Services (LCS), before you can select to deploy it on the **Commerce deployment setup page** in LCS.

Both **Apply updates** and **Apply extension** operations will involve a downtime of up to 1 hour. During this time, the following will occur:

- Cloud-hosted Commerce channels will not function (unless POS offline capability is enabled).
- POS devices that have the offline capability feature enabled will have reduced functionality.
- Any e-Commerce clients that are dependent on Commerce Scale Unit will be disrupted.
- Channels hosted on Commerce Scale Units will remain unaffected.
- Head office functionality will remain unaffected.

> [!NOTE]
> Applying an extension and an update at the same time requires a single downtime, and can be an effective way of averting multiple downtimes.

## View History
To view the history of recent operations on a Scale Unit, you can select History in the action tab on top to navigate to the Scale Unit History page. On this page, you can view recent operations such as Initialize, Service Update, Quality update, version, extension details and other relevant information.

