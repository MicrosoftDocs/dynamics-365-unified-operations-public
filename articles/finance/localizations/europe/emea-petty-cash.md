---
title: Petty cash for Eastern Europe and Russia
description: Learn about the petty cash functionality that lets users in Estonia, Lithuania, Czech Republic, Hungary, Latvia, Poland, and Russia reflect cash operations.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-05-31
ms.search.form: RCashBalance, RCashCountStatementForm, RCashPosting, RCashRemainLimit, RCashReportJour_PL, RCashTable, RCashTableBalance, RCashTableCredLimit, RCashTableLastRevaluation, RCashTableTransactions, RCashTrans
---

# Petty cash for Eastern Europe and Russia

[!include [banner](../../includes/banner.md)]

This article provides information about the petty cash functionality that users in Estonia, Lithuania, Czech Republic, Hungary, Latvia, Poland, and Russia can use to reflect cash operations in the system.

Use the petty cash functionality to automate operations for receipts and expenditures of cash, create primary documents, and print related reports. By using the petty cash functionality, you can:

- Account for the receipt and expenditure of available cash assets.
- Generate typical cash forms: Cash reimbursement slips, Cash disbursement slips, and a Journal of registration for cash slips.
- Control the maximum cash amount that's allowed for operations with customers, vendors, and so on.
- Reflect cash operations in various currencies in the system.
- Convert the amounts of cash operations in foreign currency to the default currency to provide accounting reporting.
- Generate a **Cash book** report and a cashier’s report.

## Prerequisites

Before you use the petty cash functionality, complete the following prerequisites:

- Set up cash accounts.
- Set up cash posting profiles.
- Set up number sequences for cash document numbering.
- Set up default values for Cash and bank management parameters.
- Set up cash journal names in General ledger.

### Set up cash accounts

To set up a cash account, open **Cash and bank management** > **Bank accounts** > **Cash accounts**, and enter the following information.

| Field                 | Description                                                                                                          |
|-----------------------|----------------------------------------------------------------------------------------------------------------------|
| Cash                  | Enter a code to identify the cash account (cash).                                                                    |
| Name                  | Enter a description of the cash account.                                                                             |
| Currency              | Select the default currency code for cash transactions.                                                              |
| Number sequence group | If the numbering of cash documents must differ from the numbering that is specified in the parameters, enter a code. |
| More currencies       | Select this check box to allow currencies that differ from the accounting currency to be posted.                     |
| Negative cash         | Select this check box to allow negative cash balances in any currency.                                               |

To set up cash balance control rules for a cash account, select the cash account. On the **Cash account** tab of the action pane, in the **Balance limit** group, select **Balance limit**. Enter the following information.

| Field | Description |
|---|---|
| Currency type | Select the type of currency: **Accounting currency** – Use the basic company currency code. **Indicated currency** – Use a currency code that differs from the basic company currency code. |
| Currency | If you selected **Indicated currency** in the **Currency type** field, select a currency code. This field is unavailable if you selected **Accounting currency** in the **Currency type** field. |
| Balance limit type | Select one of the available values: **Maximum** – The cash balance shouldn't exceed the **Balance limit** amount for the cash account (upper bound). **Minimum** – The cash balance shouldn't go below the **Balance limit** amount for the cash account (bottom bound). |
| Check balance limit | Select what occurs during the approval process for cash documents if the **Balance limit** amount for the cash account is exceeded: **Accept** – The limit can be exceeded. **Warning** – The limit can be exceeded, but the user receives a warning message. The cash document is confirmed or approved. **Error** – The limit can't be exceeded. The user receives an error message, and the cash document isn't confirmed or approved. For more information about the approval process for cash documents, see the "Cash transaction approval and posting" section, later in this article. |
| Balance limit | Enter a limit for the cash account balance. Enter the amount in the currency that you specified. |

### Set up cash posting profiles

Cash posting profiles define postings to the general ledger. To set up a cash posting profile, go to **Cash** **and bank management** > **Setup** > **Cash posting profiles**, and select or create a posting profile. Enter the following information.

| Field | Description |
|---|---|
| Valid for | Select whether the posting profile applies to a specific cash account or all cash accounts: **Table** – If there's a posting profile line for the cash account, use that line for cash transaction posting. **All** – There's no posting profile line for the cash account. |
| Cash | If you selected **Table** in the **Valid for** field, specify the cash account. This field remains blank if you selected **All** in the **Valid for** field. |
| Ledger account | Enter the number of the ledger account to use as the summary account for the cash account. |

### Set up number sequences for cash documents

