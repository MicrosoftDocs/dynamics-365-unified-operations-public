---
title: Set up item tax groups
description: Learn how to set up item tax groups in the Tax Calculation, including overviews and processes for setting up and configuring tax groups. 
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

# Set up item tax groups

[!include [banner](../../includes/banner.md)]

This article explains how to set up item tax groups in the Tax Calculation feature. It also explains how to set up the item tax group applicability rule matrix and configure lines in the matrix.

The concept of item tax groups in the Tax Calculation feature resembles the concept of item sales tax groups in Microsoft Dynamics 365 Finance. They're groups of tax codes. The Tax Calculation feature uses the intersection of a tax group and an item tax group to determine the tax codes.

> [!IMPORTANT]
> The setup of item tax groups in the Tax Calculation feature of the Globalization studio workspace is legal entity–agnostic. When you enable the **Enable advanced tax calculation** in the Tax Calculation feature, the system automatically syncs item tax groups to the item sales tax groups for the selected legal entity.

## Set up an item tax group 

Follow these steps to set up an item tax group.

1. In Finance, open the **Globalization Studio** workspace, select **Globalization services**, and then select the **Tax Calculation** tile.
1. On the **Tax calculation features** page, select the feature and version that you want to set up, and then select **Edit**.
1. On the **General** tab, select **Configuration version**.
1. On the **Item tax group** tab, select **Manage column**. If you're setting up an item tax group for the first time, the fields in the **Manage column** dialog box are automatically set.
1. In the list on the left, expand the **Lines** node, and select the checkbox for **Item Tax Group**.

    :::image type="content" source="../media/select-item-tax-group.png" alt-text="Screenshot of Item Tax Group selected under the Lines node in the Manage columns dialog box.":::

1. Select the right arrow button to add **Item Tax Group** to the **Selected columns** list on the right.

    :::image type="content" source="../media/add-item-tax-group.png" alt-text="Screenshot of Item Tax Group added to the Selected columns list.":::

1. Select **OK**.

## Configure an item tax group

When you set up an item tax group, you create the applicability rule matrix. Add lines to the matrix to configure the item tax group.

1. On the **Item tax group** tab, select **Add**.
1. In the **Item tax group** field, enter the name of the item tax group.

    > [!IMPORTANT]
    > Limit the name of the item tax group to 10 characters. This name syncs with Finance, which has a limit of 10 characters for the names of item sales tax groups.

1. In the **Tax codes** field, select the checkbox for each tax code that you want to include in the item tax group. You can include multiple tax codes in one item tax group.

    :::image type="content" source="../media/multiple-tax-codes-selection.png" alt-text="Screenshot of multiple tax codes selected in the Tax codes field.":::

1. Repeat steps 1 through 3 to add more item tax groups.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
