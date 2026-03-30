---
title: Enable Microsoft Dataverse virtual entities
description: Learn about how to enable finance and operations apps virtual entities in Microsoft Dataverse, including an overview on how to generate virtual entities.
author: jaredha
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-10-14
ms.search.form:
ms.dyn365.ops.version: 10.0.12
---

# Enable Microsoft Dataverse virtual entities

[!include[banner](../includes/banner.md)]

Because many entities that are available in finance and operations apps are enabled for Open Data Protocol (OData), the entities aren't available as virtual entities in Microsoft Dataverse by default. After you complete configuration for finance and operations apps virtual entities in Dataverse, you can enable the virtual entities in the Dataverse environment. Administrators can then determine which entities to expose as virtual entities that can be used in Dataverse.

> [!NOTE]
> You must configure finance and operations apps virtual entities in Dataverse before you can enable the virtual entities. For finance and operations apps environments linked to a Microsoft Power Platform environment, the configuration is done automatically. For unlinked environments, you must manually complete the configuration before you can enable the virtual entities. For step-by-step information about how to configure finance and operations apps virtual entities in Dataverse, see [Configure Dataverse virtual entities](admin-reference.md).

## Generate virtual entities

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com), and select the **Environments** tab.
1. In the **Environments** list, select the Power Platform environment associated with your finance and operations apps environment.
1. In the **Details** section of the environment page, select the **Environment URL** link to open the Power Platform environment.
1. At the top-right of the page, select the **Settings** gear icon, and select **Advanced Settings**.
1. At the top-right of the **Settings** page, select the **Advanced find** filter icon.
1. In the **Advanced find** page, select **Available finance and operations entities** in the **Look for** drop-down list. 
1. Enter any other filter criteria to restrict the results to specific entities, and select **Results**.

    :::image type="content" source="../media/fovecatalog.png" alt-text="Screenshot of Catalog of entities.":::

1. Find and open the entity that you want to enable.
1. Select the **Visible** check box, and then save your change.

    :::image type="content" source="../media/foveenable.png" alt-text="Screenshot of Visible checkbox selected for an entity.":::

The virtual entity is generated and appears on all the appropriate menus. For example, it appears in the **Advanced find** dialog box.

## Refresh virtual entity metadata

Force a refresh of a virtual entity's metadata when you expect that the entity metadata in finance and operations apps has changed. To force a refresh, select the **Refresh** checkbox, and then save your change. The latest entity definition from finance and operations apps is synchronized to Dataverse, and the virtual entity is updated.

## Disable virtual entities

Virtual entities for finance and operations apps are in a managed solution and you can't delete them directly from the maker portal. To disable a virtual entity and remove the virtual entity metadata from the Dataverse environment, follow these steps:

1. Find and open the entity by following steps 1 through 8 in the [Generate virtual entities](enable-virtual-entities.md#generate-virtual-entities) section of this article.
1. Clear the **Visible** checkbox.
1. Save your change.

## Reference virtual entities

The **MicrosoftOperationsERPVE** solution generates all virtual entities and manages them through the API. When you make entities visible or hidden, the solution's items change. However, the solution remains a managed solution that you can depend on. 

The standard Application Lifecycle Management (ALM) flow is to take a standard reference to a virtual entity from this solution. Use the **Add existing** action in the independent software vendor (ISV) solution to do this. The virtual entity appears as a missing dependency of the solution, and the import process checks it. If a specified virtual entity doesn't exist during import, it's automatically made visible. No extra work is required.

To consume virtual entities, follow these steps:

1. In Dataverse, create a separate solution that contains the consuming logic. For more information, see [Create a solution](/powerapps/maker/data-platform/create-solution) in the Power Platform documentation.
1. Select **Add existing** \> **Table**. 
1. In the **Add existing tables** list, select the virtual entity that you want to reference.
1. When you're prompted to select assets to add, select any forms, views, or other elements that you want to customize, and then select **Finish**.

You can use the development tools to modify existing elements for the virtual entity, such as forms. You can also add new forms, views, and other elements.

:::image type="content" source="../media/fovesolution.png" alt-text="Screenshot of Solution.":::

When you export the solution, it contains hard dependencies on the virtual entity that the **MicrosoftOperationsERPVE** solution generates.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

