---
# required metadata

title: Vendor invoices overview
description: This article provides general information about vendor invoices.
author: abruer
ms.date: 02/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Vendor invoices overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


This article provides general information about vendor invoices. Vendor invoices are requests for payment for products and services. Vendor invoices might represent a bill for ongoing services, or they can be based on purchase orders for specific items and services.

## Vendor invoices

A vendor invoice from a purchase order is produced when products or services are received according to a purchase order placed with a vendor. The vendor invoice contains a header, and one or more lines for items or services. A vendor invoice completes the cycle from purchase order to product receipt to vendor invoice.

Although some vendor invoices connect to a purchase order, vendor invoices can also contain lines that don't correspond to purchase order lines. You can also create vendor invoices that aren't associated with any purchase order. These vendor invoices might represent ongoing services, such as a utility bill. You don't have to reference a purchase order when you add an ongoing service.

There are several ways to enter a vendor invoice:

- The vendor invoice register lets you quickly enter invoices that don't reference a purchase order, so that you can accrue the expense. By using the vendor invoice approval journal, you can select those invoices and post them to the vendor balance to reverse the accrual.
- The vendor invoice journal lets you quickly enter invoices that don't reference a purchase order, in a single step.
- Together with the vendor invoice pool, the vendor invoice register lets you quickly enter invoices to accrue the expense. You can open the associated purchase orders later to post the invoice against the expense account.
- The **Open vendor invoices** and **Pending vendor invoices** pages let you create vendor invoices from confirmed purchase orders.

The following discussion provides more information about how to use the **Open vendor invoices** or **Pending vendor invoices** page to create a vendor invoice from a purchase order.

## Understanding invoice line quantities

When you open a vendor invoice from a related purchase order, the system creates invoice lines from the purchase order. By default, the system takes the quantities from the product receipt. However, you can use any of the following default behaviors:

- **Receive now quantity** – Use this option for partial shipments. The default value in the **Quantity** field will be set to the quantity specified in the **Receive now** field on the purchase order.
- **Ordered quantity** – Use this option for complete shipments. The default value in the **Quantity** field will be set to the quantity specified in the **Ordered** field on the purchase order.
- **Registered quantity** – Use this option if the item requires registration, as specified on the **Item model groups** page. The default value in the **Quantity** field is the physical update quantity that has been registered.
- **Product receipt quantity** – Use this option if a product receipt has already been received for the order. The default value in the **Quantity** field is the total quantity of available product receipts.
- **Registered quantity and services** – Use this option if quantities have been registered in arrival journals for stocked items or items that aren't stocked. This option also includes services, regardless of whether they are registered.

If your legal entity uses invoice matching, you can view the results of the quantity matching in the **Product receipt quantity match** column. You can also use the **Matching details** button on the **Review** tab of the Action Pane to view the results of the quantity matching.

## Adding a line that wasn't on the purchase order

You can add a line that wasn't on the purchase order to the vendor invoice. You must select an item number or procurement category. You can then add quantities, prices, and amounts to the line. The line will be included only in matching policies for invoice totals.

## Submitting a vendor invoice for review

Your organization might use workflows to manage the review process for vendor invoices. Workflow review can be required for the invoice header, the invoice line, or both. The workflow controls apply to the header or the line, depending on where the focus is when you select the control. Instead of the **Post** button, a **Submit** button sends the vendor invoice through the review process.

### Preventing invoice from being submitted to workflow 

Following are several ways you can prevent an invoice from being submitted to a workflow.

