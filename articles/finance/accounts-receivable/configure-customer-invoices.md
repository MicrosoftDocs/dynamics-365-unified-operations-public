---
title: Create a customer invoice
description: A customer invoice for a sales order is a bill that is related to a sale, and that an organization gives to a customer.
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustFreeInvoice
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 00b4b40c-1576-4098-9aed-ac376fdeb8c5
---

# Create a customer invoice

[!include [banner](../includes/banner.md)]

A **Customer invoice for a sales order** is a bill that relates to a sale, and that an organization gives to a customer. Create this type of customer invoice based on a sales order, which includes order lines and item numbers. You specify and post item numbers in the ledger. Subledger journal entries aren't available for a customer invoice for a sales order. For more information, see [Create sales order invoices](tasks/create-sales-order-invoices.md).

A **Free text invoice** isn't related to a sales order. It contains order lines that include ledger accounts, free-text descriptions, and a sales amount that you enter. You can't enter an item number on this kind of invoice. You must enter the appropriate sales tax information. Each invoice line indicates a main account for the sale, which you can distribute to multiple ledger accounts by selecting **Distribute amounts** on the **Free text invoice** page. Additionally, the posting profile that you use for the free text invoice posts the customer balance to the summary account.

For more information, see:

- [Create free text invoices](../accounts-receivable/create-free-text-invoice-new.md)
- [Create a free text invoice template](../accounts-receivable/create-free-text-invoice-template-new.md)
- [Assign free text invoice template to a customer](tasks/assign-free-text-invoice-template-customer.md)
- [Generate and post recurring free text invoices](tasks/post-recurring-free-text-invoices.md)

A **Pro forma invoice** is an invoice that you prepare as an estimate of the actual invoice amounts before you post the invoice. You can print a **Pro forma invoice** either for a customer invoice for a sales order or for a free text invoice.

>[!NOTE]
> In the case of a system interruption during the sales pro forma invoice process, a pro forma invoice can be orphaned. You can delete an orphaned pro forma invoice by running the **Delete pro forma invoices manually** periodic job. Go to **Sales and marketing > Periodic tasks > Clean up > Delete pro forma invoices manually**.

## Using sales order customer invoice data entities

Use data entities to import and export information about a customer invoice for a sales order. Different entities exist for the information on the sales invoice header and the sales invoice lines.

The following entities are available for the information on the sales invoice header:

- **Sales invoice journal header** entity (SalesInvoiceJournalHeaderEntity)
- **Sales invoice headers V2** entity (SalesInvoiceHeaderV2Entity)

Use the **Sales invoice journal header** entity for a more performant experience for sales header import and export. This entity doesn't contain the **Sales tax amount** (INVOICEHEADERTAXAMOUNT) column, which represents the sales tax value on the sales invoice header. If your business scenario requires that information, use the **Sales invoice headers V2** entity to import and export the sales invoice header information.

The following entities are available for the information on sales invoice lines:

- **Customer invoice lines** entity (BusinessDocumentSalesInvoiceLineItemEntity)
- **Sales invoice lines V3** entity (SalesInvoiceLineV3Entity)

When you're determining which line entity to use for exports, consider whether a full push or an incremental push will be used. Additionally, consider the data composition. The **Sales invoice lines V3** entity supports more complex scenarios, such as mapping to the inventory fields. It also supports full-push export scenarios. For incremental pushes, use the **Customer invoice lines** entity. This entity contains a much simpler data composition than the **Sales invoice lines V3** entity and is preferred, especially if inventory field integration isn't required. Because of differences in the mapping support between the line entities, the **Customer invoice lines** entity typically has faster performance than the **Sales invoice lines V3** entity.

## Post and print individual customer invoices that are based on sales orders

Use this process to create an invoice that is based on a sales order. You might do this if you decide to invoice the customer before you deliver the goods or services.

