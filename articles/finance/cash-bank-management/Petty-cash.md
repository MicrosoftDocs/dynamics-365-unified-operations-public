---
title: Petty cash
description: Learn about the global petty cash functionality that is available in all countries, including prerequisites and processes for setting up accounts.
author: music727
ms.author: mibeinar
ms.topic: article
ms.date: 06/04/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-01-29
ms.search.form: 
ms.dyn365.ops.version:
---

# Petty cash

[!include [banner](../../includes/banner.md)]

This article provides information about the petty cash functionality that extends existing localization features as a global feature for all countries and regions. For more information, see [Petty cash for Eastern Europe and Russia](../localizations/europe/emea-petty-cash.md).

Use the petty cash functionality to automate the receipt and expenditure of cash, the creation of primary documents, and the printing of related reports.

Petty cash performs the following actions:

- Accounts for the receipt and expenditure of available cash assets.
- Generates typical cash forms. Examples include cash reimbursement slips, cash disbursement slips, and the journal of registration for cash slips.
- Controls the maximum cash amount that's allowed for customers or vendors.
- Reflects cash operations in various currencies.
- Converts the amounts of cash operations in foreign currency to the default currency to provide accounting reporting.

## Prerequisites

Before you can use the petty cash functionality, ensure the following prerequisites are in place:

- Enable petty cash.
- Set up the following items:

  - Cash accounts
  - Cash posting profiles
  - Number sequences for cash document numbering
  - Default values for Cash and bank management parameters
  - Cash journal names in General ledger

### Enable petty cash

To enable petty cash, follow these steps:

1. In Feature management, enable the **Petty cash** feature.
1. Go to **Cash and bank management parameters** > **Cash**, and select the **Enable petty cash** option.

### Set up cash accounts

To set up the cash accounts, follow these steps:

1. Go to **Cash and bank management** > **Petty cash** > **Cash accounts**.
1. Enter the following information.

    | Field                 | Description |
    |-----------------------|-------------|
    | Cash                  | Enter a code to identify the cash account (cash). |
    | Name                  | Enter a description of the cash account. |
    | Currency              | Select the default currency code for cash transactions. |
    | Number sequence group | If the numbering of cash documents differs from the numbering that's specified in the parameters, enter a code. |
    | More currencies       | Select this checkbox to allow currencies that differ from the accounting currency to be posted. |
    | Negative cash         | Select this checkbox to allow negative cash balances in any currency. |

To set up cash balance control rules for a cash account, follow these steps:

