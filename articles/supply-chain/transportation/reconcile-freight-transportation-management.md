---
title: Reconcile freight in transportation management
description: Learn about the freight reconciliation process, including outlines on manual reconciliation and automatic reconciliation.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSAuditMaster, TMSFreightBillInvoiceReconcile, TMSFreightBillSummary, TMSFreightBillType, TMSFreightMatchReason, TMSFBDetailReconcile, TMSInvoiceTable,TMSInvoiceLineReconcile,TMSReconcileInvoice, TMSFreightBillDetail, TMSFreightBillTypeAssignment, TMSRejectInvoiceLine, TMSMiscellaneousCharge, TMSCarrierCodeLookup, DefaultDashboard, WHSLoadPlanningWorkbench, TMSInvoiceJournal, LedgerJournalTable, LedgerJournalTransDaily, WHSInboundLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Reconcile freight in transportation management

[!include [banner](../includes/banner.md)]

This article describes the freight reconciliation process, which is also known as the matching process. During this process, system-generated freight bills that contain estimated freight costs are matched to actual invoices that are received from carriers. Any differences (variances) are reconciled.

Freight reconciliation can be done manually. Alternatively, to help save time and reduce manual errors, it can be set up to occur automatically.

## The freight reconciliation process

Freight rates are calculated by the rate engine that is associated with the relevant shipping carrier. When a load is confirmed, a freight bill is generated, and the freight rates are transferred to it. The freight rates are apportioned as miscellaneous charges to the relevant source document (purchase order, sales order, or transfer order), depending on the setup that is used for the regular billing process.

The freight reconciliation process can start as soon as the freight invoice arrives from the shipping carrier. The invoice can be received either electronically or on paper. If it's received on paper, generate an electronic invoice by using the freight bill as a template.

Freight bills and invoices must then be matched. In other words, the freight bills that correspond to each freight invoice must be found. You can match the invoice lines one by one (manual matching), or you can match all available invoices at once (auto matching). To handle any variances that occur between the freight bill and the invoice, use the reconciliation reason codes that are set up for both manual and automatic reconciliation.

:::image type="content" source="media/freight-reconcilation-process.jpg" alt-text="Diagram that illustrates the freight reconciliation process." lightbox="media/freight-reconcilation-process.jpg":::

## Enable freight reconciliation

To use Transportation management (TMS) to reconcile freight, follow these steps.

1. Go to **Transportation management** \> **Setup** \> **Transportation management parameters**.
1. On the **General** tab, on the **Freight reconciliation** FastTab, set the **Enable freight reconciliation** option to *Yes*.

## Set up reconciliation reasons

Reconciliation reasons (or reason codes) specify accounts that are debited and credited with any variances that occur between the freight bills and invoices as a result of manual or automatic reconciliation. They're set up on the **Reconciliation reasons** page (**Transportation management** \> **Setup** \> **Reconciliation reasons**).

For some reason codes, you might not want to credit a specific account. Instead, you want any credit to be paid to the vendor. In this case, select the **Pay freight vendor** checkbox. Be sure that you also specify a vendor account for the carrier on the **Shipping carriers** page (**Transportation management** \> **Carriers** \> **Shipping carriers**).

When the ship confirm action occurs, the freight bill is generated, and freight charges are apportioned back to the original source document as miscellaneous charges. Alternatively, you might want to charge the debit and credit accounts that are specified on the **Reconciliation reasons** page. In this case, select the **Override accounts** checkbox.

If you're reconciling freight manually, match each invoice line with the freight bill line or lines for the load that is being invoiced. Do this matching on the **Freight bill and invoice matching** page.

If the amount on the invoice line doesn't match the freight bill amount, select a reconciliation reason for the difference. If multiple reconciliations reasons apply, split the unmatched amount across them. Reconciliation reasons determine how the difference amounts are posted in the general ledger.

After the reconciliation of the whole invoice amount is accounted for, it's submitted for approval. Then the journal is posted.

The following illustration shows how to generate a freight invoice and do freight reconciliation.

:::image type="content" source="media/processflowforfreightreconciliation.jpg" alt-text="Diagram that shows the freight reconciliation tasks." lightbox="media/processflowforfreightreconciliation.jpg":::

