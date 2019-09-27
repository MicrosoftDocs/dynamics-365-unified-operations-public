---
# required metadata

title: Apply updates and extensions to cloud hosted Retail channel components
description: This topic shows how to apply updates and extensions to cloud-hosted Retail channel components.
author: AamirAllaq
manager: AnnBe
ms.date: 09/03/2019
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


# Apply updates and extensions to cloud hosted Retail channel components

[!include[banner](../includes/banner.md)]

If you are updating a Tier-2 sandbox or production environment on application version 8.1.2 or newer and have enabled reduced downtime updates for Retail channel components in the cloud, you will also need to update Retail channel components. This topic shows how to apply updates and extensions to cloud-hosted Retail channel components.

Updates to Retail channel components are cumulative. This means that any update that you apply will include all previously released changes. Applying a Retail deployable package is also a cumulative process and will replace the previously deployed version of the extension.

## Prerequisites

Before you proceed, you must first apply updates and extensions (if applicable) to the environment. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md).

To update cloud-hosted Retail channel components, do the following:

1. On the **Environment details** page, go to **Environment features > Retail**.
2. On the **Retail deployment setup** page, select **Update**.
3. In the selection panel, select the version to update to.
4. You can also choose to apply an extension at the same time. 

To apply an extension to a cloud-hosted Retail channel, do the following:

1. On the **Retail deployment setup** page, select **Apply Extension**.
2. In the selection panel, select the extension to apply.

> [!NOTE]
> You must first upload the Retail deployable package to the project asset library in Lifecycle Services (LCS), before you can select to deploy it on the **Retail deployment setup page** in LCS.

Both Apply updates and Apply extension operations will involve a downtime of up to 1 hour. During this time, the following will occur:

- Cloud-hosted Retail channels will not function (unless POS offline capability is enabled).
- POS devices that have the offline capability feature enabled will have reduced functionality.
- Any e-Commerce clients that are dependent on Retail Server will be disrupted.
- Channels hosted on Retail Store Scale Units will remain unaffected.
- Head office functionality will remain unaffected.

> [!NOTE]
> Applying an extension and an update at the same time requires a single downtime, and can be an effective way of averting multiple downtimes.
