---
# required metadata

title: Settlement priority in the public sector
description: This article provides information about how public sector can automatically or manually prioritize settlements by using billing classifications. 
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustBillingClassification, CustBillingCode, CustParameters, CustSettlementPrioritySetup, LedgerParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: b6f96e12-5614-4edf-9f67-47bf011b6ee7
ms.search.region: Global
ms.search.industry: Public sector
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Settlement priority in the public sector

[!include [banner](../includes/banner.md)]

In Dynamics 365 Finance, you can manually select transactions to settle, or you can use the automatic settlement functionality. Public-sector organizations have additional options for prioritizing settlements by using billing classifications. These options can be used with automatic or manual settlement.

## How to set the general ledger parameters and accounts receivable parameters for settlement priority

To use billing classifications to control settlement priorities, you must set both a sales tax parameter in the General ledger app and settlement parameters in the Accounts receivable app. 

> [!NOTE]
> Your billing classifications should be completely set up and enabled before you set these parameters. As soon as you enable billing classifications, Billing classification becomes a required field on the free text invoice. 

To learn more about billing classifications, including how to enable them, see [Billing classifications and billing codes in the public sector](billing-classifications-billing-codes-public-sector.md).

-   On the **General ledger parameters** page, in the **Sales tax** section, on the **Tax options** FastTab, select the **Sales tax amount per invoice line** option.
-   On the **Accounts receivable parameters** page, in the **Settlement** section, do the following:
    -   Select the option to mark lines on free text invoices and interest notes.
    -   Select the option to prioritize settlement.
    -   Click **Manage priority**, and edit the page to make the **Billing** attribute active and to set the invoice line priority and related settings. The **Billing** attribute is not available until billing classifications are enabled.

Three options are available for the invoice line priority: **None**, **Billing code**, and **Proration**.

-   If you select **None** for the invoice priority, settlement is prioritized by billing classifications. When you do this, payments are applied first to the transactions with the highest billing classification priority. Any remaining payment is applied to the billing classification with the next-highest priority, and so on until the payment is exhausted.
-   If you select **Billing code**, settlement is prioritized by billing classifications and billing codes are used to further refine the settlement priority. When you do this, you can choose whether to extend billing codes across all invoices. For example, suppose that you have three invoices that have the billing classification Parks. All three invoices have four lines, and all four lines have billing codes.
    -   If you extend billing codes across all invoices, the settlement process looks at all 12 lines, and settles the payment according to the billing code priority. Therefore, all lines that have the highest priority billing code are settled before any line that has the next-highest priority billing code is settled.
    -   If you don’t extend billing codes across all invoices, the settlement process looks at the lines on each invoice separately. All of the lines on the first invoice are settled according to the billing code priority before any line on the next invoice is settled.
-   If you select **Proration**, settlement is prioritized by billing classifications and proration is used to further refine the settlement priority within billing classifications. When you do this, you can choose whether to use equal or proportional proration. In either case, all lines on one invoice must be settled before any line on the next invoice is settled. For example, suppose that you have three invoices that have the billing classification Parks. Each invoice has four lines, for $200, $400, $600, and $800. A payment of $2500 has been received.
    -   If you use equal proration, a payment amount that will not pay an invoice in full is divided into four equal portions. One portion is applied to each line. The result for the example would be as follows:
        -   The first invoice is completely settled, and $500 is left over to apply to the next invoice.
        -   The remaining $500 is divided into four equal portions of $125 and applied to each invoice line on the second invoice.
        -   Nothing is applied to any line on the third invoice.
    -   If you use proportional proration, a payment amount that will not pay an invoice in full is divided into proportionate amounts and applied to each invoice line. The proportion is based on the line amount relative to the total invoice amount. The result for the example would be as follows:
        -   The first invoice is completely settled, and $500 is left over to apply to the next invoice.
        -   The remaining $500 is divided into four proportional amounts of $50, $100, $150, and $200 and applied to the corresponding lines on the second invoice.
        -   Nothing is applied to any line on the third invoice.

## How to set the settlement priority of billing codes, billing classifications, and settlement attributes
During the settlement process, settlement attributes are considered first, then billing classifications, then billing codes.

-   After you add billing codes to a billing classification, use the **Up** and **Down** buttons on the **Billing codes** FastTab to arrange the billing codes in priority order. (This is necessary only if you plan to use **Billing code** as your invoice line priority.)
-   After you create all of the billing classifications for your organization, use the **Up** and **Down** buttons at the top of the **Billing classifications** page to arrange the billing classifications in priority order.
-   After you enable the **Billing** attribute on the **Settlement priority** page, use the **Up** and **Down** buttons at the top of the page to arrange the active settlement attributes in priority order.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