1. Select the cash account.
1. On the **Cash account** tab, in the **Balance limit** section, select **Balance limit**, and then enter the following information.

    | Field | Description |
    |-------|-------------|
    | Currency type | Select the type of currency:<br>- **Accounting currency** – Use the basic company currency code.<br>- **Indicated currency** – Use a currency code that differs from the basic company currency code. |
    | Currency | If you selected **Indicated currency** in the **Currency type** field, select a currency code. This field is unavailable if you selected **Accounting currency** in the **Currency type** field. |
    | Balance limit type | Select the type of balance limit:<br>- **Maximum** – The cash balance shouldn't exceed the **Balance limit** amount for the cash account (upper bound).<br>- **Minimum** – The cash balance shouldn't be less than the **Balance limit** amount for the cash account (lower bound). |
    | Check balance limit | Select what occurs during the approval process for cash documents if the **Balance limit** amount for the cash account is exceeded:<br>- **Accept** – The limit can be exceeded.<br>- **Warning** – The limit can be exceeded, but the user receives a warning message. The cash document is confirmed or approved.<br>- **Error** – The limit can't be exceeded, and the user receives an error message. The cash document isn't confirmed or approved.<br><br>For more information about the approval process for cash documents, see the [Cash transaction approval and posting](#cash-transaction-approval-and-posting) section later in this article. |
    | Balance limit | Enter a limit for the cash account balance. The amount should be in the specified currency. |

### Set up cash posting profiles

Cash posting profiles define postings to the general ledger. To set up a cash posting profile, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Cash posting profiles**.
1. Select or create a posting profile, and enter the following information.

    | Field | Description |
    |-------|-------------|
    | Valid for | Select if the posting profile applies to a specific cash account or all cash accounts:<br>- **Table** – If there's a posting profile line for the cash account, the system uses that line for cash transaction posting.<br>- **All** – There's no posting profile line for the cash account. |
    | Cash | If you selected **Table** in the **Valid for** field, specify the cash account. This field remains blank if you selected **All** in the **Valid for** field. |
    | Main account | Enter the number of the main account to use as the summary account for the cash account. |

### Set up number sequences for cash documents

To set up number sequences for cash documents, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**.
1. On the **Number sequence** tab, specify number sequence codes for the **Cash reimbursement slips**, **Cash disbursement slips**, **Cash correction voucher**, and **Exchange adjustment** references.

### Set up default values for Cash and bank management parameters

To set up default values for Cash and bank management parameters for petty cash, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Cash and bank management parameters**.
1. On the **Cash** tab, enter the following information.

    | Field | Description |
    |-------|-------------|
    | Cash | Select the default cash account in journals. |
    | Cash posting | Enter the default cash posting profile that's used if no other posting profile is specified. |
    | Check for voucher used | Select what occurs if duplicate numbers are found during the check of the cash document number:<br>- Reject duplicate<br>- Reject copies within fiscal year<br>- Accept duplicates<br>- Warn in case of duplicates |
    | Check operations limit | Select what occurs if the limit for operations with counteragents is exceeded:<br>- **Accept** – The limit can be exceeded.<br>- **Warning** – The limit can be exceeded, but the user receives a warning message. The operation is posted.<br>- **Error** – The limit can't be exceeded, and the user receives an error message. The operation isn't posted. |
    | Validation method | Select the validation method that's used to control exceeded limit amounts for operations:<br>- **Operation** – Validation is done per transaction.<br>- **Agreement** – Validation is done per transaction that has a specified contract with a counteragent. |
    | Operations limit | Enter the maximum amount that's allowed for operations with counteragents in cash. |
    | Posting on earlier date | Select this checkbox to allow cash transactions to be posted before the last date of the cash transaction. |
    | Dimensions | Enter dimensions in the **Department code**, **Analytical code**, and **Purpose code** fields. The printing page for cash documents reflects this information. |
    | Use confirm status | Select this checkbox to use an additional status, **Confirmed**, during the approval process for cash documents. |

### Set up cash journal names in General ledger

To create a journal for cash transaction posting, follow these steps:

1. Go to **General ledger** > **Journal setup** > **Journal names**, and create a record.
1. In the **Journal type** field, specify **Cash**. Define other default journal parameters as needed.

## Daily cash operations via a Slip journal

To create a cash document through a Slip journal, follow these steps:

1. Go to **Cash and bank management** > **Petty cash** > **Slip journal**, and create a journal.
1. On the Action Pane, select **Lines**.
1. Add a line, and enter the following information.

    | Field | Description |
    |-------|-------------|
    | Date | Enter the date of the transaction. |
    | Account | Select the cash account. By default, a cash account is specified in Cash and bank management parameters. |
    | Description | Enter text for the transaction. |
    | Debit, Credit | Enter the cash document amount in one of these fields:<br>- **Debit** – Use this field to register cash receipts and a Cash reimbursement slip.<br>- **Credit** – Use this field to register cash expenditures and a Cash disbursement slip. |
    | Offset account type, Offset account | Select an offset account type and an offset account number. |
    | Currency | Select the transaction currency code. |
    | Voucher | This field is set based on the journal setup. |
    | Order number | If you don't set up a number sequence for the cash account, the system automatically sets this field based on the number sequence that you specify in the parameters. You can manually enter an order number in this field. To help prevent inconsistent cash document numbering, the following control is applied: the number of a cash document that has an earlier date of operation can't be higher than number of a cash document that has a later date of operation. If you don't need this control, select the **Posting on earlier date** checkbox in Cash and bank management parameters. |
    | Approval status | The first transaction status is **None**. For information about how to set the transaction status, see the [Cash transaction approval and posting](#cash-transaction-approval-and-posting) section. |
    | Document type | This field on the **Cash order** tab is automatically set based on the amount that you entered for the cash document:<br>- **Cash reimbursement slip** – You entered an amount in the **Debit** field for the cash account.<br>- **Cash disbursement slip** – You entered an amount in the **Credit** field for the cash account.<br>- **Correction** – You entered a negative amount in either the **Debit** field or the **Credit** field for the cash account. |
    | Sales tax group | Specify a sales tax group to calculate taxes on the operation. |
    | Item sales tax group | Specify an item sales tax group to calculate taxes on the operation. |
    | Reason | In this field on the **Cash order** tab, enter text to describe the transaction subject. This text is printed on the cash slip reporting page. |
    | Document date | Enter the description, number, and date of the primary document that's the reason for the transaction (for example, advance reports, invoice, or order). |
    | Representative type | This field can have the following values:<br>- **Worker** – If the **Offset account** field is set to **Ledger** or **Bank**, the **Representative** lookup contains a list of employees. If the **Offset account** field is set to **Customer** or **Vendor**, the **Representative** lookup contains a list of the counteragent contact persons. To set up representatives, go to **Basic** > **Setup** > **Contacts** > **Contact person**.<br>- **Other** – The **Representative** lookup contains a list of other clients. To set up receivers who don't appear in the **Customers** or **Vendors** table, go to **General ledger** > **Receivers**.<br><br>  **Note:** This representative type is available only for Latvia. (The **CSELatvia** configuration key should be enabled.)<br>- **Vendor** – The **Representative** lookup contains a list of vendors. To set up vendors, go to **Accounts payable** > **Vendors**.<br>- **Customer** – The **Representative** lookup contains a list of customers. To set up customers, go to **Accounts receivable** > **Customers**. |
    | Representative | Select a representative of the type that you specified in the **Representative type** field. |
    | Name of person | This field is automatically set based on the **Offset account** and **Representative** values. The printing page for cash slips reflects this information. |
    | Remainder | The remaining amount that's calculated. Note that the whole transaction amount must be assigned to destination codes. |
    | Posting profile | Enter the posting profile for the cash account. By default, the posting profile that's specified in Cash and bank management parameters is used. |
    | Offset posting profile | Enter the posting profile for the selected offset account. |
    | Total amount | In the **Total amount** section at the bottom of the page, the **Reimb** field shows the total that's calculated for all Cash reimbursement slips that are entered in the current journal. The **Disb** field shows the total for all Cash disbursement slips. |

To review journal entries, on the Action Pane, select **Validate**.

## Daily cash operations through a general journal

To create a cash transaction through a general journal, follow these steps:

1. Go to **General ledger** > **Journal entries** > **General journals**, and create a journal.
1. On the Action Pane, select **Lines**.
1. Add a line, and enter the following information.

    | Field | Description |
    |-------|-------------|
    | Date | Enter the date of the transaction. |
    | Account type | Select **Petty cash**. |
    | Account | Select the cash account number. |
    | Transaction text | Enter explanatory text for the transaction. |
    | Debit, Credit | Enter the cash document amount in one of these fields:<br>- **Debit** – Use this field to register cash receipts and a Cash reimbursement slip.<br>- **Credit** – Use this field to register cash expenditures and a Cash disbursement slip. |
    | Offset account type, Offset account | Select an offset account type and an offset account number. |
    | Currency | Select the code for the transaction currency. |

On the **Invoice** tab, specify posting profiles for the selected account and offset account. If the registered transaction is a prepayment, on the **Payment** tab, select the **Prepayment** checkbox. In the **Representative** section, set the fields to print on the **Cash** report. To review journal entries, on the Action Pane, select **Validate**.

## Cash transaction approval and posting

For cash transactions, apply the following statuses:

- None
- Confirmed
- Approved
- Rejected

The **Approval** FastTab of the **Cash** tab includes a **Use confirm status** parameter. Go to **Cash and bank management** > **Setup** > **Cash and bank management parameters** to activate two additional statuses: **Confirmed** and **Rejected**.

Use the **Confirmed** status when two employees share cash receipts or expenditures - an accountant and a cashier. The **Reset status** function changes the current transaction status. **Approved** becomes **Confirmed**, and **Confirmed** becomes **None**. You can edit cash journal entries only when the status is **None**. You can reject cash transactions only when the transaction status is **Confirmed**.

- To confirm a transaction, select the corresponding Slip journal line, and then select **Documents approval** > **Confirm**. An order number is generated based on the specified number sequence. The transaction status changes to **Confirmed**, and you can no longer edit the journal line. The cash account balance remains unchanged.
- To reject a cash document, select **Documents approval** > **Reject**. This option is available only for documents that have **Confirmed** status.
- To approve a transaction, select the corresponding Slip journal line, and then select **Documents approval** > **Approve**. The **Approved** status indicates that cash funds are received or expended. The cash balance changes. The cash transaction can be posted.
- To cancel an **Approved** status and reset the status to **None**, select **Documents approval** > **Reset status**. Only approved cash transactions can be posted. To post a journal, select **Post** > **Post**.
- Journals with **Rejected** documents can be posted, but won't generate vouchers for these transactions. All rejected documents are logged and available to be reviewed on the **Cash transactions** page.
  
## Periodic tasks

To complete the following tasks, go to **Cash and bank management** > **Periodic tasks**.

| Periodic task                       | Description |
|-------------------------------------|-------------|
| Check balance limit                 | Check the balance for the selected cash account on the specified date, and show the result in an information message. Only approved transactions count in the balance calculation. |
| Cash balance recalculation          | Use this task to confirm that the ledger balances for cash accounts fit the cash balance. |
| Foreign currency revaluation - Cash | Use this task to ensure that you have an adequate balance in the default currency on the reporting date when the operations are entered in foreign currencies. Use the **Filter** function on the **Records to include** tab to specify the cash account to run the task for. In the dialog box for the task, use the **From currency** and **To Currency** fields to specify transaction currencies. The system compares the amount in the currency that was converted by using the exchange rate on the selected date with the amount in the default currency. The difference between the two amounts (excluding the previous exchange adjustment) is the calculated exchange adjustment. This task creates an approved cash transaction of the **Exchange adjustment** type. The ledger transaction is created by using the ledger account for cash that's specified in the **Unrealized profit** or **Unrealized loss** field in the **Currency** table. |

## Inquiries and reports

| Inquiry or report            | Description |
|------------------------------|-------------|
| Cash transactions            | Go to **Cash and bank management** > **Inquiries and reports** > **Cash transactions** to view cash transactions. Use the **Filter** function to specify additional criteria to limit the selection of cash transactions. |
| Cash balance                 | Go to **Cash and bank management** > **Inquiries and reports** > **Cash balance** to view the cash balance. |
| Cash - Ledger reconciliation | Go to **Cash and bank management** > **Inquiries and reports** > **Cash reports** > **Cash - Ledger reconciliation** to run this report. |
| Cash statement report        | Go to **Cash and bank management** > **Inquiries and reports** > **Cash reports** > **Cash statement report** to run this report. |
| Cash transaction report      | Go to **Cash and bank management** > **Inquiries and reports** > **Cash reports** > **Cash transactions report** to run this report. |
