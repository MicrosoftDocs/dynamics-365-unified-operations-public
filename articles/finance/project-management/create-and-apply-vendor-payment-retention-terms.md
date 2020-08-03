---
# required metadata

title: Create and apply vendor payment retention terms
description: This topic provides information about how to set up and maintain retention terms for vendor payments.
author: kfend
manager: AnnBe
ms.date: 05/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15

---

# Create and apply vendor payment retention terms

[!include [banner](../includes/banner.md)] 

Setting up vendor payment retention terms for a project is useful when your organization wants to retain part of the payments made to a vendor. For example, when you want to hold payment to a vendor until the products delivered meet your expectations. Vendor payment retention terms can be specified when you negotiate a vendor contract.

## Create vendor payment retention terms

You can enter the percentage of vendor payment for retention and the percentage of the previously retained amounts to be released. Amounts are automatically retained on vendor invoices until the contract reaches the specified state of completion. After you set up the retention terms, you can apply them to any project for that vendor.

Use the following steps to set up and maintain retention terms for vendor payments. 

1. Go to **Project management and accounting** > **Retention** > **Vendor payment retention terms**.
2. Select **New** to add a new vendor retention term. The **Rule ID** value for the new term is automatically entered. 
3. Enter a brief description in the **Description** field, and on the **Terms** FastTab, select **Add line** to enter term values for the following:

   - **Percentage of units delivered**: Enter a percentage of completion for the term. Amounts are automatically retained on vendor invoices until the project stage of completion is equal to the specified percentage. For example, if you enter 50.00, amounts are retained until the project is 50 percent completed.
   - **Percentage to retain**: Enter a percentage of the vendor invoice amount to be retained. For example, if you enter 10.00, then 10 percent of the amount on a vendor invoice is retained until the project reaches the percentage of completion as set in the **Percentage of units delivered field**.
   - **Percentage to release**: Select **Add line** to enter a percentage of any previously retained amounts to be released for the selected level of project completion.

> [!NOTE]
> If you have more than one milestone for different levels of project completion, enter a separate vendor retention term line for each retention rule. Each line can specify a different retention percentage and a different release percentage for each designated level of project completion.

After you create vendor retention terms for a vendor, you can apply the terms to a project.

## Apply vendor retention terms to a project

1. Go to **Project management and accounting** > **Projects** > **All projects** and open a project from the project list page.
2. On the **Vendor agreements** FastTab, select **Add line**.
3. In the **Account code field**, select one of the following options: 

   - **Table**: The vendor retention terms apply to a single vendor.
   - **Group**: The vendor retention terms apply to all vendors in a vendor group.
   - **All**: The vendor retention terms apply to all vendors.

4. In the **Vendor/Vendor group field**, select the vendor or vendor group to which the vendor retention terms apply. If you selected **All** in the previous step, this field is unavailable.
5. In the **Vendor retention terms** field, select the retention terms that you created in the previous procedure.
6. If the project also has pay-when-paid (PWP) terms set up for the vendor, enter the threshold percentage for the project in the **PWP threshold percentage** field.

The vendor retention terms are also displayed on purchase orders that you create for the vendor.