To set up number sequences for cash documents, go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**. On the **Number sequence** tab, specify number sequence codes for the **Cash reimbursement slips**, **Cash disbursement slips**, **Cash correction voucher**, and **Exchange adjustment** documents, and for **Cash report number**.

### Set up default values for Cash and bank management parameters

To set up default values for Cash and bank management parameters for the petty cash functionality, go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**. On the **Cash** tab, enter the following information.

| Field | Description |
|---|---|
| Cash | Select the default cash account in journals. |
| Cash posting | Enter the default cash posting profile that is used if no other posting profile is specified. |
| Check for voucher used | Select what occurs if duplicate numbers are found during the check of the cash document number: Reject duplicate; Reject copies within fiscal year; Accept duplicates; Warn in case of duplicates |
| Check operations limit | Specify what occurs if the limit for operations with counteragents is exceeded: **Accept** – The limit can be exceeded. **Warning** – The limit can be exceeded, but the user receives a warning message. The operation is posted. **Error** – The limit can't be exceeded. The user receives an error message, and the operation isn't posted. |
| Validation method | Select the validation method that is used to control exceeded limit amounts for operations: **Operation** – Validation is done per transaction **Agreement** – Validation is done per transaction that has a specified contract with a counteragent. |
| Operations limit | Enter the maximum amount that is allowed for operations with counteragents in cash. |
| Posting on earlier date | Select this check box to enable cash transactions to be posted before the last date of the cash transaction. |
| Dimensions | Enter dimensions in the **Department code**, **Analytical code**, and **Purpose code** fields. The printing form for cash documents reflects this information. |
| Use confirm status | Select this check box to use an additional status, **Confirmed**, during the approval process for cash documents. (For more information, see the "Cash transaction approval and posting" section.) |

### Set up cash journal names in General ledger

To create a journal for cash transaction posting, go to **General ledger** > **Journal setup** > **Journal names**, and create a new record. In the **Journal type** field, enter **Cash**. Define other default journal parameters as needed.

## Daily cash operations via a Slip journal

To create a cash document through a Slip journal, go to **Cash and bank management** > **Cash transactions** > **Slip journal**, and create a new journal. On the Action Pane, select **Lines**. Add a new line, and enter the following information.

| Field | Description |
|---|---|
| Date | Enter the date of the transaction. |
| Account | Select the cash account. By default, a cash account is specified in the Cash and bank management parameters. |
| Description | Enter explanatory text for the transaction. |
| Debit Credit | Enter the cash document amount in one of these fields: **Debit** – Use this field to register cash receipts and a Cash reimbursement slip. **Credit** – Use this field to register cash expenditures and a Cash disbursement slip. |
| Offset account type Offset account | Select an offset account type and offset account number. |
| Currency | Select the code for the transaction currency. |
| Voucher | This field is filled in automatically, based on the journal setup. |
| Order number | If you don't set up another number sequence for the cash account, this field fills in automatically, based on the number sequence that you specify in the parameters. You can manually enter an order number in this field as you require. To prevent inconsistency in cash document numbering, the following control is applied: the number of a cash document that has an earlier date of operation can't be higher than number of a cash document that has a later date of operation. If you don't require this control, select the **Posting on earlier date** check box in the Cash and bank management parameters. |
| Approval status | The first transaction status is **None**. For information about how to set the transaction status, see the "Cash transaction approval and posting" section. |
| Document type | This field on the **Cash order** tab fills in automatically, based on the amount that you entered for the cash document: **Cash reimbursement slip** – This value is used if you entered an amount in the **Debit** field for the cash account. **Cash disbursement slip** – This value is used if you entered an amount in the **Credit** field for the cash account **Correction** – You entered a negative amount in either the **Debit** field or the **Credit** field for the cash account. |
| Sales tax group | Specify a sales tax group to calculate taxes on the operation. |
| Item sales tax group | Specify an item sales tax group to calculate taxes on the operation. |
| Reason | On the **Cash order** tab, enter text that describes the transaction subject. This text will be printed on the cash slip reporting form. |
| Document Date | Enter the description, number, and date of the primary document that is the reason for the transaction (for example, advance reports, invoice, or order). |
| Representative type | This field can have the following values: **Worker** – The **Representative** lookup contains a list of employees if the **Offset account** field is set to **Ledger** or **Bank**, or a list of the counteragent's contact persons if the **Offset account** field is set to **Customer** or **Vendor**. To set up representatives, go to **Basic** > **Setup** > **Contacts** > **Contact person**. **Other** – The **Representative** lookup contains a list of other clients. To set up receivers who don't appear in the **Customers** or **Vendors** table, go to **General ledger** > **Receivers**. This type is available only for Latvia. (The **CSELatvia** configuration key should be enabled.) **Vendor** – The **Representative** lookup contains a list of vendors. To set up vendors, go to **Accounts payable** > **Vendors**. **Customer** – The **Representative** lookup contains a list of customers. To set up customers, go to **Accounts receivable** > **Customers**. |
| Representative | Select a representative of the type that you specified in the **Representative type** field. |
| Name of person | This field fills in automatically, based on the **Offset account** and **Representative** fields. The printing form for cash slips reflects this information. |
| Identity card | This field fills in automatically, based on the identity card data for the contact person (representative). If the **Offset account type** field is set to **Advance holder**, and the **Offset account** field is set to an employee number, cash receipts or expenditures can be done from or to the employee. In this case the **Identity card** field fills in automatically by using data for the identity card from the **Employee** table (**Staff accounting** > **Employee table**). |
| Purpose | In the **Purpose** table, define one or more destination codes for the transaction amount. Select a destination code in the **Purpose** field, and enter an explanation in the **Transaction text** field. In the **Amount** field, enter an amount in the transaction currency. The **Percent** field shows, as a percentage, the ratio of the destination amount to the total transaction amount. |
| Remainder | The remaining amount that is calculated. You must assign the whole transaction amount to destination codes. |
| Officials | On the **Officials** tab, specify the names and titles for responsible persons: Director, Chief accountant, and Cashier. The **Position** values are determined by the setup of officials on the **General** and **Ledger** tabs of the **Officials** page (**Basic** > **Setup** > **Contacts** > **Officials**). |
| Prepayment | Select this check box if the transaction is a prepayment. |
| Posting profile | Enter the posting profile for the cash account. By default, the posting profile that is specified in the Cash and bank management parameters is used. |
| Offset posting profile | Enter the posting profile for the selected offset account. |
| Total amount | In the **Total amount** field group at the bottom of the page, the **Reimb** field shows the total that's calculated for all Cash reimbursement slips that you enter in the current journal, and the **Disb** field shows the total for all Cash disbursement slips. |

