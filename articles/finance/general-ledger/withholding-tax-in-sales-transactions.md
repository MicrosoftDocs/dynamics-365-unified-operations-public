---
# required metadata

title: Withholding tax in sales transactions
description: This article explains how to enable the calculation of withholding tax for selected customers. For customers who specify withholding tax in their payments to you, you can assign the default withholding tax group. 
author: kailiang
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2020-01-12
ms.dyn365.ops.version: AX 10.0.16

---

# Withholding tax in sales transactions

This article lists the steps to enable the calculation of withholding tax for selected customers. For customers who specify withholding tax in their payments to you, you can assign the default **Withholding tax group** on the **Customers** page. 

1. Go to **Navigation pane > Modules > Accounts receivable > Customers > All customers**.

2. Click the respective customer account, click **Edit**.

3. In the **Invoice and delivery** tab, set the **Calculate withholding tax** field to **Yes**.

   > [!NOTE] 
   > Withholding tax will not be calculated if **Calculate withholding tax** is not switched on for this customer in the master data.

4. Select a withholding tax group in **Withholding tax group**.

5. Click **Save**.

For items/services, which are liable to withholding tax, you can assign the default **Item withholding tax group** in **Released Products**.

1. Go to **Navigation pane > Modules > Product information management > Products > Released products**.

2. Click the respective Item number, click **Edit**.

3. In the **Sell** tab, click **Calculate withholding tax**.

   > [!NOTE] 
   > Withholding tax will not be calculated if **Calculate withholding tax** is not set to **Yes** for this Item in the **Sell** tab on the **Released product** page.

4. Select an Item withholding tax group in **Item withholding tax group** list.

5. Click **Save**.

Withholding tax groups and Item withholding tax groups can be assigned using the **Sales order** page. 

The default Withholding tax group and Item withholding tax group is used as default entries on sales order lines when you create a new sales order.
   > [!NOTE] 
   > Starting in version 10.0.32, the **Withholding tax group** and **Item withholding tax group** fields are integrated into the lines on the **Free text invoice** page. Withholding tax is calculated and posted when free text invoices are settled.

Withholding tax is calculated and posted with **Customer payment journal**. You can manually adjust the applicable withholding tax code and the actual withholding tax amount in the **Withholding tax** tab on the **Settle transactions** page.

The calculated withholding tax amount is deducted from the customer payment and posted to the **Withholding tax offset** account in a related voucher.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