## Reconcile freight manually

### Select a load to reconcile

1. Go to one of the following pages, depending on whether you're reconciling an inbound load or an outbound load:

    - **Transportation management** \> **Planning** \> **Inbound load planning workbench**.
    - **Transportation management** \> **Planning** \> **Outbound load planning workbench**.

1. Clear the **Hide shipped and received** checkbox.
1. In the **Load** grid, select the load that you want to reconcile.

### Create a carrier invoice

If you reconcile freight manually and don't automatically receive carrier invoices, you can create an invoice based on the freight bill.

1. Select **Related information**.
1. Select **Freight bill details**.
1. Select **Generate freight bill invoice**.
1. In the **Invoice** field, enter a value.
1. Select **OK**.

### Reconcile the invoice

When you reconcile a carrier invoice and a freight bill, the reconciliation is done line by line.

1. Select **Match freight bills and invoices**.
1. In the **Invoice details** section, expand the **Unmatched freight bill details** section.
1. In the list, mark the selected row.
1. Select **Match**.
1. Expand the **Matched freight bill details** section.

All freight bills that have positive amounts are available for matching. As in auto matching, you can only match freight invoices that have negative amounts to freight bills that aren't fully matched.

### Submit the invoice for approval

1. Select **Submit for approval**.
1. Close the page.
1. Clear the **Hide approved** checkbox.
1. Select **Vendor invoice journals**.
1. In the **Reference journal number** field, select the link.
1. Select **Lines**.

## Automatic reconciliation

If you choose to run automatic reconciliation, you must handle any invoices that the system can't match. You must then process those invoices manually before you can post all the invoices for payment.

To use automatic reconciliation, you must specify the schedule for reconciliation. You must also specify the invoices and shipping carriers to use. The automatic matching of the invoice lines and freight bills is done according to the setup of the audit master and freight bill type.

### Set up vendor invoice parameters

To enable automatic creation and/or posting of a vendor invoice journal during the automatic reconciliation process, go to **Transportation management** \> **Setup** \> **Transportation management parameters** \> **Vendor invoice**. To enable the system to create an invoice journal to reconcile any differences between the freight bill and freight invoice, turn on the **Write vendor invoice journal** parameter. To enable the system to post the invoice journal after it's approved by the user who is defined in the **Workflow user** field, turn on the **Post journal** parameter.

To run the automated match and pay batch jobs, turn on the **Automatically match and pay the freight invoice** parameter. If the **Automatically match and pay the freight invoice** parameter is turned off, but the **Enable Freight Reconciliation** parameter is turned on, you can run the manual match and pay process, and still submit vendor invoices for approval.

The **Match interval** parameter defines the schedule for automatic reconciliation or matching. If you turn on the **Automatically match and pay the freight invoice** parameter, the minimum standard recommended interval is 120 seconds.

### Set up billing groups

Billing groups are user-defined categories. They can be set up to reflect the categories of charges that are present on the invoices that you receive from carriers. To set them up, go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Billing group**, and specify a billing group ID and name. (Both fields are free-text fields.)

### Set up the freight bill type

Freight bill types define how freight bills and carrier invoices should be matched. They define specific criteria, both mandatory and optional. The auto matching process considers a freight bill and an invoice only if defined mandatory criteria are populated and match on both. If optional criteria are blank on the freight bill or the invoice, the process can still consider them.

1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Freight bill type**.
1. Select **New**.
1. In the **Freight bill type** field, enter a value.
1. In the **Engine assembly** field, enter *Microsoft.Dynamics.Ax.Tms.dll*. This assembly is the standard TMS matching engine code library.
1. In the **Engine class** field, enter *Microsoft.Dynamics.Ax.Tms.Bll.GenericNormalizer*. This class is the standard TMS matching engine class.
1. Select **New**.
1. In the **Description** field, select the value that should match on the freight bill and the carrier invoice.
1. In the **Match required** field, select one of the following values:

    - *Yes* – The value selected in the **Description** field must match on both the freight bill and the carrier invoice.
    - *No* – The value selected in the **Description** field can be blank on the freight bill or the carrier invoice.

1. Select **Save**.
1. Close the page.

### Set up the freight bill type assignment

