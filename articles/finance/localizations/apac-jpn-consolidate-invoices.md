---
# required metadata

title: Consolidated invoices for Japan
description: In Japan, invoices are consolidated each month for payment. This article provides information about consolidated invoices, and explains how the invoice amount and due date are calculated.
author: EricWangChen
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustConsInvoice_JP, VendConsInvoice_JP
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: bd7255d9-0b0e-4372-8563-eaa559adbf24
ms.search.region: Japan
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Consolidated invoices for Japan

[!include [banner](../includes/banner.md)]

In Japan, invoices are consolidated each month for payment. This article provides information about consolidated invoices, and explains how the invoice amount and due date are calculated.

You can consolidate several vendor invoices, purchase orders, purchase returns, and purchase journals into a consolidated vendor invoice for payment. You don't have to issue payments for the separate vendor transactions. You can also consolidate customer invoices, sales orders, sales returns, and sales journals into a customer consolidated invoice that you can send to the customer.

You can create two or more consolidated invoices on the same day for a customer or a vendor. After you create a consolidated invoice for a customer or a vendor, you can pay the vendor or receive payment from the customer, and settle the consolidated invoice for the amount of the payment.

The following calculations are performed for a consolidated invoice:

- Invoice amount
- Due date

## Calculating the invoice amount for a consolidated invoice

After you create and confirm a consolidated invoice on the **Consolidated invoice** page, the following amounts are calculated:

- **Previous invoice amount** – The total invoice amount for the previous consolidation period.
- **Previously paid amount** – The total amount that was paid for the previous consolidation period.
- **Adjustment amount** – The adjustment amount for the previous consolidation period. The adjustment amount includes cash discounts and bank charges.
- **Outstanding amount** – The total outstanding amount for the current consolidation period. The outstanding amount is calculated by using the following formula: Previous invoice amount – Paid amount – Adjustment amount
- **Invoice amount during consolidation period** – The total invoice amount for the current consolidated invoice. This amount includes the sales tax.
- **Total invoice amount** – The new total invoice amount for the current invoice. This amount is calculated by using the following formula: Outstanding amount + Invoice amount during consolidation period

## Calculating the due date for a consolidated invoice

Invoices are consolidated each month, based on the consolidation day that you specify for each vendor or customer. The consolidation day determines the day and period that invoices are consolidated for, and the date that payment is due. If the last day of the month falls on a date that is earlier than the consolidation day that you specify, the invoices are consolidated on the last business day of the month. Therefore, if you specify 31 for the consolidation day, but the current month has fewer than 31 days, the invoices are consolidated on the last business day of that month. For example, the invoices for June 2012 are consolidated on June 29, 2012, because that is the last business day of the month. The following table shows how the payment due date is calculated for invoices that are generated on different days. The consolidation day is 10, and the payment date is the end of the month.

| Invoice number | Invoice date | Consolidation day | Due date      |
|----------------|--------------|-------------------|---------------|
| INV001         | May 4, 2012  | May 10, 2012      | June 29, 2012 |
| INV002         | May 10, 2012 | May 10, 2012      | June 29, 2012 |
| INV003         | May 18, 2012 | June 10, 2012     | July 31, 2012 |
| INV004         | June 8, 2012 | June 10, 2012     | July 31, 2012 |

## Tax adjustment on consolidated invoice

The primary purpose of this feature is to support consolidated monthly invoices for Japan as qualified invoices. Changes are introduced in relation to the Qualified Invoice System (QIS) for Japan. For more information, see [Qualified Invoice System in Japan](apac-jpn-qualified-invoice-system.md).

To support the QIS requirements that affect consolidated invoices, the following capabilities have been introduced (in both Accounts receivable and Accounts payable):

- Adjust (calculate and round) Japan Consumption Tax (JCT) once per qualified consolidated invoice and tax code.
- Set the accounting currency as a mandatory filter when you create consolidated invoices.
- Confirm a consolidated invoice to validate sales tax transaction properties, calculate the consolidated invoice tax and tax adjustment per sales tax code, and show the consolidated invoice tax and tax adjustments.
- Allow for manual adjustment of the calculated consolidated tax (Accounts payable only).
- Add a **Post** operation to post the tax adjustment per sales tax code.
- Print the Qualified Invoice Issuer (QII) number of the company on a consolidated qualified invoice (Accounts receivable only).
- Print a total tax breakdown, including the total invoice and total tax amounts per tax code, on a consolidated qualified invoice.
- Add a **Reverse** operation to reverse posted tax adjustments per sales tax code.

