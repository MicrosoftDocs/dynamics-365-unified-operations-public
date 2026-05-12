---
title: Vendor invoices overview
description: Learn about vendor invoices, which are requests for payment for products and services, including an outline on submitting invoices.
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 04/01/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Vendor invoices overview

[!include [banner](../includes/banner.md)]

This article provides general information about vendor invoices. Vendor invoices are requests for payment for products and services. Vendor invoices might represent a bill for ongoing services, or they can be based on purchase orders for specific items and services.

## Vendor invoices

A vendor invoice from a purchase order is produced when products or services are received according to a purchase order placed with a vendor. The vendor invoice contains a header, and one or more lines for items or services. A vendor invoice completes the cycle from purchase order to product receipt to vendor invoice.

Although some vendor invoices connect to a purchase order, vendor invoices can also contain lines that don't correspond to purchase order lines. You can also create vendor invoices that aren't associated with any purchase order. These vendor invoices might represent ongoing services, such as a utility bill. You don't have to reference a purchase order when you add an ongoing service.

There are several ways to enter a vendor invoice:

- Use the vendor invoice register to quickly enter invoices that don't reference a purchase order, so that you can accrue the expense. By using the vendor invoice approval journal, you can select those invoices and post them to the vendor balance to reverse the accrual.
- Use the vendor invoice journal to quickly enter invoices that don't reference a purchase order, in a single step.
- Together with the vendor invoice pool, use the vendor invoice register to quickly enter invoices to accrue the expense. You can open the associated purchase orders later to post the invoice against the expense account.
- Use the **Open vendor invoices** and **Pending vendor invoices** pages to create vendor invoices from confirmed purchase orders.
- The **Invoice capture solution** automatically creates vendor invoices from digital invoice images. For more information, see [Invoice capture](invoice-capture-overview.md).

The following discussion provides more information about how to use the **Open vendor invoices** or **Pending vendor invoices** page to create a vendor invoice from a purchase order.

## Understanding invoice line quantities

When you open a vendor invoice from a related purchase order, the system creates invoice lines from the purchase order. By default, the system takes the quantities from the product receipt. However, you can use any of the following default behaviors:

- **Receive now quantity** – Use this option for partial shipments. The default value in the **Quantity** field is set to the quantity specified in the **Receive now** field on the purchase order.
- **Ordered quantity** – Use this option for complete shipments. The default value in the **Quantity** field is set to the quantity specified in the **Ordered** field on the purchase order.
- **Registered quantity** – Use this option if the item requires registration, as specified on the **Item model groups** page. The default value in the **Quantity** field is the physical update quantity that has been registered.
- **Product receipt quantity** – Use this option if a product receipt has already been received for the order. The default value in the **Quantity** field is the total quantity of available product receipts.
- **Registered quantity and services** – Use this option if quantities are registered in arrival journals for stocked items or items that aren't stocked. This option also includes services, regardless of whether they're registered.

If your legal entity uses invoice matching, you can view the results of the quantity matching in the **Product receipt quantity match** column. You can also use the **Matching details** button on the **Review** tab of the Action Pane to view the results of the quantity matching.

## Adding a line that wasn't on the purchase order

You can add a line that wasn't on the purchase order to the vendor invoice. You must select an item number or procurement category. You can then add quantities, prices, and amounts to the line. The line is included only in matching policies for invoice totals.

## Submitting a vendor invoice for review

Your organization might use workflows to manage the review process for vendor invoices. Workflow review can be required for the invoice header, the invoice line, or both. The workflow controls apply to the header or the line, depending on where the focus is when you select the control. Instead of the **Post** button, a **Submit** button sends the vendor invoice through the review process.

### Preventing invoice submission to workflow

To prevent an invoice from being submitted to a workflow, use the following options.

