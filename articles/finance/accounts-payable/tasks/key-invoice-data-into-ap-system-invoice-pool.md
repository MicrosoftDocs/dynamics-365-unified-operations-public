--- 
title: Key invoice data into the AP system using invoice pool
description: Learn about how to use the invoice register to create invoices, including step-by-step process on creating purchase orders and invoices.
author:  leizi2015
ms.author: raynezou
ms.topic: how-to
ms.date: 01/02/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0 
---

# Key invoice data into the AP system using invoice pool

[!include [banner](../../includes/banner.md)]

This article describes how to use the invoice register to create invoices. Then use the invoice pool to match the invoice to a purchase order and finalize the expense in the vendor invoice page.


## Create a purchase order
1. Go to **Accounts payable > Purchase orders > Purchase orders**.
2. Select **New** to create a purchase order.
3. In the **Vendor account** field, select a vendor for the drop-down list. For example, select vendor **1001**.
4. Select **OK**.
5. In the **Item number** field, select the services item number in the drop-down list. For example, select **S0001**. The net amount is 75.00. That is the amount that we will expect on the invoice.  
6. On the action pane, select **Purchase**.
7. Select **Confirm**.

## Create and post and invoice
1. Go to **Accounts payable > Invoices > Invoice register**.
2. Select **New**.
3. Open the lookup to select the name of the invoice register that you want to use.
4. Select the name of the invoice register that you want to use.
5. Select **Lines** to open the register and enter expense lines.
6. In the lookup, select a vendor. For example, select vendor **1001**.
7. In the **Invoice** field, enter the invoice number.
8. In the **Description** field, type a value.
9. In the **Credit** field, enter a number.
10. In the **Purchase order** field, open the drop-down list to select the purchase order that you created earlier.
11. In the **Approved by** field, highlight an approver in the drop-down list and click **Select** to select that approver.
12. Select **Post**.

## Open an invoice from the pool and match it to a purchase order to complete the invoice process
1. Go to **Accounts payable > Invoices > Invoice pool**.
2. Select **Purchase order** to create a vendor invoice from the invoice in the pool.
3. Select the invoice that you want to review.
4. Select **Update match status** to complete the matching.
5. On the action pane, select **Options**.
6. Select **Change view**.
7. Select **Grid view**.
8. Select **Post**.
9. Close the page.
10. Go to **Accounts payable > Vendors > Vendors**.
11. Select the vendor that was on the purchase order. For example, select vendor **1001**.
12. On the action pane, select **Vendor**.
13. Select **Transactions**.
14. Select the invoice that you created. The invoice register accrual was reversed and posted to the appropriate expense account.
    

## Import an invoice with automatic posting of invoice register journal
When receiving a vendor invoice, the initial step registers the invoice in the invoice register. This reflects the immediate accrual amount, which aligns with some country-/region-specific tax registration requirements. The process includes receipt matching, validating 3-way matching, and workflow approval for pending vendor invoices in the invoice pool. 

The **Vendor invoice automation with tax registration** feature automates the invoice register process for imported vendor invoices through the Data Management Framework (DMF). The **VENDORINVOICETYPE** field on vendor invoice header entity determines to generate a standard pending vendor invoice or post the invoice register journal in advance. When the field is **InvoicePool**, an invoice register journal is created and posted. The pending vendor invoice is generated in the invoice pool.

The streamlined process involves the following steps:
1. Create a purchase order.
2. Importing the invoice using the entities **Vendor invoice header** and **Vendor invoice line**.
After the invoice is imported successfully, the invoice register journal is automatically posted, and the pending vendor invoice is created within invoice pool. This integrated approach ensures efficiency and compliance with tax registration requirements.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
