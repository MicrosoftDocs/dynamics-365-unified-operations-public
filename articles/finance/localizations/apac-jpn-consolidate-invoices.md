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

-   Invoice amount
-   Due date

## Calculating the invoice amount for a consolidated invoice
After you create and confirm a consolidated invoice on the **Consolidated invoice** page, the following amounts are calculated:

-   **Previous invoice amount** – The total invoice amount for the previous consolidation period.
-   **Previously paid amount** – The total amount that was paid for the previous consolidation period.
-   **Adjustment amount** – The adjustment amount for the previous consolidation period. The adjustment amount includes cash discounts and bank charges.
-   **Outstanding amount** – The total outstanding amount for the current consolidation period. The outstanding amount is calculated by using the following formula: Previous invoice amount – Paid amount – Adjustment amount
-   **Invoice amount during consolidation period** – The total invoice amount for the current consolidated invoice. This amount includes the sales tax.
-   **Total invoice amount** – The new total invoice amount for the current invoice. This amount is calculated by using the following formula: Outstanding amount + Invoice amount during consolidation period

## Calculating the due date for a consolidated invoice
Invoices are consolidated each month, based on the consolidation day that you specify for each vendor or customer. The consolidation day determines the day and period that invoices are consolidated for, and the date that payment is due. If the last day of the month falls on a date that is earlier than the consolidation day that you specify, the invoices are consolidated on the last business day of the month. Therefore, if you specify 31 for the consolidation day, but the current month has fewer than 31 days, the invoices are consolidated on the last business day of that month. For example, the invoices for June 2012 are consolidated on June 29, 2012, because that is the last business day of the month. The following table shows how the payment due date is calculated for invoices that are generated on different days. The consolidation day is 10, and the payment date is the end of the month.

| Invoice number | Invoice date | Consolidation day | Due date      |
|----------------|--------------|-------------------|---------------|
| INV001         | May 4, 2012  | May 10, 2012      | June 29, 2012 |
| INV002         | May 10, 2012 | May 10, 2012      | June 29, 2012 |
| INV003         | May 18, 2012 | June 10, 2012     | July 31, 2012 |
| INV004         | June 8, 2012 | June 10, 2012     | July 31, 2012 |

## Tax adjustment on consolidated invoice
The primary goal of this feature is to support consolidated monthly invoices for Japan as qualified invoices: changes are introduced in relation to the Qualified Invoice System (QIS) for Japan.

For more information on the Qualified Invoice System (QIS) for Japan, see [Qualified Invoice System](apac-jpn-qualified-invoice-system.md).

To support the QIS requirements that impact consolidated invoices, the following capabilities have been introduced (both Accounts Receivable and Accounts Payable):
- Adjust (calculate and round off) Japan Consumption Tax (JCT) once per consolidated qualified invoice and tax rate.
- Set transaction currency as a mandatory filter when creating consolidated invoices.
- Confirm a consolidated invoice to validate sales tax transaction properties, calculate the consolidated invoice tax and tax adjustment per sales tax code, and display the consolidated invoice tax and tax adjustments. 
- Allow manual adjustment of the calculated consolidated tax (Accounts Payable only). 
- Add Post operation to post the tax adjustment per sales tax code. 
- Print the Qualified Invoice Issuer (QII) number of the company on a consolidated qualified invoice (Accounts Receivable only). 
- Print a total tax breakdown, including total invoice and total tax amounts per tax rate, on a consolidated qualified invoice.
- Reverse operation to reverse posted tax adjustments per sales tax code.

### Calculating the consolidated tax for a consolidated invoice
After you create and post a customer consolidated invoice, the following amounts are calculated:
+ Consolidated consumption tax is calculated and adjusted on the consolidated invoice level in Accounts receivable: summing up posted sales tax transactions per sales tax code for all invoices included in the consolidated invoice.
+ Consolidated tax = Amount origin \* Value/100. Round off according to the rule in the sales tax code.
+ Tax adjustment are posted in case of a difference.
+ Posted tax adjustment can be settled against invoice payments. 

After you create and post a consolidated invoice from vendor, the following amounts are calculated:
+ Consolidated consumption tax is calculated on the consolidated invoice level in Accounts payable: summing up posted sales tax transactions per sales tax code for all invoices included in the consolidated invoice.
+ Consolidated tax = Amount origin \* Value/100.
+ If applicable, manually entered tax adjustment including non-deductible part are posted to an expense / capitalizing account.
+ Posted tax adjustment can be settled against invoice payments. 

