---
# required metadata

title: Enable Microsoft Dataverse virtual entities
description: This topic explains how to enable Finance and Operations apps virtual entities in Microsoft Dataverse.
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



Because many entities that are available in Finance and Operations apps are enabled for Open Data Protocol (OData), the entities aren't available as virtual entities in Microsoft Dataverse by default. After configuration is completed for Finance and Operations apps virtual entities in Dataverse, the virtual entities can be enabled in the Dataverse environment. Administrators can then determine which entities will be exposed as virtual entities that can be used in Dataverse.

> [!NOTE]
> Configuration of Finance and Operations apps virtual entities in Dataverse is a prerequisite for enabling the virtual entities. The configuration is automatically done for Finance and Operations apps environments that are linked to a Microsoft Power Platform environment. For unlinked environments, manual configuration must be completed before the virtual entities can be enabled. For step-by-step information about how to configure Finance and Operations apps virtual entities in Dataverse, see [Configure Dataverse virtual entities](admin-reference.md).

## Generate virtual entities

1. In Dataverse, select the **Advanced find** filter button.
2. Search for **Available Finance and Operations Entities**, and select **Results**.

    ![Catalog of entities.](../media/fovecatalog.png)

3. Find and open the entity that you want to enable.
4. Select the **Visible** checkbox, and then save your change.

    ![Visible checkbox selected for an entity.](../media/foveenable.png)

The virtual entity is generated and will appear on all the appropriate menus. For example, it will appear in the **Advanced find** dialog box.

## Refresh virtual entity metadata

You can force a refresh of a virtual entity's metadata when you expect that the entity metadata in Finance and Operations apps has changed. To force a refresh, select the **Refresh** checkbox, and then save your change. The latest entity definition from Finance and Operations apps is synchronized to Dataverse, and the virtual entity is updated.

## Reference virtual entities

All virtual entities are generated in the **MicrosoftOperationsERPVE** solution, which is API managed. Items in the solution change as you make entities visible or hidden. Nevertheless, the solution is still a managed solution that you can take dependencies on. 

The standard Application Lifecycle Management (ALM) flow is to take a standard reference to a virtual entity from this solution. You can do this by using the **Add existing** action in the independent software vendor (ISV) solution. The virtual entity will be shown as a missing dependency of the solution, and it will be checked when the solution is imported. During import, if a specified virtual entity doesn't exist, it's automatically made visible. No additional work is required.

Follow these steps to consume virtual entities:

1. In Dataverse, follow the usual steps to create a separate solution that contains the consuming logic. See [Create a solution](/powerapps/maker/data-platform/create-solution) in the Power Platform documentation for additional information on creating a solution.
2. Select **Add existing** \> **Table**. 
3. In the **Add existing tables** list, select the virtual entity that you want to reference.
4. When you're prompted to select assets to add, select any forms, views, or other elements that you want to customize, and then select **Finish**.

You can use the development tools to modify existing elements for the virtual entity, such as forms. You can also add new forms, views, and other elements.

![Solution.](../media/fovesolution.png)

When the solution is exported, it will contain hard dependencies on the virtual entity that is generated in the **MicrosoftOperationsERPVE** solution.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
