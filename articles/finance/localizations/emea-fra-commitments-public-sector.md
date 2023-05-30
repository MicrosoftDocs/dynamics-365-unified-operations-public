---
title: Commitments in the public sector in France
description: Commitments are budget control source documents used by public sector entities in France. They are used to reserve budgeted amounts so that an organization can explicitly track budget reservations for management and reporting throughout the expenditure cycle.
author: brpotter
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: France
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Public sector
ms.search.form: BudgetControlConfiguration, PurchAgreement, PurchCommitment_PSN, PurchTable
---

# Commitments in the public sector in France

[!include [banner](../includes/banner.md)]

Commitments are budget control source documents used by public sector entities in France. They are used to reserve budgeted amounts so that an organization can explicitly track budget reservations for management and reporting throughout the expenditure cycle. 

When commitments are used as part of the budgeting process, each purchase agreement, purchase order, and vendor invoice is associated with at least one commitment. The commitment is relieved when the funds are released from the purchase agreement and the purchase order is confirmed. When an invoice does not reference a purchase order or purchase agreement, the commitment associated with the invoice is relieved when the invoice is posted. In addition, a commitment may specify a vendor. When a vendor is specified, any purchase order, purchase agreement, or vendor invoice that references the commitment must have the same vendor. Commitments are valid from the date they are created through the end of the fiscal year or until they are closed. Commitments cannot be carried over from one fiscal year to the next.  
>[!NOTE]
>The **Commitment type** field on the **Purchase agreement** page is not related to the commitment document. That field only specifies whether the purchase agreement is based on a value or a quantity.

## Set up budget control and related prerequisites
Before you can use commitments, commitment number sequences must be defined, budget control must be set up, and available budget amounts must be available. The commitment workflow is optional, but recommended.

-   On the **Budgeting parameters** page, set up number sequences for commitments.
-   Set up workflow to manage the review process for commitments.
-   On the **Budget control configuration** page, set up budget control. The options that are listed below are required for commitments. Settings not listed here can be selected according to the needs and practices of your organization.
    -   In the **Budget funds available** section, select the following options:
        -   Original budget
        -   Actual expenditures
        -   Budget reservations for encumbrances
        -   Budget reservations for pre-encumbrances
        -   Budget reservations for unconfirmed pre-encumbrances
    -   In the **Documents and journals** section:
        -   Verify that both the header and line options are selected for commitments, purchase orders, and vendor invoices.
        -   Verify that the both the header and the line options are cleared for purchase requisitions.
    -   In the **Activate budget control** section, activate the budget control configuration and turn on budget control.
-   On the **General ledger parameters** page, verify that the options in the **Commitment accounting** group in the **Ledger** section are cleared. When you enable commitments, you cannot post budgetary transactions to the general ledger.

## Consume a commitment
There are three ways to consume a commitment.

-   **Assign a purchase agreement to a commitment line.** The commitment is consumed when funds are released from the purchase agreement. To do this, specify the purchase agreement on the commitment line when you create the commitment.
-   **Reference the commitment directly on a purchase order line.** The commitment is consumed when the purchase order is confirmed. No purchase agreement is involved. To do this, create a purchase order according to your usual process. When you add a line to the purchase order, select the commitment to use for this purchase order.
-   **Reference the commitment directly on a vendor invoice.** There may be a purchase agreement assigned on the header of the invoice, but no purchase order is involved. The commitment is consumed when the invoice is posted. To do this, create a vendor invoice according to your usual process. When you add a line to the invoice, select the commitment to use for this invoice.

A commitment can be restricted to a specific vendor, or it can be available for assignment to any vendor. If the commitment is restricted to a specific vendor, it is available for selection only when the vendor invoice or purchase order specifies the same vendor.

## Increase or decrease a commitment
It is sometimes necessary to change a confirmed commitment. For example, if severe weather results in higher-than-planned spending for snow removal and related services, you may need to increase a commitment. When a commitment line has already been referenced by a purchase order or vendor invoice, your ability to delete or change the commitment line may be limited.

## Close commitments
Commitments must be closed manually.

-   You can close a single commitment line or an entire commitment by using the **Close** button on the Action Pane of the commitment.
-   The purchase order year-end process automatically reverses closing entries and creates or updates budget in commitment documents in the new fiscal year. This is handled by the process. No manual intervention is required. However, after you have processed purchase orders and commitments, you must go to the **Commitment close** page to close the commitments in the closing fiscal year.

**Important**: When you select the commitments that you want to close, be sure that you don't select the commitments that you have already created for the new fiscal year. Closing a commitment line cannot be reversed. If you close a commitment line by mistake, you must create a new commitment to restore the budget reservation. To learn more about the year-end process, see [Year-end processing in the public sector](../public-sector/year-end-processing-public-sector.md).

## Additional resources

[Public sector accounting in France](emea-fra-public-sector-accounting.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
