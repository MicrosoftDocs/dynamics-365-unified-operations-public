---
title: Post detailed payments for vendor and customers
description: Learn about the feature that posts detailed vendor and customer payments, including a summary on amounts in bank accounts and the setup process.
author: mukumarm
ms.author: mukumarm
ms.topic: article
ms.date: 08/04/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
ms.dyn365.ops.version: 10.0.16
---

# Post detailed vendor and customer payments

The **Ability to post detailed vendor and customer payments, but summarize amounts to bank account** feature posts vendor and customer payments as separate vouchers, but summarizes the payments when the bank account balance is updated.

For example, your bank pays three vendors 100 euros (EUR) each on behalf of your organization. When the bank completes the transactions, the bank statement might show the three payments in detail, or it might show a summarized withdrawal of 300 EUR. If your bank summarizes the payments into a single withdrawal, use this feature to mimic that functionality. Therefore, it can help streamline the bank reconciliation process.

> [!IMPORTANT]
> This feature eliminates the need to record multiple vendor or customer payments in a single voucher number. To determine whether you can define the parameters to prohibit multiple subledger transactions in a single voucher, see [One voucher](one-voucher.md).

## Setup

In the **Feature management** workspace, enable the feature named **Ability to post detailed vendor and customer payments, but summarize amounts to bank account**.

### Journal names

You can summarize payments to the bank subledger for the following journal types:

- Daily (General journal)
- Vendor disbursement (Vendor payment journal)
- Customer payment (Customer payment journal)

On the **Journal names** page, the **Bank** section includes two new fields: **Summarize amounts in bank account** and **Summarization criteria**.

:::image type="content" source="./media/bank-field1.png" alt-text="Screenshot of the Journal names page showing the Bank section with the Summarize amounts in bank account and Summarization criteria fields.":::

When you set the **Summarize amounts in bank account** option to **No** (the default value), payments in a journal batch group update the bank account in either detail or summary, depending on whether the payments are entered in a single voucher number. Posting to the bank account works just as it does when the new feature is turned off. When you turn on the feature, don't enter multiple payments in a single voucher number.