To check journal entries, on the Action Pane, select **Validate**.

## Daily cash operations via a General journal

To create a cash transaction through a general journal, go to **General ledger** > **Journal entries** > **General journals**, and create a new journal. On the action pane, select **Lines**. Add a new line, and enter the following information.

| Field | Description |
|---|---|
| Date | Enter the date of the transaction. |
| Account type | Select **Petty cash**. |
| Account | Select the cash account number. |
| Transaction text | Enter explanatory text for the transaction. |
| Debit Credit | Enter the cash document amount in one of these fields: **Debit** – Use this field to register cash receipts and a Cash reimbursement slip. **Credit** – Use this field to register cash expenditures and a Cash disbursement slip. |
| Offset account type Offset account | Select an offset account type and offset account number. |
| Currency | Select the code for the transaction currency. |

On the **Invoice** tab, you can specify posting profiles for the selected account and offset account. If the registered transaction is a prepayment, select the **Prepayment** check box on the **Payment** tab. In the **Representative** field group, fill in the fields as you did for the Slip journal lines to print on the **Cash** report. To check journal entries, on the action pane, select **Validate**.

## Cash transaction approval and posting

For cash transactions, you can apply the following statuses: **None**, **Confirmed**, **Approved**, and **Rejected**. The **Use confirm status** parameter on the **Approval** FastTab of the **Cash** tab at **Cash and bank management** > **Setup** > **Cash and bank management parameters** activates two additional statuses: **Confirmed** and **Rejected**. Use the **Confirmed** status when you issue cash documents and share cash receipts or expenditures between two employees: accountant and cashier. The **Reset status** function changes the current transaction status. **Approved** becomes **Confirmed**, and **Confirmed** becomes **None**. You can edit cash journal entries only when the status is **None**. You can reject cash transactions only if the transaction status is **Confirmed**. Rejected cash documents are included on the **Journal of registration of cash documents** report, but they aren't reflected on the **Cash book** report. To confirm a transaction, select the corresponding Slip journal line, and then select **Documents approval** > **Confirm**. An order number is generated, based on the specified number sequence. The transaction status changes to **Confirmed**, and you can no longer edit the journal line. The cash account balance remains unchanged. To reject a cash document, select **Documents approval** > **Reject**. This option is available only for documents that have **Confirmed** status. To approve a transaction, select the corresponding Slip journal line, and then select **Documents approval** > **Approve**. The **Approved** status indicates that cash funds are received or expended. The cash balance changes. You can post the cash transaction. To cancel an **Approved** status and reset the status to **None**, select **Documents approval** > **Reset status**. You can post only approved cash transactions. To post a journal, select **Post** > **Post**.

