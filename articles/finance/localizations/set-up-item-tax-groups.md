---
# required metadata 

title: Set up item tax groups
description: This article explains how to set up item tax groups in the Tax Calculation service. 
author: wangchen
ms.date: 11/30/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxTable, TaxData   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-10-26 
ms.dyn365.ops.version: Version 10.0.21 
---

# Set up item tax groups

[!include [banner](../includes/banner.md)]

This article explains how to set up item tax groups in the Tax Calculation service. It also explains how to set up the item tax group applicability rule matrix and configure lines in the matrix.

The concept of item tax groups in the Tax Calculation service resembles the concept of item sales tax groups in Microsoft Dynamics 365 Finance. They are groups of tax codes. The Tax Calculation service uses the intersection of a tax group and an item tax group to determine the tax codes.

> [!IMPORTANT]
> The setup of item tax groups in the Tax Calculation service is legal entity–agnostic. You can complete this setup in Regulatory Configuration Service (RCS) only one time. When you enable the Tax Calculation service in Finance, item tax groups are automatically synced for the selected legal entity.

## Set up an item tax group 

Follow these steps to set up an item tax group.

1. Sign in to [Regulatory Configuration Service](https://marketing.configure.global.dynamics.com/).
2. Go to **Workspaces** \> **Globalization features** \> **Tax calculation**.
3. Select the feature and version that you want to set up, and then select **Edit**.
4. On the **General** tab, select **Configuration version**.
5. On the **Item tax group** tab, select **Manage column**. If you're setting up an item tax group for the first time, the fields in the **Manage column** dialog box are automatically set.
6. In the list on the left, expand the **Lines** node, and select the checkbox for **Item Tax Group**.

    ![Item Tax Group selected under the Lines node in the Manage columns dialog box.](media/select-item-tax-group.png)

7. Select the right arrow button to add **Item Tax Group** to the **Selected columns** list on the right.

    ![Item Tax Group added to the Selected columns list.](media/add-item-tax-group.png)

8. Select **OK**.

## Configure an item tax group

After you set up an item tax group, the applicability rule matrix is created. You can add lines to the matrix to configure the item tax group.

1. On the **Item tax group** tab, select **Add**.
2. In the **Item tax group** field, enter the name of the item tax group.

    > [!IMPORTANT]
    > We recommend that you limit the name of the item tax group to 10 characters. This name is synced with Finance, which has a limit of 10 characters for the names of item sales tax groups.

3. In the **Tax codes** field, select the checkbox for each tax code that you want to include in the item tax group. You can include multiple tax codes in one item tax group.

    ![Multiple tax codes selected in the Tax codes field.](media/multiple-tax-codes-selection.png)

4. Repeat steps 1 through 3 to add more item tax groups.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