You can set the **Summarize amounts in bank account** option to **Yes** only if the **New voucher** field for the journal name is set to **In connection with balance**. In this case, the option promotes (but doesn't guarantee) the use of a single voucher per vendor or customer payment. When you turn on the new feature, summarization doesn't occur if the voucher contains more than one vendor or customer.

> [!NOTE]
> If you set the **New voucher** field to a value other than **In connection with balance**, and you try to set the **Summarize amounts in bank account** option to **Yes**, you receive the following error message: "The Summarize amounts in bank account setting must be No when New voucher is set to Manual or One voucher number only."
>
> If you set the **Summarize amounts in bank account** option to **Yes**, and you try to change the value of the **New voucher** field to something other than **In connection with balance**, you receive the following error message: "The New voucher setting must be In connection with balance when Summarize amounts in bank account is set to Yes."

If you set the **Summarize amounts in bank account** option to **Yes**, the **Summarization criteria** field becomes available. This field enables your organization to specify the criteria that are used to summarize payments to the bank account. The following values are available:

- **Do not summarize** – Payments aren't summarized, even if the **Summarize amounts in bank account** option is set to **Yes**.
- **Default criteria** – Payments that have the same bank account, method of payment, currency code, account type (either customer or vendor), and transaction date are grouped for summarization.
- **Default criteria with document number** – Payments that have the same bank account, method of payment, currency code, account type (either customer or vendor), transaction date, and document number are grouped for summarization. If the document number for more than one payment is blank, the blank value is treated as a valid document number, and those payments are summarized together.
- **Default criteria with payment reference** – Payments that have the same bank account, method of payment, currency code, account type (either customer or vendor), transaction date, and payment reference are grouped for summarization. If the payment reference for more than one payment is blank, the blank value is treated as a valid payment reference, and those payments are summarized together.

## Parameters

When you summarize vendor or customer payments, the system assigns a new number to the single bank account transaction.

On the **Cash and bank management parameters** page, on the **Number sequences** tab, define a number sequence for the **Bank transaction summarization ID** reference.

### Entering payments in a journal

When you use this feature, you can summarize payments to the bank account when you enter them from any of the following journals:

- Accounts payable - Payments – Vendor payment journal
- Accounts receivable - Payments - Customer payment journal
- General ledger - Journal entries - General journals

After you create a journal, verify the summarization settings on the **Setup** tab of the journal batch header. The system takes default settings from the journal name, but you can override them for individual journal batch numbers.

After you enter all payments in the journal, the system uses the following criteria during posting to determine which payments can be considered for summarization. These criteria affect how you should enter payments in the journal.

- Only payments that have the following combinations of an account and an offset account are considered for summarization: Vendor/Bank, Bank/Vendor, Customer/Bank, and Bank/Customer. The system doesn't consider payments that are posted to a ledger account (*bridged payments*) for summarization.
- Each payment voucher must contain only a single vendor or customer. If a voucher number contains multiple vendors or customers, the system doesn't consider it for summarization.
- More than one payment, in separate vouchers, must exist in the journal batch number.
- Payments in different journal batch numbers aren't considered for summarization.

### Posting payments in a journal

During posting, the system considers the group of payment lines for summarization as described in the previous section. After the system determines the group of payment lines, it performs summarization based on the settings on the journal batch header.

- The system doesn't perform bank transaction summarization if the **Summarize amounts in bank account** option is set to **No**, or if the **Summarization criteria** field on the journal batch header is set to **Do not summarize**.

    If you define a journal name so that payments post to the bank account in summary, but set the **Summarization criteria** field on the journal batch header to **Do not summarize**, the system doesn't summarize the transactions.

- The system performs bank transaction summarization when you set the **Summarize amounts in bank account** option to **Yes**, and set the **Summarization criteria** field to **Default criteria**, **Default criteria with document number**, or **Default criteria with payment reference**. For more information, see the description of the **Summarization criteria** field in the [Journal names](#journal-names) section.

You can post more than one group of summarized payments to a bank account. For example, if the journal contains a group of vendor payments and a group of customer payments, you can have two or more summarized payments. You can create one or more summarized bank account transactions for the vendor payments, and one or more summarized bank account transactions for the customer payments.

In the next example, you enter the following vendor payments in a journal. You set up the journal batch number so that the **Summarization criteria** field is set to **Default criteria with document number**. During posting, the system summarizes, or doesn't summarize, the payments as shown in the following table.

| Voucher number | Transaction date | Account | Currency | Debit | Credit | Offset account | Method of payment | Document number | What's summarized? |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | August 15 | Vendor A | EUR | 100 | | USMF OPER | Electronic | | Vouchers 1 and 2 summarized |
| 2 | August 15 | Vendor B | EUR | 200 | | USMF OPER | Electronic | | Vouchers 1 and 2 summarized |
| 3 | August 17 | Vendor C | CAD | 300 | | USMF OPER | Electronic | | Posted to bank account in detail |
| 4 | August 18 | Vendor B | EUR | 400 | | USMF OPER | Electronic | | Posted to bank account in detail |
| 5 | August 28 | Vendor D | EUR | 500 | | USMF OPER | Electronic | 1 | Vouchers 5 and 6 summarized |
| 6 | August 28 | Vendor Z | EUR | 600 | | USMF OPER | Electronic | 1 | Vouchers 5 and 6 summarized |
| 7 | August 28 | Vendor Z | EUR | 700 | | USMF OPER | Electronic | 2 | Vouchers 7, 8, and 9 summarized |
| 8 | August 28 | Vendor B | EUR | 800 | | USMF OPER | Electronic | 2 | Vouchers 7, 8, and 9 summarized |
| 9 | August 28 | Vendor A | EUR | 900 | | USMF OPER | Electronic | 2 | Vouchers 7, 8, and 9 summarized |

<!--:::image type="content" source="./media/summarized-payments2.png" alt-text="Screenshot of summary posting results for payments posted to a bank account.":::-->

You post five transactions to the bank account. For two transactions, the system maintains the original payment details. For the other three transactions, the system summarizes payments based on the summarization rules.

### After you post payments in a journal

After you finish posting, you can find the summarized (or detailed) payments in the transactions of the bank account. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.

:::image type="content" source="./media/bank-transactions3.png" alt-text="Screenshot of the Bank transactions page showing summarized and detailed payments for a bank account.":::

For any summarized payment, an asterisk (\*) appears in the **Voucher number** field. Every payment is still posted in detail to the general ledger.

All summarized bank account transactions have a unique summarization ID. If you set the **Summarization criteria** field to **Default criteria with document number**, the document number from the payment lines is used as the summarization ID. Otherwise, the number sequence that you configure on the **Cash and bank management parameters** page generates the summarization ID. If the summarization ID that you assign to a summarized bank transaction is already used by another summarized bank transaction, the system selects a new one from the number sequence. The payment reference isn't used as a summarization ID.

You can view the payment details of a summarized bank account transaction by selecting **View summarization details** on the **Payment summarization details** page.

:::image type="content" source="./media/payment-summary4.png" alt-text="Screenshot of the Payment summarization details page showing the payment details of a summarized bank account transaction.":::

While you're viewing the summarization details, you can view the general ledger voucher of each payment, return to the bank account summarized transaction, or view the settlement information for the selected payment.

The bank account summarized transactions also appear on the bank statement. Therefore, bank reconciliation is easier, regardless of whether you use manual account reconciliation or advanced bank reconciliation. Both reconciliation processes show the bank summarization ID. If you enable advanced bank reconciliation for the bank account, a bank document of the **Summarized transaction** type is generated for the bank account. You can match and reconcile transactions in the same way for other types of bank documents.

:::image type="content" source="./media/bank-reconcile5.png" alt-text="Screenshot of the bank reconciliation worksheet page showing a summarized transaction bank document.":::

>[!NOTE]
>Bank transaction summarization isn't supported for customer or vendor payment transactions that include payment fees. When you apply a payment fee, Finance creates separate bank transactions instead of a summarized bank transaction, even if the journal is configured to summarize amounts in the bank account. As a result, you might need to reconcile additional bank transactions individually during bank reconciliation.
