---
# required metadata

title: Configure settlement
description: How and when transactions are settled can be complex subjects, so it's essential that you understand and correctly define the parameters to meet your business requirements. This article describes the parameters that are used for settlement for both Accounts payable and Accounts receivable. 
author: angelad116
ms.date: 05/16/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, CustParameters, VendOpenTrans, VendParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 6b61e08c-aa8b-40c0-b904-9bca4e8096e7
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure settlement

[!include [banner](../includes/banner.md)]

How and when transactions are settled can be complex subjects, so it's essential that you understand and correctly define the parameters to meet your business requirements. This article describes the parameters that are used for settlement for both Accounts payable and Accounts receivable. 

The following parameters affect how settlements are processed in Microsoft Dynamics 365 Finance. Settlement is the process of settling an invoice against a payment or credit note. These parameters are located in the **Settlement** area of the **Accounts receivable parameters** and **Accounts payable parameters** pages.

- **Automatic settlement** – Set this option to **Yes** if a transaction should be settled automatically against other open transactions when it is posted. If this option is set to **No**, users can manually settle transactions when they enter payments, or later, by using the **Settle transactions** page.
- **Cash discount administration** – Specify how a [cash discount is handled when an invoice is overpaid](cash-discount-handling-overpayments.md). For an overpayment, the cash discount can be reduced, it can be treated as a difference, or it can remain on account for the vendor or customer.
  -   **Unspecific** – The cash discount amount is reduced by the overpayment amount. This behavior is always used, regardless of whether the overpayment amount is more than or less than the amount that is entered in the **Maximum overpayment or underpayment** field.
  -   **Specific** – The overpayment amount either is posted to a cash discount difference ledger account, or remains a balance on the customer’s or vendor's account. The specific behavior depends on whether the overpayment amount is between 0.00 and the amount that is entered in the **Maximum overpayment or underpayment** field, or whether the overpayment amount is more than the **Maximum overpayment or underpayment** amount.
- **Maximum penny difference** – Enter the maximum permitted penny difference for the settled transactions. If the difference is equal to or less than the penny difference that is specified in this field, the difference will be posted to the penny difference ledger account that is specified on the **Accounts for automatic transactions** page.
- **Maximum overpayment or underpayment** – Enter the amount that is accepted for overpayment and underpayment. To calculate tax on overpayments or underpayments, on the **General ledger parameters** page, click **Sales tax**, and then select the **Sales tax on overpayment or underpayment** option.
  -   If the overpayment or underpayment produces a difference that is less than the difference that is defined in the **Maximum penny difference** field, the penny difference amount is posted to the penny difference account.
  -   If the overpayment or underpayment produces a difference that is more than the difference that is defined in the **Maximum penny difference** field, the difference amount is posted to the difference account that is selected for the **Customer cash discount** or **Vendor cash discount** posting type on the **Accounts for automatic transactions** page.
- **Calculate cash discounts for partial payments** – Set this option to **Yes** to enable cash discounts to be automatically calculated for partial payments.
  -   The effect of this option depends on the value of the **Use cash discount** field on the **Settle transactions** page. If this option is set to **Yes**, the discount is taken when the **Use cash discount** field is set to **Normal**. When the **Use cash discount** field is set to **Always**, the cash discount is always taken, regardless of the setting of this field. When the **Use cash discount** field is set to **Never**, the cash discount is never taken, regardless of the setting of this field.
  -   If this option is set to **Yes**, and a user changes the value in the **Amount to settle** field on the **Settle transactions** page, the discount is automatically calculated and displayed as the default entry in the **Cash discount amount to take** field.
  -   If this option is set to **No**, and a user changes the value in the **Amount to settle** field on the **Settle transactions** page, the default entry in the **Cash discount amount to take** field is **0** (zero).