When you post an invoice, the **Invoice remainder** quantity for each item updates with the total of the invoiced quantities from the selected sales order. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the sales order are 0, the status of the sales order changes to **Invoiced**. If the **Invoice remainder** quantity isn't 0, the status of the sales order remains unchanged, and you can enter additional invoices for it.

You can view the status of the sales orders on the **All sales orders** list page. Use the **Open customer invoices** list page to view the invoices that you posted.

## Post and print individual customer invoices that are based on packing slips and the date

Use this process when one or more packing slips are posted for the sales order. The customer invoice is based on these packing slips and reflects the quantities from them. The financial information for the invoice comes from the information that you enter when you post the invoice.

You can create a customer invoice that is based on the packing slip line items that are shipped to date, even if all the items for a particular sales order aren't shipped. You might do this if, for example, your legal entity issues one invoice per customer per month that covers all the deliveries that you ship during that month. Each packing slip represents a partial or complete delivery of the items on the sales order.

When you post the invoice, the **Invoice remainder** quantity for each item is updated with the total of the delivered quantities from the selected packing slips. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the sales order are 0, the status of the sales order changes to **Invoiced**. If the **Invoice remainder** quantity isn't 0, the status of the sales order remains unchanged, and you can enter additional invoices for it.

Inventory transactions are updated with the invoice number, and the status in the **Line status** field on the sales order changes to **Invoiced**.

View the status of the sales orders on the **All sales orders** list page.

## Consolidate sales orders or packing slips for posting

Use this process when one or more sales orders are ready to be invoiced, and you want to consolidate them into a single invoice.

You can select multiple invoices on the **Sales order** list page and then use **Generate invoices** to consolidate them. On the **Posting invoice** page, you can change the **Summary order** setting to summarize by order number (where there are multiple packing slips for a single sales order) or by invoice account (where there are multiple sales orders for a single invoice account). Use the **Arrange** button to consolidate sales orders into single invoices, based on the **Summary order** settings.

## Split sales order invoices by site and delivery information

You can configure the splitting of sales order customer invoices by site or by delivery address on the **Summary update** tab of the **Accounts receivable parameters** page.

- Select the **Split based on invoice site** option to create one invoice per site when posting.
- Select the **Split based on invoice delivery information** option to create one invoice per sales order line delivery address when posting.

## Post to revenue account for sales order lines that have no price and no cost

You can update the **Revenue** account in the **General ledger** for sales order lines that have no price and no cost.

To set up or view this information:

1. Go to the **Post to Revenue account for zero priced and zero cost sales order invoice lines** parameter on the **Ledger and sales tax** tab of the **Accounts receivable parameters** page. (**Accounts receivable > Setup > Accounts receivable parameters**).
1. Select **Yes** to update the **Revenue** account for sales order invoice lines that have no price and no cost.

- If you select this option, the voucher contains 0.00 entries for the **Customer balance** and **Revenue** posting types. You define a revenue account on the **Inventory posting** parameter page, on the **Sales order** account definition tab.
- If you don't select this option, lines that don't have price or cost information aren't posted to the **Revenue** account. Instead, the voucher contains a 0.00 entry for the **Customer balance** posting type.

## Line creation sequence number information

When you post customer invoice lines, you can create sequential line creation sequence numbers. The system assigns line creation sequence numbers during the posting process. By allowing non-sequential numbering, you can help improve the performance of customer invoice posting. Third-party integrations that expect sequential ordering can use line creation sequence numbers. Consult your IT department about any extensions that might integrate with line creation sequence numbers.

To set up or view this information, on the **Accounts receivable parameters** page, on the **Updates** tab, set the **Assign sequential line numbers when posting customer invoice lines** option:

- Set the option to **No** to use non-sequential numbering for line creation sequence numbers.
- Set the option to **Yes** to use sequential numbering. You must set the option to **Yes** for legal entities that have a primary address in Italy. You must also set it to **Yes** if the **CustInvoiceTransRandLineCreationSeqNumFlight** flight is disabled.