### Calculating the consolidated tax for a consolidated invoice

After you create and post a customer consolidated invoice, the consolidated consumption tax is calculated and adjusted in the following way at the consolidated invoice level in Accounts receivable and Accounts payable:

- The posted sales tax transactions for each sales tax code for all invoices that are included in the consolidated invoice are summed (in transaction currency) for the following values:

    - Amount origin
    - Actual sales tax amount
    - Actual nondeductible sales tax

- The consolidated tax is calculated as *Sum of the amount origin* &times; *Sales tax code rate value* &divide; 100. This calculation is done for each sales tax code, including nondeductible amounts, and rounded according to the rule in the sales tax code.
- The tax difference is calculated as *Consolidated tax* – *Sum of the actual sales tax amount*. If there's a difference per sales tax code, a tax adjustment is posted through a general ledger journal by using customer or vendor transactions, as appropriate.
- Posted transactions that are offset to the tax adjustment can be settled against invoice payments.

> [!NOTE]
> For a consolidated invoice from a vendor, a tax difference can occur only when manually entered actual consolidated tax amounts from the vendor invoice differ from the calculated amounts. In this case, the tax adjustment, including the non-deductible part, is posted to an expense or capitalizing account.

### Assumptions and limitations

Here are the main considerations for this functionality in Microsoft Dynamics 365 Finance:

