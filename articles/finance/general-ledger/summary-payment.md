---
# required metadata

title: Posting detailed payments for vendor and customers
description: This article describes posting detailed vendor and customer payments and summarize amounts in bank accounts.
author: kweekley
ms.date: 01/12/2023
ms.topic: article
ems.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 25871
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-03-23
ms.dyn365.ops.version: 10.0.16

---

# Posting detailed vendor and customer payments

The feature **Ability to post detailed vendor and customer payments, but summarize amounts to bank account** posts vendor and customer payments as separate vouchers but summarize the payments when updating the bank account balance. 

For example, your bank pays three vendors 100 EUR each on behalf of your organization. When the bank completes the transactions, the bank statement may show the three payments in detail or may show a summarized withdrawal of 300 EUR. If your bank summarizes the payments into a single withdrawal, this feature can be used to mimic that functionality, making the bank reconciliation process more streamlined.  

>[!IMPORTANT]
>This feature eliminates the need to record multiple vendor or customer payments within a single voucher number. See the One voucher documentation to determine whether the General ledger parameter can be defined to not allow multiple subledger transactions within a single voucher.


## Setup
In **Feature management**, enable the feature **Ability to post detailed vendor and customer payments, but summarize amounts to bank account**. 

### Journal names
The ability to summarize payments to the bank subledger is supported on the following journal types:
•	Daily (General journal)
•	Vendor disbursement (Vendor payment journal)
•	Customer payment (Customer payment journal)

On the **Journal names** page, two new options are available under the **Bank** field group: 

[![Journal names](./media/bank-field1.png)](./media/bank-field1.png)
 
The option **Summarize amounts in bank account** defaults to **No**. If the option is set to **No**, payments within a journal batch group will update the bank account in either detail or summary, depending on whether the payments are entered in a single voucher number or not. Posting to the bank account works the same as if the feature were turned off. With this feature, we no longer recommend entering multiple payments within a single voucher number. 

The option **Summarize amounts in bank account** can only be changed to **Yes** if the **New voucher** setting on the journal name is defined as **In connection with balance**. By having this setting defined as **In connection with balance**, it promotes (but doesn’t guarantee) a single voucher per vendor or customer payment. When using the new feature, summarization will not happen if the voucher contains more than one vendor or customer. 

>[!NOTE]
>If New voucher isn't defined as **In connection with balance**, the **Summarize amounts in bank account** can't be enabled. An error message “The Summarize amounts in bank account setting must be No when New voucher is set to Manual or One voucher number only.” If the option **Summarize amounts in bank account** is **Yes**, an error message will be given if New voucher is changed to a value different from **In connection with balance**. The error is “The New voucher setting must be In connection with balance when Summarize amounts in bank account is set to Yes.”


When changing the first option to **Yes**, the **Summarization criteria** option becomes available. The second option allows your organization to define which criteria is used to summarize payments to the bank account. 

The following options are available:
 - **Do not summarize** - Payments will not be summarized, even if **Summarize amounts in bank account** = **Yes**.
 - **Default criteria** – Payments with the same bank account, method of payment, currency code, account type (either customer or vendor) and transaction date will be grouped for summarization.
 - **Default criteria with document number** - Payments with the same bank account, method of payment, currency code, account type (either customer or vendor), transaction date and document number will be grouped for summarization. If more than one payment includes a blank document number, that is considered a valid number and those payments will be summarized together.
 - **Default criteria with payment reference** - Payments with the same bank account, method of payment, currency code, account type (either customer or vendor), transaction date and payment reference will be grouped for summarization. If more than one payment includes a blank payment reference, that is considered a valid number and those payments will be summarized together.

## Parameters

When summarizing vendor or customer payments, a new number is assigned to the single bank account transaction.
On the **Cash and bank management parameters** page, **Number sequences** tab defines the number sequence for the **Bank transaction summarization ID**.