## Additional settings that change the posting behavior

The following fields change the behavior of the posting process.

| Field | Description |
|---|---|
| Quantity | Select the quantities to base the posting of the document on. The options that are available vary, depending on the type of document that you're posting, such as a packing slip or an invoice.<br><br>- **Deliver now** – Select all quantities that you enter in the **Deliver now** field. Use this option to confirm or deliver a partial order.<br>- **Picked** – Select all quantities that you pick.<br>- **All** – Select all quantities on the sales order that aren't yet updated by the current document type.<br>- **Packing slip** – Select all quantities that a packing slip updates.<br>- **Picked quantity and not stocked products** – Select all quantities that you pick and all product quantities that aren't stocked. |
| Posting | - Select this option to journalize the sales order.<br>- Clear this option to print a pro forma sales order. **Note:** If you made an agreement for a payment schedule, the payment schedule isn't shown on the pro forma sales order. Payment schedules are shown only on actual sales orders. |
| Late selection | Select this option to apply the selected query later. This option is used for batch jobs. The query runs when the batch job runs. |
| Reduce quantity | Select this option to automatically reduce the delivered quantity when the document is posted, so that the delivered quantity equals the available inventory. |
| Print | Select when to print documents:<br><br>- **Current** – Print documents after each invoice is updated.<br>- **After** – Print documents after all the invoices are updated.<br><br>**Note:** The **Print** field is available only if you select the **Print invoice**, **Print confirmation**, **Print picking list**, or **Print packing slip** option. For example, on the **Form sorting** page, you set up the system to sort the information by invoice account. You can then select **After** to print the documents in a batch that is sorted by invoice account. Otherwise, the documents are printed before processing is completed, and the documents aren't sorted in the order that is specified on the **Form sorting** page. |
| Print invoice | Select this option to print the invoice. If you turn off this option, you can post an invoice without printing it. |
| Send e-mail | Select this option to send the invoice for a sales order to the customer as an email attachment after the invoice is posted. Attachments are sent as PDF and XML files. This option is available only if you select the **Enable CFD (electronic invoices)** option on the **Electronic invoice parameters** page. **Note:** (MEX) This control is available only to legal entities whose primary address is in Mexico. |
| Use print management destination | Select this option to use the print settings that you specify for the transaction, document, or module on the **Print management setup** page. |
| Check credit limit | Select the information that the system should analyze when it performs a credit limit check.<br><br>- **None** – There's no requirement for the credit limit check.<br>- **Balance** – The system checks the credit limit against the customer balance.<br>- **Balance + packing slip or product receipt** – The system checks the credit limit against the customer balance and deliveries.<br>- **Balance+All** – The system checks the credit limit against the customer balance, deliveries, and open orders. |
| Credit correction | Select this option to display the credit note as a debit in the voucher transactions. |
| Credit remaining quantity | If you're posting a credit note, select this option to keep the remaining quantity on order. If you clear this option, the remaining quantity is set to 0 (zero). |
| Summary update for | Select how multiple sales orders should be summarized:<br><br>- **None** – Don't summarize sales orders. For example, a separate invoice is created for each sales order.<br>- **Invoice account** – Summarize all selected orders, based on the criteria that you set up on the **Summary update parameters** page.<br>- **Order** – Summarize a selected range of orders into one order that you specify. The system summarizes the orders based on the criteria that you set up on the **Summary update parameters** page. If you select this option, you must select a value in the **Sales order** field.<br>- **Automatic summary** – If you specify summary updates on the **Summary update** page, the system summarizes all selected orders, based on the criteria that you set up on the **Summary update parameters** page. If you don't specify summary updates, the order is posted separately.<br>- **Packing slip** – Summarize a selected range of orders into one invoice for each packing slip. This option is available only if **Packing slip** is selected in the **Quantity** field. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
