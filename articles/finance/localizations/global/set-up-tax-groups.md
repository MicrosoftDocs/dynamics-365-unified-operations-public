---
title: Set up tax groups
description: Learn how to set up tax groups in the Tax Calculation service, including step-by-step processes for setting up tax groups and configuring a tax group.
author: wangchen
ms.author: wangchen
ms.topic: how-to 
ms.date: 03/19/2026
ms.reviewer: johnmichalak 
ms.search.region: Global
ms.search.validFrom: 2021-10-26
ms.search.form: TaxTable, TaxData   
ms.custom: 
  - bap-template
---

# Set up tax groups

[!include [banner](../../includes/banner.md)]

This article explains how to set up tax groups in the Tax Calculation feature. It also explains how to set up the tax group applicability rule matrix and configure lines in the matrix.

The concept of tax groups in the Tax Calculation feature resembles the concept of sales tax groups in Microsoft Dynamics 365 Finance. They're groups of tax codes. The Tax Calculation feature uses the intersection of a tax group and an item tax group to determine the tax codes.

However, tax groups in the Tax Calculation feature differ from sales tax groups in Finance in that they don't have additional parameters, such as **Use tax** and **Exempt tax**. Instead, those parameters are available at the tax code level.

> [!IMPORTANT]
> The setup of tax groups in the Tax Calculation of Globalization studio workspace is legal entity–agnostic. When you enable the **Enable advanced tax calculation** in the Tax calculation parameters, the system automatically syncs tax groups to the Sales tax groups for the selected legal entity.

## Set up a tax group

Follow these steps to set up a tax group.

1. In Finance, open the **Globalization Studio** workspace, select **Globalization services**, and then select the **Tax Calculation** tile.
1. On the **Tax calculation features** page, select the feature and version that you want to set up, and then select **Edit**.
1. On the **General** tab, select **Configuration version**.
1. On the **Tax group** tab, select **Manage Column**. If you're setting up a tax group for the first time, the fields in the **Manage column** dialog box are automatically set.
1. In the list on the left, expand the **Lines** node, and select the checkbox for **Tax Group**.

    :::image type="content" source="../media/select-tax-group.png" alt-text="Screenshot of Tax Group selected under the Lines Node in the Manage columns dialog box.":::

1. Select the right arrow button to add **Tax Group** to the **Selected columns** list on the right.

    :::image type="content" source="../media/add-tax-group.png" alt-text="Screenshot of Tax Group added to the Selected columns list.":::

1. Select **OK**.

## Configure a tax group

When you set up a tax group, you create the tax group applicability rule matrix. Add lines to the matrix to configure the tax group.

1. On the **Tax group** tab, select **Add**.
1. In the **Tax group** field, enter the name of the tax group.

    > [!IMPORTANT]
    > Limit the name of the tax group to 10 characters. This name syncs with Finance, which has a limit of 10 characters for the names of sales tax groups.

1. In the **Tax codes** field, select the checkbox for each tax code that you want to include in the tax group. You can include multiple tax codes in one tax group.

    :::image type="content" source="../media/multiple-tax-codes-selection.png" alt-text="Screenshot of multiple tax codes selected in the Tax codes field.":::

1. Repeat steps 1 through 3 to add more tax groups.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
