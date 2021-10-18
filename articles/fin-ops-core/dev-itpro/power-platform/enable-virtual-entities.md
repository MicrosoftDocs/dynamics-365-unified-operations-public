---
# required metadata

title: Enable Microsoft Dataverse virtual entities
description: This topic provides steps for enabling Dynamics 365 Finance and Operations apps virtual entities in Microsoft Dataverse.
author: jaredha
ms.date: 10/18/2021
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

# Enable Microsoft Dataverse virtual entities

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Because of the large number of OData-enabled entities available in Dynamics 365 Finance and Operations apps, the entities aren't available as virtual entities in Microsoft Dataverse by default. After configuration is complete for Finance and Operations apps virtual entities in Dataverse, the virtual entities can be enabled in the Dataverse environment. Administrators can then determine which entities will be exposed as virtual entities for use in Dataverse.

> [!NOTE]
> Configuring Finance and Operations apps virtual entities in Dataverse is prerequisite for enabling the virtual entities. The configuration is done automatically for Finance and Operations apps environments that are linked to a Microsoft Power Platform environment. For non-linked environments, manual configuration must be completed prior to enabling the virtual entities. For step-by-step guidance on configuring Finance and Operations apps virtual entities in Dataverse, see [Configure Dataverse virtual entities](admin-reference.md).

## Generate virtual entities

1. In Dataverse, select the filter icon, **Advanced find**.
2. Look for “**Available Finance and Operations Entities** and select **Results**.

    ![Catalog.](../media/fovecatalog.png)

3. Locate and open the entity that you want to enable.
4. Set **Visible** to **Yes** and save. The virtual entity is generated and will appear in all of the appropriate menus, such as the **Advanced find** dialog box.

![Enable VE.](../media/foveenable.png)

## Refreshing virtual entity metadata

The virtual entity metadata can be force-refreshed when it is expected for the entity metadata in Finance and Operations apps to have changed. The refresh can be done by setting **Refresh** to **Yes** and then saving your changes. This will synchronize the latest entity definition from Finance and Operations apps to Dataverse and update the virtual entity.

## Reference virtual entities

Virtual entities are all generated in the **MicrosoftOperationsERPVE** solution, which is API managed. Items in the solution change as you make entities visible or hidden though it's still a managed solution that you can take dependencies on. The standard ALM flow is to take a standard reference to a virtual entity from this solution with the **Add existing** option in the ISV solution. The virtual entity will show as a missing dependency of the solution and be checked when the solution is imported. During import, if a specified virtual entity doesn't exist, it's automatically made visible without any required additional work.

Complete the following steps to consume virtual entities.

1.  Create a separate solution as usual in Dataverse that contains the consuming logic.
2.  Select **Entities** > **Add Existing** and then select the virtual entity that you want to reference from the list.
3.  When prompted to select assets to add, select any forms, views, or other elements that you want to customize, and then select **Finish**.

    From the development tooling, existing elements such as forms can be modified for the virtual entity. Additionally, new forms, views, and other elements can also be added.

    ![Solution.](../media/fovesolution.png)

    When the solution is exported, it will contain hard dependencies on the virtual entity generated in the **MicrosoftOperationsERPVE** solution.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
