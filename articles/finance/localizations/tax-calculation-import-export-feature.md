---
# required metadata

title: Import and export tax calculations
description: This topic provides information about the import and export functionality of the tax calculation service.
author: Kai-Cloud
ms.date: 11/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-11-15
ms.dyn365.ops.version: 10.0.23
---
# Import and export tax calculations

This topic provides information about the import and export functionality of the tax calculation service. This functionality helps ensure a flexible and efficient configuration experience.

## Import and export tax codes

### Export templates

1. Sign in to [Regulatory Configuration Service (RCS)](https://marketing.configure.global.dynamics.com/).
2. In the **Globalization features** workspace, select **Features**, and then select the **Tax calculation** tile.
3. Select an existing feature, or [create a new feature](global-get-started-with-tax-calculation-service.md#set-up-tax-calculation-in-rcs).
4. In the **Versions** grid, select **Edit**.
5. On the **Tax calculation** feature page, set the [configuration version](global-get-started-with-tax-calculation-service.md#set-up-tax-calculation-in-rcs).
6. On the **Tax codes** tab, select **Import**.
7. Select **Export a tax code template** to download the **TaxCodesTemplate.zip** file.
8. Unzip **TaxCodesTemplate.zip**. The tax code templates are compressed separately according to **Calculation origin** value.
9. Unzip **By Net Amount.zip** to get the following comma-separated values (CSV) files:

    - **TaxCode.csv** – Enter the tax codes.
    - **TaxLimit.csv** – Enter the tax limits for each tax code.
    - **TaxRate.csv** – Enter the tax rates for each tax code.

> [!NOTE]
> By default, entries for the **Sample** tax code are available in the templates. If the **Sample** tax code isn't removed from the CSV files, it will be imported into the feature.

### Import tax codes

Follow these steps to import the **Sample** tax code in the template into your tax calculation feature.

1. In RCS, on the **Tax calculation** feature page, on the **Tax codes** tab, select **Import**.
2. Select **Browse**, find and select the **TaxCode.csv** file, and then, in the **Target table** field, select **Tax code**.
3. Select **OK** to import the tax code.
4. Find and select the **TaxRate.csv** file, and then, in the **Target table** field, select **Tax rate**.
5. Select **OK** to import the tax rate.
6. Find and select the **TaxLimit.csv** file, and then, in the **Target table** field, select **Tax limit**.
7. Select **OK** to import the tax limit.

You can also directly import the zip file that includes all three CSV files. In this way, you can quickly and easily complete the import.

1. In RCS, on the **Tax calculation** feature page, on the **Tax codes** tab, select **Import**.
2. Select **Browse**, find and select the **By Net Amount.zip** file, and then select **OK**.

### Export tax codes

1. In RCS, on the **Tax calculation** feature page, on the **Tax codes** tab, select **Export**.

    The **Export** button is available when there is at least one tax code in the **Tax codes** grid.

2. Select **OK** to export all tax codes of the feature in a zip file.

> [!NOTE]
> Use the exported file as a template to import tax codes into the corresponding feature.

## Import and export applicability rules

### Export applicability rules

1. Sign in to [RCS](https://marketing.configure.global.dynamics.com/).
2. In the **Globalization features** workspace, select **Features**, and then select the **Tax calculation** tile.
3. Select an existing feature, or [create a new feature](global-get-started-with-tax-calculation-service.md#set-up-tax-calculation-in-rcs).
4. In the **Versions** grid, select **Edit**.
5. On the **Tax calculation** feature page, set the [configuration version](global-get-started-with-tax-calculation-service.md#set-up-tax-calculation-in-rcs).
6. On the **Tax group applicability** tab, select the rows in the **Set up tax group applicability** grid.
7. Select the **Open in Microsoft Office** button, and then select **Tax service dynamic applicability matrix**.

    [![Exporting applicability rules to Microsoft Excel on the Tax calculation feature page.](./media/tax-cal-import-export-1.png)](./media/tax-cal-import-export-1.png)

8. Select **Download** to export the selected rows to a Microsoft Excel worksheet.

### Import applicability rules

The Excel worksheet that you downloaded contains the structure of the **Set up tax group applicability** grid. You can add new rules directly in the worksheet. When you've finished, follow these steps to import the new rules back into the **Set up tax group applicability** grid.

1. In the Excel worksheet, select and copy the rows to import.
2. In RCS, on the **Tax calculation** feature page, on the **Tax group applicability** tab, select **Add** to insert an empty record at the bottom of the **Set up tax group applicability** grid.
3. Select **Ctrl+V** to paste the copied rows into the grid.
4. Select **Save**.