- Sales tax calculation parameters should be configured in the following way. For more information, see [Set up sales tax for JCT](apac-jpn-qualified-invoice-system.md#set-up-sales-tax-for-jct).

    - All sales tax codes have an appropriate value for the **Tax type** field (**Standard** or **Reduced**).
    - The **Origin** field is set to **Percentage of net amount**.
    - The **Marginal base** field is set to **Net amount of invoice balance**.
    - The **Calculation method** field is set to **Whole amount**.

- Sales tax code parameters should not change during the invoicing period.
- Tax-inclusive scenarios aren't supported. 
- Vendor invoices that are posted via a vendor invoice journal aren't included in consolidation.
- Free text invoices and project invoices aren't included in consolidation for customers.
- Financial dimensions aren't inherited from the invoices that are included. Instead, they're entered from vendor/customer accounts.
- Only invoices in the company's accounting currency are included in a consolidated invoice.

> [!NOTE]
> If the **Tax adjustment on consolidated invoice** functionality doesn't meet any of your specific requirements, consider using the **Summary invoice** functionality instead. For more information, see [Consolidate sales orders or packing slips for posting](../accounts-receivable/configure-customer-invoices.md#consolidate-sales-orders-or-packing-slips-for-posting).

### Setup

To set up this feature, follow these steps.

1. In Feature Management, enable the **Enable tax adjustment on consolidated invoice for Japan** feature.
1. Complete the setup that's described in [Qualified Invoice System in Japan](apac-jpn-qualified-invoice-system.md).
1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**. On the **General** tab, turn on the **Consolidated invoice for customer** option. Then, in the **Consolidated invoice journal name** field, specify a general journal name of the **Daily** type to post consolidated tax adjustments.
1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**. On the **General** tab, turn on the **Consolidated invoice for vendor** option. Then, in the **Consolidated invoice journal name** field, specify a general journal name of the **Daily** type to post consolidated tax adjustments.

### Scenarios

#### Customer consolidated invoices with tax adjustment

Before you can complete this scenario, you must have posted sales invoices to customers.

To issue consolidated invoices to customers and post the tax adjustments, follow these steps.

1. Go to **Accounts receivable** \> **Periodic tasks** \> **Consolidated invoice**, and select **New**.
1. Specify the required **Execution date** and **Consolidation date** values. Add the **Customer account** value to the filter as required. Then select **OK**. The resulting consolidated invoice includes all invoices that were previously posted in the specified period and that match the filter criteria.
1. Review the data, and then select **Consolidated invoice** \> **Confirm**. The invoice status is changed to **Confirmed**.
1. Select **Consolidated invoice** \> **Sales tax**. The **Sales tax transactions** dialog box appears and shows unposted sales tax transactions for the tax adjustments for the consolidated invoice. The **Overview** tab contains additional fields for the consolidated amount origin, consolidated posted sales tax, and actual consolidated sales tax.
1. On the **Consolidated invoice** page, select **Post**. The following actions occur:

    1. Sales tax adjustments and a corresponding customer transaction are posted. The posting date is the consolidation date of the consolidated invoice.
    1. The total amount of the sales tax adjustment is added to **Invoice amount during consolidation**, **Sales tax**, and **Total invoice amount** on the consolidated invoice.
    1. The consolidated invoice is marked as **Posted**.

1. On the **Consolidated invoice** page, you can review the posted sales tax transactions by selecting the **Sales tax** menu for the posted consolidated invoice.
1. On the **Consolidated invoice** tab, select **Print**. The printed consolidated invoice contains the QII number of the legal entity. The printed sales tax specification includes both the original sales tax from the included invoices and the sales tax adjustments that were posted for the consolidated invoice.
1. Select **Consolidated invoice** \> **History**. The **Consolidated invoice history** page shows the posting history of the consolidated invoice, including the posting date and general ledger journal number.
1. Go to **Accounts receivable** \> **Payments** \> **Customer payment journal**, and create a new customer payment journal.
1. Select **Lines**, and create a new payment journal line for the customer.
1. Select **Settle transactions**.
1. In the **Settle transaction** dialog box, select **Consolidated invoice** \> **Select**.
1. In the **Select consolidated invoices** dialog box, select the **Consolidation ID** value of the newly created consolidated invoice, and then select **OK**. Only open customer transactions that correspond to the customer invoices that are included in the consolidated invoice are shown in the **Settle transaction** dialog box. In addition, the customer transaction that's posted for the consolidated invoice is shown and is available for settlement.

#### Reversal of customer consolidated invoices with tax adjustment

If you must edit a posted consolidated invoice because of missed invoices or extra invoices that were added by mistake, follow these steps to perform a consolidated invoice reversal.

1. Go to **Accounts receivable** \> **Periodic tasks** \> **Consolidated invoice**.
1. Select the previously posted consolidated invoice, and then select **Reverse**.
1. In the **Reversal transactions** dialog box, set the desired values for the **Use existing dates for reversal**, **Reversal date**, and **Reason comment** fields, and then select **Reverse**. The following actions occur:

    1. Reversing sales tax adjustments and a corresponding customer transaction are posted.
    1. The total amount of the sales tax adjustments that are being reversed is subtracted from the **Invoice amount during consolidation**, **Sales tax**, and **Total invoice amount** values of the consolidated invoice.
    1. The reversed consolidated invoice history record is marked as **Reversed**.
    1. The posted customer transaction that's related to the tax adjustment is settled against the customer transaction that corresponds to the reversing consolidated invoice history record.
    1. The consolidated invoice is unmarked as **Posted**. You can then reopen the consolidated invoice and edit its content (for example, add or remove invoices to include).

#### Consolidated invoices from vendors

Before you can complete this scenario, you must have posted purchase invoices from vendors.

To create a consolidated invoice from a vendor, follow these steps.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Consolidated invoice**, and select **New**.
1. Specify the required **Execution date** and **Consolidation date** values. Add the **Vendor account** value to the filter to select the desired vendors. Then select **OK**. The resulting consolidated invoice includes all invoices that were previously posted in the specified period and that match the filter criteria.
1. Review the data, and then select **Consolidated invoice** \> **Confirm**. The invoice status is changed to **Confirmed**, and consolidated taxes are calculated.
1. Select **Consolidated invoice** \> **Sales tax**. The **Temporary sales tax transactions** dialog box appears and shows the sales tax transactions to adjust.
1. On the **Adjustment** tab, adjust the **Actual consolidated tax amount** value according to the figures in the consolidated invoice from the vendor. Then select **Apply actual amounts** to apply the adjusted actual sales tax amounts or **Reset actual from calculated amounts** to reset the adjustment. When you've finished, select **OK**.
1. On the **Consolidated invoice** page, select **Consolidated invoice** \> **Post**. Sales tax adjustments and a corresponding vendor transaction are posted.
1. Select **Consolidated invoice** \> **History**. The **Consolidated invoice history** page shows the posting history of the consolidated invoice, including the posting date, voucher, and reversal.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
