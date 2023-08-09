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

## Qualified consolidated invoices
The primary goal of this feature is to support consolidated monthly invoices for Japan as qualified invoices: changes are introduced in relation to the Qualified Invoice System (QIS) for Japan.

For more information on the requirements of the Qualified Invoice System (QIS) for Japan, see ....

The following are significant QIS requirements that impact consolidated invoices:

- Calculate and round off Japan Consumption Tax (JCT) once per qualified invoice and tax rate.
- Print the Qualified Invoice Issuer (QII) number of the company on a qualified invoice.
- Print a total tax breakdown, including total invoice and total tax amounts per tax rate, on a qualified invoice.

Consolidated/monthly invoicing is a widely accepted business practice in Japan, where businesses issue monthly invoices to their customers. A consolidated invoice summarizes all deliveries to a customer over a month and sets payment terms/dates. The customer then pays against the consolidated invoice.

Dynamics 365 Finance has Japan-specific functionality to support this business practice. A consolidated invoice is a collection of customer invoices posted during a month. There is a printed form of a consolidated invoice, and it is possible to settle customer payments against consolidated invoices. Similar functionality also exists for the Account payable side.

### Assumptions
According to legal and business practice perspectives, the following approach is wide-used in in Japan:
- Issue an (non-qualified) invoice for each delivery and then issue a consolidated/monthly invoice. Treat the consolidated/monthly invoice as a qualified invoice. This implies recalculation of taxes for the consolidated invoice and application of rounding to the total consolidated invoice tax amount per tax code, including posting tax adjustments. 
- The common business practice is to use tax-exclusive pricing. 

### Limitations
The following are not covered by this system in Finance:
- It is possible for a company to configure sales tax codes so that two or more sales tax codes with the same tax rate are never used in one and the same consolidated vendor or customer invoice.
- Only specific sales tax calculation parameters are supported.
- Sales tax code parameters do not change during the invoicing period.
- Tax-inclusive scenarios are not supported because the common business practice is to use tax-exclusive pricing. 
- Only consolidation of sales invoices is supported. Free text invoices and project invoices cannot be consolidated.
- Financial dimensions can only be populated from vendor/customer accounts.
- Only accounting currency is supported.

### Scope
The following changes must be made within the scope of this feature:
1. Consolidated invoice creation and processing (both AP and AR): 

    a. Split consolidated invoices per transaction currency. Add transaction currency as a default filter when creating consolidated invoices. 
    b. Modify the Confirm operation to validate sales tax transaction properties, calculate the consolidated invoice tax and tax adjustment per sales tax code, and display the consolidated invoice tax and tax adjustments. 
    c. Allow manual adjustment of the calculated consolidated tax (AP only). 
    d. Add Post operation to post the tax adjustment per sales tax code. 
    e. Print consolidated invoice (AR only). 
    f. Add Reverse operation to reverse posted tax adjustments per sales tax code.

2. Consolidated tax calculation (both Accounts Receivable and Accounts Payable): 
    a. Sum up posted sales tax transactions per sales tax code for all invoices included in the consolidated invoice. 
    b. Consolidated tax = Amount origin \* Value/100. Round off according to the rule in the sales tax code.

Vendor invoices posted via vendor invoice journal are not supported in the vendor consolidated invoice functionality and will not be included in this feature.

Free text invoices and project invoices are not supported in the customer consolidated invoice functionality and will not be included in this feature.

### Setup
To set up this feature, follow these steps:

1. Enable the “Enable tax adjustment on consolidated invoice for Japan” feature in Feature Management.
1. Configure a registration type for QII registration for Japan and link it to the “Qualified Invoice Issuer” registration category.
1. Add a QII registration number to the primary address of the legal entity that is in Japan.
1. Set up sales tax codes for JCT, including separate sales tax codes for standard rate (10%) and reduced rate (8%), as well as separate sales tax codes for purchases from qualified invoice issuers and non-qualified invoice issuers.
1. Set up sales tax groups for JCT, one for qualified invoice issuers and another one for non-qualified invoice issuers.
1. Set up item sales tax groups for JCT 10% and JCT 8%.
1. Specify sales tax groups on vendor master records, one vendor as QII, and another one as non-QII.
1. Specify item sales tax groups for purchases and for sales on items: two for JCT 10% and another two for JCT 8%.
1. Create charges codes for AP and AR with JCT 8%.
1. Specify journal names to post consolidated tax adjustments.

### Scenarios
#### Consolidated Invoice issued to a Customer
To create a customer payment journal, open the Customer Payment Journal page, create a new customer payment journal, and click Lines. Create a new payment journal line for the customer and click Settle Transactions. On the Settle Transaction dialog page, click Consolidated Invoice -> Select. In the Select Consolidated Invoices dialog, select the newly created consolidated invoice and click OK.

#### Consolidated Invoice from a Vendor that is a Qualified Invoice Issuer
To create a consolidated invoice from a vendor that is a qualified invoice issuer, follow these steps:
1. Create two purchase orders from a vendor that is a qualified invoice issuer and post purchase invoices for them in the last month.
1. Open the AP Consolidated Invoice page, click New, specify the last day of the last month as Execution date and Consolidation date, add the vendor account to the filter, and click OK.
1. Click Consolidated Invoice -> Confirm to change the invoice status to Confirmed, calculate consolidated taxes and tax adjustments, and create unposted tax transactions.
1. Click Consolidated Invoice -> Sales Tax to open the Sales Tax Transactions dialog page, which displays unposted sales tax transactions for the tax adjustments for the consolidated invoice.
1. On the Adjustment tab, adjust Actual consolidated tax amount according to figures in the consolidated invoice from the vendor, then click Apply actual amounts to apply adjusted actual sales tax amounts.
1. On the Consolidated Invoice page, click Consolidated Invoice -> Post to post sales tax adjustments and a corresponding vendor transaction.

#### Consolidated Invoice from a Vendor that is a Non-Qualified Invoice Issuer
To create a consolidated invoice from a vendor that is a non-qualified invoice issuer, follow these steps:
1. Create two purchase orders from a vendor that is a non-qualified invoice issuer and post purchase invoices for them in the last month.
1. Open the AP Consolidated Invoice page, click New, specify the last day of the last month as Execution date and Consolidation date, add the vendor account to the filter, and click OK.
1. Click Consolidated Invoice -> Confirm to change the invoice status to Confirmed, calculate consolidated taxes and tax adjustments (including calculation of consolidated nondeductible sales tax), and create unposted tax transactions.
1. Click Consolidated Invoice -> Sales Tax to open the Sales Tax Transactions dialog page, which displays unposted sales tax transactions for the tax adjustments for the consolidated invoice.
1. On the Adjustment tab, adjust Actual consolidated tax amount according to figures in the consolidated invoice from the vendor (including calculation of consolidated nondeductible sales tax adjustments), then click Apply actual amounts to apply adjusted actual sales tax amounts.
1. On the Consolidated Invoice page, click Consolidated Invoice -> Post to post sales tax adjustments (including posting of consolidated nondeductible sales tax adjustments) and a corresponding vendor transaction.

> [!NOTE]
> On the Consolidated Invoice page, click Consolidated Invoice -> Sales Tax to review posted sales tax transactions for the last consolidated invoice history record. On the Consolidated Invoice page, click Consolidated Invoice -> History to display the history of posting of the consolidated invoice. It is possible to review the voucher, posted sales tax transactions, and vendor transaction for the history record by clicking corresponding menu items on the page.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