### Entering payments into journal
When using this feature, payments can be summarized to the bank account when entered from any of the following journals:
 - Accounts payable - Payments – Vendor payment journal 
 - Accounts receivable - Payments - Customer payment journal 
 - General ledger - Journal entries - General journals

After creating the journal, verify the summarization settings on the **Setup** tab of the journal batch header. The settings default from the journal name, but the settings can be overridden on individual journal batch numbers.

After all payments are entered within the journal, the following criteria is used during posting to determine which payments can be considered for summarization. 
These conderations impacts how payments should be entered within the journal:
 - Only payments with the Account/Offset account combinations are considered for summarization: Vendor/Bank, Bank/Vendor, Customer/Bank and Bank/Customer. Payments posted to a Ledger account (bridged payments) are not considered for summarization.
 - Each payment voucher must only contain a single vendor or customer. If a voucher number contains multiple vendors or customers, it will not be considered for summarization.
 - More than one payment, in separate vouchers, must exist within the journal batch number. 
 - Payments in different journal batch numbers are not considered for summarization.

### Posting payments in a journal
During posting, the group of payment lines considered for summarization as defined in the previous section. Once the group of payments is determined, the summarization will occur based on the settings on the journal batch header. 
 - Bank transaction summarization will not happen when **Summarize amounts in bank account** is **No** or the **Summarization** criteria is **Do not summarize** on the journal batch header.
      - If a Journal name was defined to post the payments in summary to the bank account but the settings were changed on the journal batch header to not summarize, summarization will not happen.
 - Bank transaction summarization will happen when **Summarize amounts in bank account** is **Yes** and the **Summarization** criteria is set to **Default criteria**, **Default criteria with document number**, or **Default criteria with payment reference**. Refer to the summarization criteria in the Journal name setup section.


More than one group of summarized payments can be posted to a bank account. For example, if the journal contains a group of vendor payments and a group of customer payments, you could have two or more summarized payments. One or more summarized bank account transactions could be created for the vendor payments, and one or more summarized bank account transactions could be created for the customer payments. 
Assume the following vendor payments were entered in a journal. The journal batch number was defined to summarize using **Default criteria with document number**. 

The payments are summarized or not summarized as follows during the posting:

[![Summary posting](./media/summarized-payments2.png)](./media/summarized-payments2.png)
 
Five transactions will be posted to the bank account, some maintaining the original payment detail and other payments summarized based on the summarization rules.

### After posting payments in a journal
After posting is complete, the summarized (or detailed payments) can be found on the Transactions of the bank account: Cash and bank management - Bank accounts - Bank accounts.

[![Bank transactions](./media/bank-transactions3.png)](./media/bank-transactions3.png)
 
For any summarized payments, the voucher number will display with an asterisk. Each payment is still posted in detail to the General ledger.


All summarized bank account transactions will have a unique summarization ID. If the summarization criteria is **Default criteria with document number**, the document number from the payment lines will be used as the summarization ID. Otherwise, the summarization ID will be generated from the number sequence configured by the user. If the summarization ID to be assigned to a summarized bank transaction is already used by another summarized bank transaction, a new one will be picked from the number sequence. The payment reference is not used as a summarization ID.


Users can view the payment details of a summarized bank account transaction by choosing the **View summarization details** button on the **Payment summarization details** page.

[![Payment summarization details](./media/payment-summary4.png)](./media/payment-summary4.png)

 
While viewing the summarization details, you can view the general ledger voucher of each payment, return to the bank account summarized transaction or view the settlement information for the selected payment.

The bank account summarized transactions will also be displayed on the bank statement, making bank reconciliation easier, whether using the manual Account reconciliation or Advanced bank reconciliation. Both reconciliation processes show the bank summarization ID. If Advanced bank reconciliation is enabled for the bank account, a bank document with **Summarized transaction** type will be generated for the bank account. Users could match and reconcile them in the same way for other types of bank documents.
 
[![Reconcile bank transactions](./media/bank-reconcile5.png)](./media/bank-reconcile5.png)
