---
title: Set up tax groups
description: Learn how to set up tax groups in the Tax Calculation service, including step-by-step processes for setting up tax groups and configuring a tax group.
author: wangchen
ms.author: wangchen
ms.topic: how-to 
ms.date: 02/09/2024 
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-10-26
ms.search.form: TaxTable, TaxData   
ms.dyn365.ops.version: Version 10.0.21 
---

# Set up tax groups

[!include [banner](../../includes/banner.md)]

This article explains how to set up tax groups in the Tax Calculation feature. It also explains how to set up the tax group applicability rule matrix and configure lines in the matrix.

The concept of tax groups in the Tax Calculation feature resembles the concept of sales tax groups in Microsoft Dynamics 365 Finance. They are groups of tax codes. The Tax Calculation feature uses the intersection of a tax group and an item tax group to determine the tax codes.

However, tax groups in the Tax Calculation feature differ from sales tax groups in Finance in that there are no additional parameters on them, such as **Use tax** and **Exempt tax**. Instead, those parameters are available at the tax code level.

> [!IMPORTANT]
> The setup of tax groups in the Tax Calculation service is legal entity–agnostic. You can complete this setup in Regulatory Configuration Service (RCS) only one time. When you enable the Tax Calculation service in Finance, tax groups are automatically synced for the selected legal entity.

> [!NOTE]
> The functionality of RCS is merged to the **Globalization Studio** workspace in Finance in version 10.0.39. For more information, see [Regulatory Configuration Service merge to the Globalization Studio workspace](workspace/merge-rcs-to-gsw.md).
>
> If you're using version 10.0.39 or later, use the **Globalization Studio** workspace in Finance instead of RCS.

## Set up a tax group

Follow these steps to set up a tax group.

1. Follow one of these steps, depending on where you're completing the procedure:

    - In Finance, open the **Globalization Studio** workspace, select **Globalization services**, and then select the **Tax Calculation** tile.

2. On the **Tax calculation features** page, select the feature and version that you want to set up, and then select **Edit**.
3. On the **General** tab, select **Configuration version**.
4. On the **Tax group** tab, select **Manage Column**. If you're setting up a tax group for the first time, the fields in the **Manage column** dialog box are automatically set.
5. In the list on the left, expand the **Lines** node, and select the checkbox for **Tax Group**.

    ![Tax Group selected under the Lines Node in the Manage columns dialog box.](../media/select-tax-group.png)

6. Select the right arrow button to add **Tax Group** to the **Selected columns** list on the right.

    ![Tax Group added to the Selected columns list.](../media/add-tax-group.png)

7. Select **OK**.

## Configure a tax group

After you set up a tax group, the tax group applicability rule matrix is created. You can add lines to the matrix to configure the tax group.

1. On the **Tax group** tab, select **Add**.
2. In the **Tax group** field, enter the name of the tax group.

    > [!IMPORTANT]
    > We recommend that you limit the name of the tax group to 10 characters. This name is synced with Finance, which has a limit of 10 characters for the names of sales tax groups.

3. In the **Tax codes** field, select the checkbox for each tax code that you want to include in the tax group. You can include multiple tax codes in one tax group.

    ![Multiple tax codes selected in the Tax codes field.](../media/multiple-tax-codes-selection.png)

4. Repeat steps 1 through 3 to add more tax groups.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
