---
title: Add dimensions to Excel templates
description: Learn about dimensions, dimensions that have entities, and the dimension controls that are available, including additional resources.
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 02/03/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Developer
ms.assetid: 20e6b97e-30ed-48d4-b63c-a073f80300b2
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Add dimensions to Excel templates

[!include [banner](../includes/banner.md)]

This article provides information about dimensions, dimensions that have entities, and the dimension controls that are available.

The only value present on Microsoft Excel templates after installation is the MainAccount. This dimension is the only one that all customers have. To add dimensions to Microsoft Excel templates, complete the following steps:

1. Add dimensions to the DimensionCombinationEntity or the DimensionSet entity.
1. Add the dimensions to each template where you want dimensions in separate columns. For more information, see [Create Open in Excel experiences](../office-integration/office-integration-edit-excel.md).
1. Add the [capability to look up financial dimension values in Excel](add-dimensions-excel-templates.md).
1. Publish the template.

This article shows how to modify DimensionCombinationEntity to enable the dimensions in columns for Excel. You can use the same steps to modify the DimensionSet entity.

>[!IMPORTANT]
> Data import by using Excel templates is optimized for performance and therefore supports only core field values. As a result, fields such as default dimensions and derived dimensions aren't automatically populated when importing lines through Excel.

> [!NOTE]
> This information is subject to change for each release. Therefore, be sure to check back frequently for the most up-to-date information.

## Add dimensions to Dynamics 365 Finance

1. In Microsoft Visual Studio, select **Dynamics 365 > Addins > Add financial dimensions for Odata**.
1. Enter the name of the financial dimension in the **Dimension name** column. Use the exact name of the financial dimension. Select the **Model** that has your extensions. It should be above the AppSuite layer. Select **Apply**.

:::image type="content" source="media/financial-dimensions-odata.png" alt-text="Screenshot of the Financial dimensions for OData add-in in Visual Studio.":::

1. Compile the project, and then synchronize it with the database.

> [!NOTE]
> You must keep the extension name "DimensionIntegration" for the project to work properly.

:::image type="content" source="media/8-300x260.png" alt-text="Screenshot of the menu options to build and synchronize in Visual Studio.":::

1. Your customization is now completed. You can test it in SQL using the following statement.

    ```sql
    select * from DIMENSIONCOMBINATIONENTITY 
    ```

1. To view the new dimension fields in the Excel templates, update the design as follows:
    1. Open the desired Excel template and select **Design**.
    1. Select the **pencil** next to the journal lines table to view the newly added fields.
    1. Select the newly added dimension field from the list of available fields and select **Add**.
    1. Once all fields are selected, select **Update**.
    1. Select **Refresh** to view the new dimension fields and related data.

## Additional resources

[Migrate default dimensions controls to Dimension Entry controls](dimension-entry-control-migration.md)

[Uptake of Dimension Entry controls](dimension-entry-control-uptake.md)

[Extensibility home page](../extensibility/extensibility-home-page.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