- **Invoice total and the registered total are not equal.** The user who submitted the invoice will receive an alert that the totals aren't equal. This alert gives the user an opportunity to correct the balances before they resubmit the invoice to the workflow system. This feature is available if the **Prohibit submission to workflow when the invoice total and registered invoice total are not equal** parameter on the **Feature management** page and the **Workflow option when invoice total and registered total do not equal** parameter on the **Accounts payable parameters** page are turned on. 
- **Invoice contains unallocated charges.** The user who submitted the invoice will receive an alert that the invoice has unallocated charges. In this way, the user can correct the invoice before they resubmit it to the workflow system. This feature is available if the **Prohibit submission to workflow when there are unallocated charges on a vendor invoice** parameter on the **Feature management** page and the **Workflow option when unallocated charges exist** parameter on the **Accounts payable parameters** page are turned on.
- **Invoice contains the same invoice number as another posted invoice.** The user who submitted the invoice will receive an alert that an invoice was found that has a duplicate number. The user can correct the duplicate number before they resubmit the invoice to the workflow system. The alert will be shown if the **Check the invoice number used** parameter in Accounts payable is set to **Reject duplicate**. This feature is available if the **Prohibit submission to workflow when the invoice number already exists on a posted invoice, and your system is not set up to accept duplicate invoice numbers** parameter on the **Feature management** page is turned on.
- **Invoice contains a line where the invoice quantity is less than the matched product receipt quantity.** The user who submits the invoice or tries to post it will receive a message that the quantities aren't equal. This message gives the user an opportunity to correct the values before they resubmit the invoice to the workflow system. This feature is available if the **Block posting and submission of vendor invoices to workflow** parameter on the **Feature management** page and the **Block posting and submission to workflow** parameter on the **Accounts payable parameters** page are turned on.

## Matching vendor invoices to product receipts

You can enter and save information for vendor invoices, and you can match invoice lines to product receipt lines. You can also match partial quantities for a line.

You can create a vendor invoice that is based on the product receipt line items that have been received through the current date, even if all the items for a particular purchase order haven't yet been received. For example, you might use this option if a vendor sends one invoice per month to cover all the deliveries that it shipped during that month. Each product receipt represents a partial or complete delivery of the items on the purchase order.

When an invoice is in workflow, the approver can update invoice quantities so that they match the value in the **Product-receipt-quantity-to-match** field. To do so, select the **Update the invoice quantities to match product receipt quantities in workflow** feature in the **Feature management** workspace and select **Enable**. If an approver in the workflow process has removed all the matches from all the product receipts from the invoice line, the invoice line will be deleted. When this feature isn't enabled, invoice quantities are not updated for invoices in workflow.

When you post the invoice, the **Invoice remainder** quantity for each item is updated with the total of the received quantities from the selected product receipts. If both the **Invoice remainder** quantity and the **Deliver remainder** quantity for all items on the purchase order are 0 (zero), the status of the purchase order is changed to **Invoiced**. If the **Invoice remainder** quantity isn't 0, the status of the purchase order remains unchanged, and additional invoices can be entered for it.

This option assumes that at least one product receipt has been posted for the purchase order. The vendor invoice is based on these product receipts and reflects the quantities from them. The financial information for the invoice is based on the information that is entered when you post the invoice.

For more information, see [Record vendor invoice and match against received quantity](../accounts-payable/tasks/record-vendor-invoice-match-against-received-quantity.md).

## Configure an automated task for vendor invoice workflow to post the vendor invoice using a batch job

You can add an automated posting task to the Vendor invoice workflow so that invoices are processed in a batch. Posting invoices in a batch lets the workflow process continue without having to wait for the posting to finish, which improves the overall performance of all the tasks submitted to the workflow.

To post a vendor invoice in a batch, on the **Feature management** page, turn on the **Vendor invoice batch posting** parameter. Vendor invoice workflows are configured by going to **Accounts payable > Setup > Accounts payable workflows**.

You can see the **Post the vendor invoice using a batch** task in the workflow editor, regardless of whether the feature parameter, **Vendor invoice batch posting**, is enabled. When the feature parameter is not enabled, an invoice that contains the **Post the vendor invoice using a batch task** won't process in workflow until the parameter is enabled. The **Post the vendor invoice using a batch** task must not be used in the same workflow as the **Post vendor invoices** automated task. Also, the **Post the vendor invoice using a batch** task should be the last element in the workflow configuration.

You can specify the number of invoices to include in the batch, and the number of hours to wait before rescheduling a batch, by going to **Accounts payable > Setup > Accounts payable parameters > Invoice > Invoice workflow**. 

## Working with multiple invoices

