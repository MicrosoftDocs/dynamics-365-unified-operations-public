---
# required metadata

title: Enable Dataverse virtual entities
description: This topic provides steps for enabling Finance and Operations virtual entities in Dataverse.
author: jaredha
ms.date: 10/14/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-10-14
ms.dyn365.ops.version: 10.0.12
---

# Enable Dataverse virtual entities

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Due to the large number of OData-enabled entities available in Finance and Operations, the entities are not available as virtual entities in Dataverse by default. Once configuration has been completed for Finance and Operations virtual entities in Dataverse, the virtual entities can be enabled in the Dataverse environment. This enables administrators to determine which entities will be exposed as virtual entities for use in Dataverse.

> [!NOTE]
> Configuration for Finance and Operations virtual entities in Dataverse is prerequisite for enabling the virtual entities. The configuration is done automatically for Finance and Operations environments that are linked to a Power Platform environment. For non-linked environments, manual configuration must be completed prior to enabling the virtual entities. See [Configure Dataverse virtual entities](admin-reference.md) for step-by-step guidance on configuring Finance and Operations virtual entities in Dataverse.

## Generating virtual entities

1. In Dataverse, go to **Advanced find** (filter icon).

2. Look for “Available Finance and Operations Entities” and select **Results**.

![Catalog.](../media/fovecatalog.png)

3. Locate and open the entity that you want to enable.

4. Set **Visible** to **Yes** and save. This will generate the virtual entity, so that it will appear in all of the appropriate menus, such as the advanced find dialog box.

![Enable VE.](../media/foveenable.png)

## Refreshing virtual entity metadata

The virtual entity metadata can be force-refreshed when it is expected for the entity metadata in Finance and Operations to have changed. This can be done by setting **Refresh** to **Yes** and saving. This will sync the latest entity definition from Finance and Operations to Dataverse and update the virtual entity.

## Referencing virtual entities

The virtual entities are all generated in the MicrosoftOperationsERPVE solution, which is API Managed. That means the items in the solution change as you make entities visible/hidden, but it is still a managed solution that you can take dependency on. The standard ALM flow would be to just take a standard reference to a virtual entity from this solution with the **Add existing** option
in the ISV solution. It will then show as a missing dependency of the solution and be checked at solution import time. During import if a specified virtual entity does not yet exist, it would automatically be made visible without needing additional work.

To consume virtual entities:

1.  Create a separate solution as usual in Dataverse, which will contain the consuming logic.

2.  Select **Entities \> Add Existing**. Select the virtual entity that you want to reference from the list.

3.  When prompted to select assets to add, select any forms, views, or other elements that you want to customize, then select **Finish**.

From the development tooling, existing elements such as forms can be modified for the virtual entity. Additionally, new forms, views, and other elements can also be added.

![Solution.](../media/fovesolution.png)

When the solution is exported, it will contain hard dependencies on the virtual entity generated in the MicrosoftOperationsERPVE solution.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
