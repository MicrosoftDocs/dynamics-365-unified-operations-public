---
title: Invoice issue deadline
description: This article explains how to set up parameters to calculate the due dates for issuing customer invoices and vendor invoices in the European Union (EU).
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Iceland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: CustParameters, LedgerInvoiceIssueDueDateSetup_W
---

# Invoice issue deadline

[!include [banner](../includes/banner.md)]

This article explains how to set up parameters to calculate the due dates for issuing customer invoices and vendor invoices in the European Union (EU).

European Union (EU) Directive 45/2010 and other directives require that shipments within the EU (intra-EU shipments) must be invoiced on or before the fifteenth day of the month after the delivery is made. At the same time, each EU country can have different invoicing deadlines for domestic deliveries. Invoice issue due date functionality lets you align the date interval to the country/region type. Then, for all shipments to and from a country/region of a particular type, the invoice issue due date is calculated by using rules that are set in the specified date interval. In addition, you can get all packing slips that have a specific invoice issue due date, filter by invoice issue due date during periodic sales invoicing, and control the sales invoice issue date during invoice posting. You can set up a date interval code, and then set up a calculation rule for the invoice issue date by assigning the date interval code to a country/region type. The calculation rule is used to calculate the due date for issuing invoices for the following transactions:

-   Intra-EU shipments
-   Domestic shipments within an EU member state

You can also set up date controls to help guarantee that customer invoices and credit notes for customer transactions are generated within the specified period after the delivery is made.

## Prerequisites
The following table shows the prerequisites that must be in place before you can use the invoice issue due date functionality .

| Category            | Prerequisite                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Country/region      | The primary address of the legal entity must be in a EU member state.                                                                                                                                                                                                                                                                                                                    |
| Related setup tasks | On the **Date intervals** page, set up a date interval that is used to calculate the invoice issue due date. (Click **General Ledger** &gt; **Ledger setup** &gt; **Date intervals**.) On the **Foreign trade parameters** page, set up foreign trade properties for various countries/regions. (Click **Tax** &gt; **Setup** &gt; **Foreign trade** &gt; **Foreign trade parameters**.) |

## Invoice issue due date calculation rule
Use the **Set up calculation for invoice issue due date** page to set up an invoice issue due date calculation rule by assigning a date interval code to a country/region type.

## Date control parameters for customer invoices and credit notes
You can set up date control parameters to help guarantee that customer invoices and credit notes for customer transactions are generated within the specified period after the delivery is made. You can find these parameters in the **Invoice dates control** area of the **Accounts receivable parameters** page.

## Example
To calculate invoice issue due dates for intra-EU shipments on the fifteenth day of the month after the supply is delivered, create a date interval code and calculation rule that have the following settings.

### Date interval code

| Field                                                           | Value                           |
|-----------------------------------------------------------------|---------------------------------|
| Date interval code                                              | 15-NM                           |
| Description                                                     | Fifteenth day of the next month |
| Before (In the **To date** field group)                         | Month                           |
| Start/End (In the **To date** field group)                      | End                             |
| +/- (In the **To date** field group)                            | 15                              |
| Days, months, years or periods (In the **To date** field group) | Days                            |

### Invoice issue due date calculation rule

| Field               | Value                                                     |
|---------------------|-----------------------------------------------------------|
| Country/region type | **EU**                                                    |
| Start date          | Enter the date when the current setup line becomes valid. |
| Date interval code  | **15-NM**                                                 |

## Next steps
After you've finished setting up the parameters to calculate invoice issue due dates, you can create and post the following transactions to automatically calculate and update the due dates for issuing invoices:

-   **Sales orders** – When you create a sales order and post a packing slip, the due date for issuing the invoice is calculated and updated on the packing slip. The due date is calculated based on the date interval that is associated with the country/region that is specified in the delivery address of the sales order. After you post the packing slip, you can verify the invoice issue due date in the **Invoice issue due date** field on the **Packing slip journal** page. (Click **Sales and marketing** &gt; **Sales order** &gt; **Order shipping** &gt; **Packing slip**.) You can view all the packing slips that aren't invoiced, and their invoice issue due dates, on the **Packing slips not invoiced** page. (Click **Sales and marketing** &gt; **Sales order** &gt; **Order shipping** &gt; **Packing slips not invoiced**.)
-   **Purchase orders** – When you create a purchase order and post a product receipt, the due date for issuing the invoice is calculated and updated on the product receipt. The due date is calculated based on the date interval that is associated with the country/region that is specified in the primary address of the vendor. After you post the product receipt, you can verify the invoice issue due date in the **Invoice issue due date** field on the **Product receipt journal** page. (Click **Procurement and sourcing** &gt; **Purchase orders** &gt; **Receiving products** &gt; **Product receipt**.) You can view all the product receipts that aren't invoiced, and their invoice issue due dates, on the **Product receipts not invoiced** page. (Click **Procurement and sourcing** &gt; **Purchase orders** &gt; **Receiving products** &gt; **Product receipts not invoiced**.)

## Technical information for system administrators
If you don't have access to the pages that are used to complete the tasks that are mentioned in this article, contact your system administrator, and provide the information that is shown in the following table.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Configuration keys</td>
<td>Click <strong>System administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Licensing</strong> &gt; <strong>License configuration</strong>. Click the <strong>General ledger</strong> configuration key.</td>
</tr>
<tr class="even">
<td>Security roles and duties</td>
<td>To perform this task, you must be a member of a security role that includes the following duties:
<ul>
<li><strong>CustInvoiceInvoiceAndCashProcessEnable</strong> (Enable invoice and cash process)</li>
<li><strong>VendInvoiceInvoicePaymentProcessEnable</strong> (Enable invoice and payment process)</li>
</ul></td>
</tr>
<tr class="odd">
<td>Security roles and privileges</td>
<td>To perform this task, you must be a member of a security role that includes the following privileges:
<ul>
<li><strong>CustPackingSlipJournalView</strong> (View sales packing slips)</li>
<li><strong>VendPackingSlipJournalView</strong> (View product receipt journal from purchase order)</li>
<li><strong>LedgerInvoiceIssueDueDateSetupMaintain_W</strong> (Calculate invoice issue due dates)</li>
</ul></td>
</tr>
</tbody>
</table>







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