The freight bill type assignment specifies the freight bill type that is used for a carrier. The system then uses that freight bill type to determine the matching requirements when an invoice is received. If carriers ship from or to multiple sites and warehouses within the same legal entity, leave the **Site** and **Warehouse** fields blank.

1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Freight bill type assignments**.
1. Select **New**.
1. In the **Mode** field, enter or select a value.
1. In the **Shipping carrier** field, enter or select a value.
1. In the **Freight bill type** field, select the freight bill type that you created earlier.
1. Close the page.

### Set up the audit master

The audit master defines the tolerance limits for automatic freight reconciliation. In other words, it specifies how much the monetary amounts on the freight bill and the carrier invoice can differ. If the difference is outside the defined tolerance limits, reconciliation is prevented from occurring. The audit master also defines how discrepancies are handled.

1. Go to **Transportation management** \> **Setup** \> **Freight reconciliation** \> **Audit master**.
1. Select **New**.
1. In the **Audit master ID** field, enter a value.
1. In the **Shipping carrier** field, select the same shipping carrier that you selected earlier.
1. In the **Freight bill type** field, select the freight bill type that you created earlier.
1. On the **Tolerance** FastTab, in the **Minimum tolerance level** field, enter a number.
1. In the **Maximum tolerance level** field, enter a number.
1. On the **Result** FastTab, in the **Overpayment reason code** field, enter or select a value.
1. In the **Underpayment reason code** field, enter or select a value.

    If the monetary amounts on the freight bill and the carrier invoice differ, and the difference is within the defined tolerance limits, the overpayment and underpayment reason codes specify the accounts that the difference is registered on.

1. Close the page.

You can also define exceptions if you don't want specific types of charges to be evaluated according to the same criteria as the audit master during the automatic reconciliation process.

### Auto matching

When multiple freight invoices are matched to the same freight bill, the process for auto matching works in the following way:

1. All unmatched freight invoices are sorted by amount. The invoice that has the largest amount is listed first.
1. The freight invoices are matched one by one until the freight bill has no positive remaining amount.
1. Depending on the setup of the audit master and the remaining amount on the freight invoices, the remaining amount is set.

## Example

You have an original freight bill (FB) for the amount of 1,500. You create three freight invoices for FB (Inv1, Inv2, and Inv3). There's one invoice line for each invoice. The following settings are used:

- **Original freight bill FB:** Amount = 1,500
- **Freight invoice Inv1:** Amount = 1,000
- **Freight invoice Inv2:** Amount = 600
- **Freight invoice Inv3:** Amount = &minus;100

### Automatic matching result

Auto matching runs in the following order:

1. Sort all freight invoices in descending order by amount: Inv1 &rarr; Inv2 &rarr; Inv3.
1. Match Inv1 with FB. Inv1 has 1,000 matched, and FB has a remaining amount of 500. Therefore, the status is set to *Partially matched*.
1. Match Inv2 with FB. Inv2 has 500 matched, and FB has a remaining amount of 0 (zero). Therefore, the status is set to *Fully matched*.
1. Because FB is now fully matched, Inv3 isn't processed.

### Manual matching result

The results for manual matching vary, depending on the order of matching, as the following example cases show.

#### Manual matching case 1

One way to do manual matching for this example is to proceed in the following way:

1. Match FB with Inv1. FB has a remaining amount of 500. Therefore, the status is set to *Partially matched*.
1. Match Inv2 with FB. Inv2 has 500 matched, and FB has a remaining amount of 0 (zero). Therefore, the status is set to *Fully matched*.
1. When you try to manually match Inv3, you don't find any unmatched freight bills.

This case is essentially the same as auto matching.

#### Manual matching case 2

Another way to do manual matching for this example is to proceed in the following way:

1. Match Inv3 with FB. FB has a remaining amount of 1,600, which is the same as subtracting &minus;100 from 1,500. Both FB and Inv3 have a matched quantity of &minus;100.
1. Match Inv1 and Inv2 with FB, one after the other. FB is fully matched.

As this example shows, matching should always be done manually if freight invoices have negative amounts. This approach ensures the freight invoices that have negative amounts can always be matched to a freight bill that wasn't fully matched, because you can control the matching sequence.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