You can work with multiple invoices at the same time and post all of them at the same time. If you need to create multiple invoices, use the **Pending vendor invoices** page. If you must post and print multiple vendor invoices, use the **Invoice approval journal**. If you're using the **Invoice approval journal**, at least one product receipt must be posted for the purchase order, and an invoice for the purchase order must be posted in an invoice register. The financial information for the invoice comes from the invoice that was posted in the register.

## Recovering vendor invoices that are being used

While a vendor invoice is being used, it can't be edited by another user. However, the state of an invoice might sometimes indicate that the invoice is being used, even though it isn't being actively edited. For example, the application might have stopped responding while the invoice was being edited, or a user might have inadvertently left the invoice open in the application.

You can use the **Recover vendor invoices** page to recover or release vendor invoices that have been in use for more than four hours, so that they can be edited. You can open this page from the **Periodic task** navigation or a tile on the **Vendor invoice entry** workspace. After an invoice is recovered, it will be available for editing on the **Vendor invoice** page.

You can access the **Recover vendor invoices** page only if the **Recover vendor invoices in use** security duty and privilege are assigned to you. Additionally, the **Allow vendor invoice recovery** parameter on the **Accounts payable parameters** page must be turned on.

## Default financial dimension in vendor invoice lines
For vendor invoices which are associated with purchase order, the default financial dimension will be derived from corresponding purchase order lines. 

For vendor invoices which are not associated with any purchase order, the default financial dimension will merge the dimension from dimension link, invoice header, item.  If the same dimension defined on dimension link, invoice header and item， the dimension on the invoice line will follow the priority sequence: 
dimension link > invoice header > Item

## Resetting the workflow status for vendor invoices from Unrecoverable to Draft

A workflow instance that has stopped because of an unrecoverable error will have a workflow status of **Unrecoverable**. When the status of a vendor invoice workflow is **Unrecoverable**, you can reset it to **Draft** by selecting **Recall**. You can then edit the vendor invoice. This feature is available if the **Resetting the workflow status for vendor invoices from Unrecoverable to Draft** parameter on the **Feature management** page is turned on.

You can use the **Workflow history** page to reset the workflow status to **Draft**. You can open this page from **Vendor invoice** or from the **Common > Inquires > Workflow** navigation. To reset the workflow status to **Draft**, select **Recall**. You can also reset the workflow status to Draft by selecting the **Recall** action on the **Vendor invoice** or **Pending vendor invoices** page. After the workflow status is reset to **Draft**, it becomes available for editing on the **Vendor invoice** page.

## Viewing the invoice total on the Pending vendor invoices page

You can view the invoice total on the **Pending vendor invoices** page by enabling the **Display invoice total on pending vendor invoices list** parameter on the **Accounts payable parameters** page. 

## Vendor open transactions report

The **Vendor open transactions** report provides detailed information about the open transactions for each vendor as of the date that you specify. This report is often used during the audit procedure for verifying balances between vendor book transactions and ledger account transactions.

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

- **Exclude future settlement** – Select this checkbox to exclude transactions that are settled after the date that is entered in the **Open transactions per** field.
- **Open transactions per** – Enter a date to include transactions that are open as of that date. If you don't enter a date, this field is set to the maximum date. (The maximum date is the latest date that the system will accept, December 31, 2154.) By default, the next time that the report is run, this field will be set to the last date that was entered in it.

You can use the filters under the **Record to include** field to further limit the transaction data that is included on the report.

## Additional resources

- [Set up vendor invoice policies](../accounts-receivable/tasks/set-up-vendor-invoice-policies.md)
- [Key invoice data in AP system using vendor invoice](tasks/key-invoice-data-ap-system-vendor-invoice.md)
- [Key invoice data into accounts payable using an approval journal](tasks/key-invoice-data-into-ap-system-approval-journal.md)
- [Key invoice data into the AP system using invoice pool](tasks/key-invoice-data-into-ap-system-invoice-pool.md)
- [Record a vendor invoice in the invoice journal](tasks/record-vendor-invoice-invoice-journal.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