- **Invoice total and the registered total aren't equal.** The user who submitted the invoice receives an alert that the totals aren't equal. This alert gives the user an opportunity to correct the balances before they resubmit the invoice to the workflow system. This feature is available if the **Prohibit submission to workflow when the invoice total and registered invoice total aren't equal** parameter on the **Feature management** page and the **Workflow option when invoice total and registered total aren't equal** parameter on the **Accounts payable parameters** page are turned on.
- **Invoice contains unallocated charges.** The user who submitted the invoice receives an alert that the invoice has unallocated charges. In this way, the user can correct the invoice before they resubmit it to the workflow system. This feature is available if the **Prohibit submission to workflow when there are unallocated charges on a vendor invoice** parameter on the **Feature management** page and the **Workflow option when unallocated charges exist** parameter on the **Accounts payable parameters** page are turned on.
- **Invoice contains the same invoice number as another posted invoice.** The user who submitted the invoice receives an alert that an invoice was found that has a duplicate number. The user can correct the duplicate number before they resubmit the invoice to the workflow system. The alert is shown if the **Check the invoice number used** parameter in Accounts payable is set to **Reject duplicate**. This feature is available if the **Prohibit submission to workflow when the invoice number already exists on a posted invoice, and your system isn't set up to accept duplicate invoice numbers** parameter on the **Feature management** page is turned on.
- **Invoice contains a line where the invoice quantity is less than the matched product receipt quantity.** The user who submits the invoice or tries to post it receives a message that the quantities aren't equal. This message gives the user an opportunity to correct the values before they resubmit the invoice to the workflow system. This feature is available if the **Block posting and submission of vendor invoices to workflow** parameter on the **Feature management** page and the **Block posting and submission to workflow** parameter on the **Accounts payable parameters** page are turned on.

## Matching vendor invoices to product receipts

You can enter and save information for vendor invoices, and you can match invoice lines to product receipt lines. You can also match partial quantities for a line.

Create a vendor invoice based on the product receipt line items that you received through the current date, even if you didn't receive all the items for a particular purchase order. For example, use this option if a vendor sends one invoice per month to cover all the deliveries that it shipped during that month. Each product receipt represents a partial or complete delivery of the items on the purchase order.

When an invoice is in workflow, the approver can update invoice quantities so that they match the value in the **Product-receipt-quantity-to-match** field. To do so, select the **Update the invoice quantities to match product receipt quantities in workflow** feature in the **Feature management** workspace and select **Enable**. If an approver in the workflow process removes all the matches from all the product receipts from the invoice line, the invoice line is deleted. When this feature isn't enabled, invoice quantities aren't updated for invoices in workflow.

When you post the invoice, the **Invoice remainder** quantity for each item is updated with the total of the received quantities from the selected product receipts. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the purchase order are 0, the status of the purchase order changes to **Invoiced**. If the **Invoice remainder** quantity isn't 0, the status of the purchase order remains unchanged, and you can enter additional invoices for it.

This option assumes that you posted at least one product receipt for the purchase order. The vendor invoice is based on these product receipts and reflects the quantities from them. The financial information for the invoice is based on the information that you enter when you post the invoice.

For more information, see [Record vendor invoice and match against received quantity](../accounts-payable/tasks/record-vendor-invoice-match-against-received-quantity.md).

## Configure an automated task for vendor invoice workflow to post the vendor invoice using a batch job

Add an automated posting task to the Vendor invoice workflow so that invoices are processed in a batch. Posting invoices in a batch lets the workflow process continue without having to wait for the posting to finish, which improves the overall performance of all the tasks submitted to the workflow.

To post a vendor invoice in a batch, on the **Feature management** page, turn on the **Vendor invoice batch posting** parameter. Configure vendor invoice workflows by going to **Accounts payable > Setup > Accounts payable workflows**.

You can see the **Post the vendor invoice using a batch** task in the workflow editor, regardless of whether the feature parameter, **Vendor invoice batch posting**, is enabled. When the feature parameter isn't enabled, an invoice that contains the **Post the vendor invoice using a batch task** isn't processed in workflow until the parameter is enabled. The **Post the vendor invoice using a batch** task must not be used in the same workflow as the **Post vendor invoices** automated task. Also, the **Post the vendor invoice using a batch** task should be the last element in the workflow configuration.

You can specify the number of invoices to include in the batch, and the number of hours to wait before rescheduling a batch, by going to **Accounts payable > Setup > Accounts payable parameters > Invoice > Invoice workflow**.

## Working with multiple invoices

You can work with multiple invoices at the same time and post all of them at the same time. If you need to create multiple invoices, use the **Pending vendor invoices** page. If you must post and print multiple vendor invoices, use the **Invoice approval journal**. If you're using the **Invoice approval journal**, you must post at least one product receipt for the purchase order, and you must post an invoice for the purchase order in an invoice register. The financial information for the invoice comes from the invoice that you posted in the register.

## Recovering vendor invoices that are in use

