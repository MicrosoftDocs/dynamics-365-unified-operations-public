---
# required metadata

title: Resolve sales tax differences between purchase orders and invoices
description: This topic explains how to resolve sales tax differences between purchase orders and invoices.
author: kailiang
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: 
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version:

---

# Resolve sales tax differences between purchase orders and invoices
Sometimes, the sales tax for a purchase order and the sales tax for the corresponding vendor invoice differ. When this occurs, you should verify that the sales tax codes and sales tax amounts are correct for the vendor invoice.
> [!Note]
> If changes are needed, make corrections to the invoice lines before you change the sales tax information in the **Sales tax transactions** page. This includes changes that might affect the sales tax calculations. These changes include unit prices, quantities, and so on. It is especially important that you make any necessary changes to tax groups for invoice lines first. If you change tax groups for invoice lines, previous changes that you have made in the **Sales tax transactions** page might be recalculated.

## Purchase order and vendor invoice sales tax total amounts differ
The sales tax total amounts for the purchase order and for the vendor invoice that you receive from the vendor might differ. If invoice totals invoice matching is enabled, these differences could cause a matching discrepancy. If the **Post invoice with discrepancies** field in the **Accounts payable parameters** page is set to **Require approval**, and you are authorized to do this, you can approve the matching variance. If necessary, you can change a tax group for the invoice or correct the tax amounts for the invoice.

1. Select **Accounts payable > Vendor invoices > Pending vendor invoices**.

2. Select an invoice. The **Vendor invoice** page opens.

3. On the **Action Pane**, on the **Financials** tab, select **Sales tax**.

4. Compare the sales tax codes in the **Sales tax transactions** page with the sales tax codes on the invoice that you received from the vendor. If the invoice from the vendor includes sales tax codes that differ from the sales tax codes for the purchase order, determine whether the purchase order or the invoice is correct.

   - If the purchase order is correct, you can put the invoice on hold until the vendor provides a new invoice, and then continue to step 6. For information about putting an invoice on hold, see Key tasks: Vendor invoices.

   - If the invoice from the vendor is correct, follow these steps:

      a. Close the **Sales tax transactions** page.

      b. In the **Vendor invoice** page, select different tax groups for one or more invoice lines.

      c. On the **Action Pane**, on the **Financials** tab, select **Sales tax**.

5. Compare the sales tax amounts in the **Sales tax transactions** page with the sales tax amounts on the invoice that you received from your vendor. If the invoice from the vendor includes sales tax amounts that differ from the sales tax amounts for the purchase order, determine whether the purchase order or the invoice is correct.

   - If the purchase order is correct, you can put the invoice on hold until the vendor provides a new invoice, and then continue to step 6. 

   - If the invoice from the vendor is correct, follow these steps:

      a. On the **Adjustment** tab, in the **Total calculated sales tax amount** field, enter the correct sales tax amount.
         - If a difference for special line - then the Detail option for Adjust sales tax field should be used.
         - If an adjustment is required for a negative line, then a corresponding tax code amount should be updated with a negative amount.

      b. Select the **Override calculated sales tax** check box.

      c. Optional: The calculated sales tax amount might be incorrect if the tax rate for the sales tax code is incorrect. Verify the tax rate in the Sales tax codes page. (Select **Tax > Indirect taxes > Sales tax > Sales tax codes**.)

6. Close the **Sales tax transactions** page.

7. In the **Vendor invoice** page, save or post the invoice.

## Purchase order and vendor invoice sales tax codes differ
The sales tax codes for the purchase order and the vendor invoice might differ. You can change a tax group for the invoice, delete any sales tax codes that are not derived from the tax groups for the invoice, or reset the actual sales tax amount to the calculated amount.

1. Select **Accounts payable > Vendor invoices > Pending vendor invoices**.

2. Select an invoice. The **Vendor invoice** page opens.

3. On the **Action Pane**, on the **Financials** tab, select **Sales tax**.

4. Compare the sales tax codes in the **Sales tax transactions** page with the sales tax information for the invoice that you received from the vendor. If the invoice from the vendor includes sales tax codes that differ from the sales tax codes for the purchase order, determine whether the purchase order or the invoice is correct.

   - If the purchase order is correct, you can put the invoice on hold until the vendor provides a new invoice, and then continue to step 5.

   - If the invoice from the vendor is correct, complete one or more of the following procedures.   
        ### Change tax groups for the invoice

        a. Close the **Sales tax transactions** page.

        b. In the **Vendor invoice** page, select different tax groups for one or more invoice lines.

        c. On the **Action Pane**, on the **Financials** tab, select **Sales tax**.

        ### Delete non-derived sales tax codes

        - In the **Sales tax transactions** page, delete any sales tax code lines that are not included in the tax groups for the invoice lines. This might occur, for example, if the invoice was created by a service. If the **Keep sales tax adjustments for PO invoices** option is selected in the **Accounts payable parameters**, transactions that include sales tax code lines that are not derived from the intersection of the tax groups cannot be posted. This means that sales tax code lines that are not included in both the sales tax group and the item tax group for the invoice line cannot be posted.

        ### Reset actual amounts to the calculated amounts

        a. In the **Sales tax transactions** page, select the **Adjustment** tab, and then select **Reset actuals to calculated**.

        b. Review the sales tax code lines. If necessary, change the amount in the **Actual sales tax amount** field, and then select the **Override calculated sales tax** check box.

5. Close the **Sales tax transactions** page.

6. If required, verify invoice matching information.

7. In the **Vendor invoice** page, save or post the invoice.