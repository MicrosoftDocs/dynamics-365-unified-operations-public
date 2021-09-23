---
title: References to original invoices in credit notes (vendor invoices)
---

This topic describes the how to create reference to original invoice when
creating a credit note.

# Prerequisites

In the **Feature management** workspace, enable the **Enable credit invoicing
for vendor invoices** feature. For more information, see [Feature management
overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

The functionality that is described in this topic applies to the following
documents:

**Accounts payable**

-   Purchase order

-   Invoice journal,

-   Invoice register

**General ledger**

-   General journal

# How to define references to original invoices

Use the following procedures to define references to original invoices, based on
the document type.

## Vendor credit note (purchase order)

1. Go to Accounts payable \> Purchase orders \> All purchase orders\*\*.

2. Create a new purchase order or use existing one for creation credit note.

3. On the Action Pane, on the \*\*Invoice\*\* tab, in the \*\*Introduce\*\*
group, select \*\*Credit invoicing\*\*.

4. Enter the reason for the correction and the reference to the original
invoice.

## Vendor credit note (ledger journals)

1. Go to Accounts payable \> Invoice journals or Accounts payable \> Invoice
register or General ledger \> Journal entries \> General journals.

2. Create a new journal and new journal lines.

3. On the Action Pane, click the **Functions** button, then click **Credit
invoicing**.

4. Enter the reason for the correction and the reference to the original
invoice.

Note. The **Credit invoicing** function is visible in a general journal (Journal
voucher) if value in **Account type** field is equal to **Vendor**.

 
