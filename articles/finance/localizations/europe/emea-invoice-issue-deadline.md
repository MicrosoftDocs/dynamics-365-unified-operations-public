---
title: Invoice issue deadline
description: Learn how to set up parameters to calculate the due dates for issuing customer invoices and vendor invoices in the European Union (EU).
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Iceland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-02-28
ms.search.form: CustParameters, LedgerInvoiceIssueDueDateSetup_W
---

# Invoice issue deadline

[!include [banner](../../includes/banner.md)]

This article explains how to set up parameters to calculate the due dates for issuing customer invoices and vendor invoices in the European Union (EU).

European Union (EU) Directive 45/2010 and other directives require that shipments within the EU (intra-EU shipments) must be invoiced on or before the fifteenth day of the month after the delivery is made. At the same time, each EU country/region can have different invoicing deadlines for domestic deliveries. By using the invoice issue due date functionality, you can align the date interval to the country/region type. For all shipments to and from a country/region of a particular type, the invoice issue due date is calculated by using rules that you set in the specified date interval. In addition, you can get all packing slips that have a specific invoice issue due date, filter by invoice issue due date during periodic sales invoicing, and control the sales invoice issue date during invoice posting. You can set up a date interval code, and then set up a calculation rule for the invoice issue date by assigning the date interval code to a country/region type. The calculation rule is used to calculate the due date for issuing invoices for the following transactions:

- Intra-EU shipments
- Domestic shipments within an EU member state

You can also set up date controls to help guarantee that customer invoices and credit memos for customer transactions are generated within the specified period after the delivery is made.

## Prerequisites

The following table shows the prerequisites that must be in place before you can use the invoice issue due date functionality .

| Category            | Prerequisite                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Country/region      | The primary address of the legal entity must be in an EU member state.                                                                                                                                                                                                                                                                                                                    |
| Related setup tasks | On the **Date intervals** page, set up a date interval that is used to calculate the invoice issue due date. (Select **General Ledger** > **Ledger setup** > **Date intervals**.) On the **Foreign trade parameters** page, set up foreign trade properties for various countries/regions. (Select **Tax** > **Setup** > **Foreign trade** > **Foreign trade parameters**.) |

## Invoice issue due date calculation rule

Use the **Set up calculation for invoice issue due date** page to set up an invoice issue due date calculation rule by assigning a date interval code to a country/region type.

## Date control parameters for customer invoices and credit notes

Set up date control parameters to help guarantee that customer invoices and credit memos for customer transactions are generated within the specified period after the delivery is made. You can find these parameters in the **Invoice dates control** area of the **Accounts receivable parameters** page.

## Example

To calculate invoice issue due dates for intra-EU shipments on the fifteenth day of the month after the supply is delivered, create a date interval code and calculation rule with the following settings.

### Date interval code

| Field                                                           | Value                           |
|-----------------------------------------------------------------|---------------------------------|
| Date interval code                                              | 15-NM                           |
| Description                                                     | Fifteenth day of the next month |
| Before (In the **To date** field group)                         | Month                           |
| Start/End (In the **To date** field group)                      | End                             |
| +/- (In the **To date** field group)                            | 15                              |
| Days, months, years, or periods (In the **To date** field group) | Days                            |

### Invoice issue due date calculation rule

| Field               | Value                                                     |
|---------------------|-----------------------------------------------------------|
| Country/region type | **EU**                                                    |
| Start date          | Enter the date when the current setup line becomes valid. |
| Date interval code  | **15-NM**                                                 |

## Next steps

After you finish setting up the parameters to calculate invoice issue due dates, you can create and post the following transactions to automatically calculate and update the due dates for issuing invoices:

- **Sales orders** – When you create a sales order and post a packing slip, the system calculates and updates the due date for issuing the invoice on the packing slip. The system calculates the due date based on the date interval that's associated with the country/region that you specify in the delivery address of the sales order. After you post the packing slip, you can verify the invoice issue due date in the **Invoice issue due date** field on the **Packing slip journal** page. (Select **Sales and marketing** > **Sales order** > **Order shipping** > **Packing slip**.) You can view all the packing slips that aren't invoiced, and their invoice issue due dates, on the **Packing slips not invoiced** page. (Select **Sales and marketing** > **Sales order** > **Order shipping** > **Packing slips not invoiced**.)
- **Purchase orders** – When you create a purchase order and post a product receipt, the system calculates and updates the due date for issuing the invoice on the product receipt. The system calculates the due date based on the date interval that's associated with the country/region that you specify in the primary address of the vendor. After you post the product receipt, you can verify the invoice issue due date in the **Invoice issue due date** field on the **Product receipt journal** page. (Select **Procurement and sourcing** > **Purchase orders** > **Receiving products** > **Product receipt**.) You can view all the product receipts that aren't invoiced, and their invoice issue due dates, on the **Product receipts not invoiced** page. (Select **Procurement and sourcing** > **Purchase orders** > **Receiving products** > **Product receipts not invoiced**.)

## Technical information for system administrators

If you don't have access to the pages that you use to complete the tasks mentioned in this article, contact your system administrator, and provide the information shown in the following table.

| Category | Prerequisite |
|---|---|
| Configuration keys | Select **System administration** > **Setup** > **Licensing** > **License configuration**. Select the **General ledger** configuration key. |
| Security roles and duties | To perform this task, you must be a member of a security role that includes the following duties: **CustInvoiceInvoiceAndCashProcessEnable** (Enable invoice and cash process), **VendInvoiceInvoicePaymentProcessEnable** (Enable invoice and payment process) |
| Security roles and privileges | To perform this task, you must be a member of a security role that includes the following privileges: **CustPackingSlipJournalView** (View sales packing slips), **VendPackingSlipJournalView** (View product receipt journal from purchase order), **LedgerInvoiceIssueDueDateSetupMaintain_W** (Calculate invoice issue due dates) |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