- **Calculate cash discounts for credit notes** – Set this option to **Yes** to automatically calculate a cash discount for credit notes. In Accounts receivable, a credit note transaction is a negative transaction that has a value in the **Invoice** field on the **Free text invoice** page, or a return on the **Sales order** page.
  - The effect of this option depends on the value of the <strong>Use cash discount</strong> field on the <strong>Settle transactions</strong> page. If this option is set to <strong>Yes</strong>, the discount is taken when the *<strong><em>Use cash discount</em></strong>* field is set to <strong>Normal</strong>. When the *<strong><em>Use cash discount</em></strong>* field is set to <strong>Always</strong>, the cash discount is always taken, regardless of the setting of this field. When the *<strong><em>Use cash discount</em></strong>* field is set to <strong>Never</strong>, the cash discount is never taken, regardless of the setting of this field.
  - If this option is set to **Yes**, and a credit note is marked on the **Settle transactions** page, the discount is automatically calculated and is displayed as the default entry in the **Cash discount amount to take** field.
  - If this option is set to **No**, and a credit note is marked on the **Settle transactions** page, the default entry in the **Cash discount amount to take** field is **0** (zero).

- **Discount offset accounts (AP only)** – Define the default cash discount ledger account that should be used for the accounting entry for cash discounts.
  -   **Use Main account for vendor discounts** – The cash discount is posted to the main account that is defined on the **Cash discount setup** page.
  -   **Accounts on the invoice lines** – The cash discount is posted to the ledger accounts on the original invoice.
- **Mark lines on free text invoices and interest notes (AR only)** – Set this option to **Yes** to enable the **Mark invoice lines** button on the **Enter customer payments**, **Payment journal voucher**, and **Settle transactions** pages. This button lets users mark individual lines for settlement.
- **Prioritize settlement (AR only)** – Set this option to **Yes** to enable the **Mark by priority** button on the **Enter customer payments** and **Settle transactions** pages. This button lets users assign the predetermined settlement order to transactions.  After the settlement order has been applied to a transaction, the order and the payment allocation can be modified before posting.
- **Use priority for automatic settlements** – Set this option to **Yes** to use the defined priority order when transactions are automatically settled. This field is available only if the **Prioritize settlement** and **Automatic settlement** options are set to **Yes**.

## Fixed dimensions on accounts receivable/accounts payable main accounts

When fixed dimensions are used on the accounts receivable/accounts payable main account, additional accounting entries and two additional vendor transactions will be posted by the settlement process. Settlement compares the accounts receivable/accounts payable ledger account from the invoice and payment.  When the payment and settlement are completed together, which is the typical scenario, the payment’s accounting entry isn’t posted to General ledger until after the settlement process is also complete. Due to the order of processing events, settlement is unable to determine the actual accounts receivable/accounts payable ledger account from the payment’s accounting entry. Settlement reconstructs what the ledger account will be for the payment. This becomes an issue when a fixed dimension is used for the accounts receivable/accounts payable main account.

To reconstruct the ledger account, the accounts receivable/accounts payable main account is retrieved from the posting profile and the financial dimensions are retrieved from the vendor transaction record for the payment, as defined on the payment journal. Fixed dimensions are not defaulted onto payment journals, but instead are applied to the main account as the last step of the posting process. As a result, the fixed dimension value is likely not contained on the vendor transaction, unless it defaulted from another source, such as the vendor. The reconstructed account will not include the fixed dimension. Settlement processing will determine that an adjusting entry must be created, because the invoice posted with the fixed dimension value and the reconstructed payment account did not.  As settlement continues with posting the adjusting entry, the last step in posting is for the fixed dimension to be applied. By adding the fixed dimension to the adjusting entry, it is posted with a debit and credit to the same ledger account. Settlement cannot roll back the accounting entry.

To avoid the additional accounting entries, the debit and credit to the same ledger account, the following workarounds should be considered, depending on your business requirements. 

-   Organizations often use fixed dimensions to zero-fill a financial dimension that isn't required. This is commonly the case for balance sheet accounts, such as accounts receivable/accounts payable. Account structures can be used to not track financial dimensions that are typically zero-filled.  You can remove the financial dimension for the Balance sheet accounts, eliminating the need to use fixed dimensions.
-   If your organization requires fixed dimensions on the accounts receivable/accounts payable main account, find a way to default the fixed dimension onto the payment, so that the fixed dimension value is stored  on the vendor transaction for the payment. This will allow the system to reconstruct the accounts receivable/accounts payable main account to include the fixed dimension values. The fixed dimension value can be defined as a default on either vendors or the journal name for the payment journal.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