While a user is using a vendor invoice, other users can't edit it. However, the state of an invoice might sometimes indicate that the invoice is in use, even though no user is actively editing it. For example, the application might have stopped responding while the invoice was being edited, or a user might have inadvertently left the invoice open in the application.

You can use the **Recover vendor invoices** page to recover or release vendor invoices that have been in use for more than four hours, so that they can be edited. You can open this page from the **Periodic task** navigation or a tile on the **Vendor invoice entry** workspace. After an invoice is recovered, it will be available for editing on the **Vendor invoice** page.

You can access the **Recover vendor invoices** page only if you're assigned the **Recover vendor invoices in use** security duty and privilege. Additionally, the **Allow vendor invoice recovery** parameter on the **Accounts payable parameters** page must be turned on.

## Default financial dimension in vendor invoice lines

For vendor invoices that are associated with a purchase order, the default financial dimension comes from the corresponding purchase order lines.

For vendor invoices that aren't associated with any purchase order, the default financial dimension merges the dimensions from the dimension link, invoice header, and item. If the same dimension is defined on the dimension link, invoice header, and item, the dimension on the invoice line follows this priority sequence:
dimension link > invoice header > item

## Resetting the workflow status for vendor invoices from Unrecoverable to Draft

A workflow instance that stops because of an unrecoverable error has a workflow status of **Unrecoverable**. When the status of a vendor invoice workflow is **Unrecoverable**, you can reset it to **Draft** by selecting **Recall**. You can then edit the vendor invoice. This feature is available if the **Resetting the workflow status for vendor invoices from Unrecoverable to Draft** parameter on the **Feature management** page is turned on.

Use the **Workflow history** page to reset the workflow status to **Draft**. You can open this page from **Vendor invoice** or from the **Common > Inquires > Workflow** navigation. To reset the workflow status to **Draft**, select **Recall**. You can also reset the workflow status to **Draft** by selecting the **Recall** action on the **Vendor invoice** or **Pending vendor invoices** page. After you reset the workflow status to **Draft**, you can edit the vendor invoice on the **Vendor invoice** page.

## Viewing the invoice total on the Pending vendor invoices page

You can view the invoice total on the **Pending vendor invoices** page by enabling the **Display invoice total on pending vendor invoices list** parameter on the **Accounts payable parameters** page.

## Vendor open transactions report

The **Vendor open transactions** report provides detailed information about the open transactions for each vendor as of the date that you specify. Use this report during the audit procedure to verify balances between vendor book transactions and ledger account transactions.

For each transaction, the report includes the following details:

- Invoice number
- Transaction date
- Voucher number
- Transaction amount in the transaction currency and accounting currency
- Credit balance in the transaction currency and accounting currency
- Debit balance in the transaction currency and accounting currency
- Subtotal amount in the accounting currency
- Payment due date

### Filter the data on the report

When you generate the **Vendor open transactions** report, the following default parameters are available. You can use them to filter the data that will be included on the report.

- **Exclude future settlement** – Select this checkbox to exclude transactions that are settled after the date that you enter in the **Open transactions per** field.
- **Open transactions per** – Enter a date to include transactions that are open as of that date. If you don't enter a date, this field is set to the maximum date. (The maximum date is the latest date that the system accepts, December 31, 2154.) By default, the next time that you run the report, this field is set to the last date that you entered in it.

Use the filters under the **Record to include** field to further limit the transaction data that the report includes.

### Extend invoice number length

Starting in Dynamics 365 Finance version 10.0.40, you can enable the **Extend the length of invoice number for vendor invoice** feature to increase the invoice number from 20 characters to 50 characters in the vendor invoice and invoice journal. Before enabling the feature, create a ticket in Lifecycle services to open the **EnableEdtStringDatabaseStringLengthAttributeInComputation** flight.

## Additional resources

- [Set up vendor invoice policies](../accounts-receivable/tasks/set-up-vendor-invoice-policies.md)
- [Key invoice data in AP system using vendor invoice](tasks/key-invoice-data-ap-system-vendor-invoice.md)
- [Key invoice data into accounts payable using an approval journal](tasks/key-invoice-data-into-ap-system-approval-journal.md)
- [Key invoice data into the AP system using invoice pool](tasks/key-invoice-data-into-ap-system-invoice-pool.md)
- [Record a vendor invoice in the invoice journal](tasks/record-vendor-invoice-invoice-journal.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
