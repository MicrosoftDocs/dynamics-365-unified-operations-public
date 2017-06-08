---
# required metadata

title: Configure settlement
description: How and when transactions are settled can be complex subjects, so it's essential that you understand and correctly define the parameters to meet your business requirements. This article describes the parameters that are used for settlement for both Accounts payable and Accounts receivable. 
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, CustParameters, VendOpenTrans, VendParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 14601
ms.assetid: 6b61e08c-aa8b-40c0-b904-9bca4e8096e7
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure settlement

[!include[banner](../includes/banner.md)]


How and when transactions are settled can be complex subjects, so it's essential that you understand and correctly define the parameters to meet your business requirements. This article describes the parameters that are used for settlement for both Accounts payable and Accounts receivable. 

The following parameters affect how settlements are processed in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. Settlement is the process of settling an invoice against a payment or credit note. These parameters are located in the **Settlement** area of the **Accounts receivable parameters** and **Accounts payable parameters** pages.

-   **Automatic settlement** – Set this option to **Yes** if a transaction should be settled automatically against other open transactions when it is posted. If this option is set to **No**, users can manually settle transactions when they enter payments, or later, by using the **Settle transactions** page.
-   **Cash discount administration** – Specify how a [cash discount is handled when an invoice is overpaid](cash-discount-handling-overpayments.md). For an overpayment, the cash discount can be reduced, it can be treated as a difference, or it can remain on account for the vendor or customer.
    -   **Unspecific** – The cash discount amount is reduced by the overpayment amount. This behavior is always used, regardless of whether the overpayment amount is more than or less than the amount that is entered in the **Maximum overpayment or underpayment** field.
    -   **Specific** – The overpayment amount either is posted to a cash discount difference ledger account, or remains a balance on the customer’s or vendor's account. The specific behavior depends on whether the overpayment amount is between 0.00 and the amount that is entered in the **Maximum overpayment or underpayment** field, or whether the overpayment amount is more than the **Maximum overpayment or underpayment** amount.
-   **Maximum penny difference** – Enter the maximum permitted penny difference for the settled transactions. If the difference is equal to or less than the penny difference that is specified in this field, the difference will be posted to the penny difference ledger account that is specified on the **Accounts for automatic transactions** page.
-   **Maximum overpayment or underpayment** – Enter the amount that is accepted for overpayment and underpayment. To calculate tax on overpayments or underpayments, on the **General ledger parameters** page, click **Sales tax**, and then select the **Sales tax on overpayment or underpayment** option.
    -   If the overpayment or underpayment produces a difference that is less than the difference that is defined in the **Maximum penny difference** field, the penny difference amount is posted to the penny difference account.
    -   If the overpayment or underpayment produces a difference that is more than the difference that is defined in the **Maximum penny difference** field, the difference amount is posted to the difference account that is selected for the **Customer cash discount** or **Vendor cash discount** posting type on the **Accounts for automatic transactions** page.
-   **Calculate cash discounts for partial payments** – Set this option to **Yes** to enable cash discounts to be automatically calculated for partial payments.
    -   This effect of this option depends on the value of the **Use cash discount** field on the **Settle transactions** page. If this option is set to **Yes**, the discount is taken when the **Use cash discount** field is set to **Normal**. When the **Use cash discount** field is set to **Always**, the cash discount is always taken, regardless of the setting of this field. When the **Use cash discount** field is set to **Never**, the cash discount is never taken, regardless of the setting of this field.
    -   If this option is set to **Yes**, and a user changes the value in the **Amount to settle** field on the **Settle transactions** page, the discount is automatically calculated and displayed as the default entry in the **Cash discount amount to take** field.
    -   If this option is set to **No**, and a user changes the value in the **Amount to settle** field on the **Settle transactions** page, the default entry in the **Cash discount amount to take** field is **0** (zero).
-   **Calculate cash discounts for credit notes** – Set this option to **Yes** to automatically calculate a cash discount for credit notes. In Accounts receivable, a credit note transaction is a negative transaction that has a value in the **Invoice** field on the **Free text invoice** page, or a return on the **Sales order** page.
    -   The effect of this option depends on the value of the **Use cash discount** field on the **Settle transactions** page. If this option is set to **Yes**, the discount is taken when the ****Use cash discount**** field is set to **Normal**. When the ****Use cash discount**** field is set to **Always**, the cash discount is always taken, regardless of the setting of this field. When the ****Use cash discount**** field is set to **Never**, the cash discount is never taken, regardless of the setting of this field.
    -   If this option is set to **Yes**, and a credit note is marked on the **Settle transactions** page, the discount is automatically calculated and is displayed as the default entry in the **Cash discount amount to take** field.
    -   If this option is set to **No**, and a credit note is marked on the **Settle transactions** page, the default entry in the **Cash discount amount to take** field is **0** (zero).
-   **Discount offset accounts (AP only)** – Define the default cash discount ledger account that should be used for the accounting entry for cash discounts.
    -   **Use Main account for vendor discounts** – The cash discount is posted to the main account that is defined on the **Cash discount setup** page.
    -   **Accounts on the invoice lines** – The cash discount is posted to the ledger accounts on the original invoice.
-   **Mark lines on free text invoices and interest notes (AR only)** – Set this option to **Yes** to enable the **Mark invoice lines** button on the **Enter customer payments**, **Payment journal voucher**, and **Settle transactions** pages. This button lets users mark individual lines for settlement.
-   **Prioritize settlement (AR only)** – Set this option to **Yes** to enable the **Mark by priority** button on the **Enter customer payments** and **Settle transactions** pages. This button lets users assign the predetermined settlement order to transactions.  After the settlement order has been applied to a transaction, the order and the payment allocation can be modified before posting.
-   **Use priority for automatic settlements** – Set this option to **Yes** to use the defined priority order when transactions are automatically settled. This field is available only if the **Prioritize settlement** and **Automatic settlement** options are set to **Yes**.