## Print a cash order

To print a cash order, select a Slip journal line, and then, on the action pane, select **Print** > **Cash order report**. The system generates a printing form for either a Cash reimbursement slip or a Cash disbursement slip, depending on whether you enter an amount in the **Debit** field or the **Credit** field for the selected line:

- If there's an amount in the **Debit** field: Cash reimbursement slip
- If there's an amount in the **Credit** field: Cash disbursement slip

You can print Slip journal lines that have **Confirmed**, **Approved**, or **Rejected** status. You can also print cash order documents at **Cash and bank management** > **Inquires and reports** > **Cash order**.

## Periodic tasks

Perform the following tasks at **Cash and bank management** > **Periodic tasks**.

| Periodic task | Description |
|---|---|
| Check balance limit | Check the balance for the selected cash account on the specified date, and show the result in an information message. Only approved transactions count in the balance calculation. Transactions that are marked as **For payroll** aren't considered. |
| Cash balance recalculation | Use this task to make sure that the ledger balances for cash accounts fit the cash balance. |
| Cash report creation (for Poland only) | Create a **Cash** report. The **Cash** report number is generated based on the number sequence that is set up for **Report number**. In the dialog box for the task, in the **To date**, specify the last date for which cash transactions should be counted for the **Cash** report. Use the **Filter** function on the **Records to include** tab to specify additional criteria to limit the selection of cash transactions. These criteria can include cash account numbers and currency codes. In the **Create by** field, select the user who is responsible for report creation. To view the **Cash** report that you created, use the **Cash reports** button on the **Cash accounts** page. |
| Cash - Exchange adjustment FIFO and LIFO (for Poland only) | Calculate the exchange adjustment per Polish standards. Use the **Filter** function on the **Records to include** tab to specify the cash account to run the task for. Select the **Recalculation** check box to do a full recalculation of the exchange adjustment difference for all open periods. Here's how the exchange adjustment is calculated when the first in, first out (FIFO) and last in, first out (LIFO) methods are used: **FIFO method** – The system searches for an expenditure transaction that has an earlier transaction date (smaller order number) and settles it with a receipt transaction that has an earlier transaction date (smaller order number). **LIFO method** – The system searches for an expenditure transaction that has a later transaction date (larger order number) and settles it with a receipt transaction that has a later transaction date (larger order number). The settled amount is reflected in the **Settled currency** field on the **Cash transaction** page. If there's an exchange adjustment difference, the amount is reflected in the **Exchange adjustment amount** field, and a transaction of the **Exchange rate difference** document type is generated in the **Cash transaction** table. Ledger accounts for profit or loss transactions are set in the **Currency** table (**Exchange rate financial profit** and **Exchange rate financial loss**). |
| Foreign currency revaluation - Cash | Use this task to have an adequate balance in the default currency on the reporting date when you enter the operations in foreign currencies. Use the **Filter** function on the **Records to include** tab to specify the cash account to run the task for. In the dialog box for the task, use the **From currency** and **To Currency** fields to specify transaction currencies. The system compares the amount in the currency that it converted by using exchange rate on the selected date with the amount in the default currency. The difference between the two amounts (excluding the previous exchange adjustment) is the calculated exchange adjustment. This task creates an approved cash transaction of the **Exchange adjustment** type. The ledger transaction is formed by using the ledger account for cash and the ledger account that is specified in **Unrealized profit** or **Unrealized loss** in the **Currency** table. |

## Inquiries and reports

| Inquiry or report                             | Description                                                                                                                                                                                                                     |
|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Cash transactions view                        | For a Slip journal line, use the **Inquiries** button on the Action Pane to view ledger transactions, the cash balance, and other information.                                                                                  |
| Cash transaction                              | Go to **Cash and bank management** > **Inquiries and reports** > **Cash transactions** to view cash transactions. Use the **Filter** function to specify additional criteria to limit the selection of cash transactions. |
| Journal of registration (for Estonia, Russia) | The report at **Cash and bank management** > **Inquiries and reports** > **Journal of registration** reflects all cash reimbursement and cash disbursement slips that you issued.                                   |
| Cash book (for Latvia, Lithuania, Russia)     | The report at **Cash and bank management** > **Inquiries and reports** > **Cash book report** reflects actual cash fund movements (receipts and expenditures).                                                            |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