### Assumptions and Limitations
The main considerations for this functionality in Finance are as follows:
- Sales tax calculation parameters should be configured as follows (for more infpormation, see [Setting up Sales tax for JCT](apac-jpn-qualified-invoice-system#setting-up-sales-tax-for-jct.md):
    - All sales tax codes must have appropriate **Tax type** (*Standard and/or Reduced*), 
	- **Origin = Percentage of net amount**, 
	- **Marginal base = Net amount of invoice balance**, 
	- **Calculation method = Whole amount**.	
- Sales tax code parameters do not change during the invoicing period.
- Tax-inclusive scenarios are not supported. 
- Vendor invoices posted via vendor invoice journal are not supported.
- Free text invoices and project invoices are not supported for customers.
- Financial dimensions are not inherited from included invoice but populated from vendor/customer accounts.
- Only invpoices in company's accounting currency are included in a consolidated invoice.

> [!NOTE]
> In case when the limited **Tax adjustment on consolidated invoice** functionality doesn't fit with one or another the specific requirement, please consider use of the Summary orders functionality.
> For more information, see [Consolidate sales orders or packing slips for posting](/dynamics365/finance/accounts-receivable/configure-customer-invoices#consolidate-sales-orders-or-packing-slips-for-posting/)

### Setup
To set up this feature, follow these steps:

1. Enable the “Enable tax adjustment on consolidated invoice for Japan” feature in Feature Management.
1. Perform setup as desribed on [Qualified Invoice System in Japan](apac-jpn-qualified-invoice-system.md) page.
1. Go to **Accounts receivable parameters**, the **General** tab and specify general journal name with **Daily** type in the **Consolidated invoice journal name** field to post consolidated tax adjustments.

### Scenarios

#### Customer consolidated invoices with tax adjustment
Before you can complete this scenario, you must have posted sales invoices to customers. To issue consolidated invoices to customers and post the tax adjustments, follow these steps:
1. Go to **Accounts Receivable -> Periodic tasks -> Consolidated invoice** page and click **New**. 
1. Specify the required **Execution date** and **Consolidation date**. Add the **Customer account** to the filter, if needed. Click **OK**.
1. Resulting consolidated invoice willl include all invoices posted previously in the specified period and in line with the filter criteria.
1. Check the data and click on the **Consolidated invoice -> Confirm** button. Invoice status will change to Confirmed.
1. Click **Consolidated invoice -> Sales tax**. The Sales tax transactions dialog page will open. The page displays unposted sales tax transactions for the tax adjustments for the consolidated invoice. The Overview tab should contain additional fields for Consolidated amount origin, Consolidated posted sales tax, and Actual consolidated sales tax.
1. On the **Consolidated invoice page**,  click **Post**. Sales tax adjustments and a corresponding customer transaction are posted. The posting date is the Consolidation date of the consolidated invoice. The total amount of sales tax adjustment is added to "Invoice amount during consolidation", "Sales tax", "and Total invoice amount" of the consolidated invoice. The consolidated invoice is marked as Posted.
1. On the **Consolidated invoice page**, by clicking the **Sales tax** menu for the posted consolidated invoice, it is possible to review posted sales tax transactions, including Consolidated amount origin, Consolidated posted sales tax, and Actual consolidated sales tax.
1. Click **Print** under the **Consolidated invoice** tab. The printed consolidated invoice contains the qualified invoice issuer number of the legal entity. The printed sales tax specification includes both original sales tax from included invoices and sales tax adjustments posted for the consolidated invoice.
1. Click **Consolidated invoice -> History**.  The Consolidated invoice history page displays the history of posting of the consolidated invoice, including the posting date, GL journal number, etc.
1. Go to **Accounts Receivable -> Payments -> Customer payment journal** page. Create a new customer payment journal and click **Lines**. Create a new payment journal line for the customer.
1. Click **Settle transactions**. On the Settle transaction dialog page, click **Consolidated invoice -> Select**. In the Select consolidated invoices dialog, select the newly created consolidated invoice **Consolidation ID** and click OK. Only open customer transactions that correspond to the customer invoices included in the consolidated invoice are displayed on the Settle transaction page. In addition, the customer transaction that is posted for the consolidated invoice is also displayed and available for settlement.

#### Reversal of customer consolidated invoices with tax adjustment
In case you need to edit a posted consolidated invpioce due to missed invoices or, vice versa, extra invoices added by mistake, a consolidated invoice reversal can be performed in the following way. 
1. Go back to the **Consolidated invoice** page, select the consolidated invoice posted previously, and click **Reverse**. 
1. On the Reversal transactions dialog, specify the desired values for *Use existing dates for reversal*, *Reversal date* and *Reason comment*, and click **Reverse**. 
1. Reversing sales tax adjustments and a corresponding customer transactions are posted. 
1. The total amount of sales tax adjustments being reversed is subtracted from *Invoice amount during consolidation*, *Sales tax*, and *Total invoice amount* of the consolidated invoice.
1. The reversed consolidated invoice history record is marked as Reversed. 
1. The customer transaction is settled against the customer transaction that corresponds to the reversing consolidated invoice history record. 
1. The consolidated invoice is un-marked as Posted. It is then possible to **Reopen** the consolidated invoice and edit its content (add or remove invoices to be included in it).

#### Consolidated invoices from vendors
Before you can complete this scenario, you must have posted purchase invoices from vendors that are Qualified Invoice Issuers. 
To create a consolidated invoice from a vendor, follow these steps:
1. Go to **Accounts Payable -> Periodic tasks -> Consolidated invoice** page and click **New**. 
1. Specify the required **Execution date** and **Consolidation date**. Add the **Vendor account** to the filter to select the desired vendor(s). Click **OK**.
1. Resulting consolidated invoice willl include all invoices posted previously in the specified period and in line with the filter criteria.
1. Check the data and click on the **Consolidated invoice -> Confirm** button to change the invoice status to Confirmed and calculate consolidated taxes.
1. Click **Consolidated Invoice -> Sales Tax** to open the **Temporary sales tax transactions** dialog page, which displays sales tax transactions to adjust
1. On the **Adjustment** tab, adjust **Actual consolidated tax amount** according to figures in the consolidated invoice from the vendor, then click **Apply actual amounts** to apply adjusted actual sales tax amounts or **Reset actual from calculated amounts** to reset the adjustment. Click **OK**.
1. On the Consolidated Invoice page, click **Consolidated Invoice -> Post** to post sales tax adjustments and a corresponding vendor transaction.
1. Click **Consolidated invoice -> History**.  The Consolidated invoice history page displays the history of posting of the consolidated invoice, including the posting date, voucher, reversal, etc.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
