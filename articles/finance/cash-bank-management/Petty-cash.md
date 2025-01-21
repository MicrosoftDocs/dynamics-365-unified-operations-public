---
title: Petty cash
description: Learn about the global petty cash functionality that is available in all countries, including prerequisites and processes for setting up accounts.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 01/18/2024
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


You can use the petty cash functionality to automate the receipt and expenditure of cash, the creation of primary documents, and the printing of related reports. 

Petty cash performs the following actions:

- Account the receipt and expenditure of available cash assets.
- Generate typical cash forms. Examples include cash reimbursement slips, cash disbursement slips, and the journal of registration for cash slips.
- Control the maximum cash amount that's allowed for customers or vendors.
- Reflect cash operations in various currencies.
- Convert the amounts of cash operations in foreign currency to the default currency to provide accounting reporting.

## Prerequisites

Before you can use the petty cash functionality, the following prerequisites must be in place:

- Enable petty cash.
- Set up the following items:

    - Cash accounts
    - Cash posting profiles
    - Number sequences for cash document numbering
    - Default values for Cash and bank management parameters
    - Cash journal names in General ledger

### Enable petty cash

To enable petty cash, follow these steps.

1. In Feature management, enable the **Petty cash** feature.
2. Go to **Cash and bank management parameters** \> **Cash**, and select the **Enable petty cash** option.

### Set up cash accounts

To set up the cash accounts, follow these steps.

1. Go to **Cash and bank management** &gt; **Petty cash** &gt; **Cash accounts**.
2. Enter the following information.

    | Field                 | Description |
    |-----------------------|-------------|
    | Cash                  | Enter a code to identify the cash account (cash). |
    | Name                  | Enter a description of the cash account. |
    | Currency              | Select the default currency code for cash transactions. |
    | Number sequence group | If the numbering of cash documents differs from the numbering that's specified in the parameters, enter a code. |
    | More currencies       | Select this checkbox to allow currencies that differ from the accounting currency to be posted. |
    | Negative cash         | Select this checkbox to allow negative cash balances in any currency. |

To set up cash balance control rules for a cash account, follow these steps.

1. Select the cash account.
2. On the **Cash account** tab, in the **Balance limit** section, select **Balance limit**, and then enter the following information.

    <table>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Currency type</td>
    <td><p>Select the type of currency:</p>
    <ul>
    <li><strong>Accounting currency</strong> – Use the basic company currency code.</li>
    <li><strong>Indicated currency</strong> – Use a currency code that differs from the basic company currency code.</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Currency</td>
    <td>If you selected <strong>Indicated currency</strong> in the <strong>Currency type</strong> field, select a currency code. This field is unavailable if you selected <strong>Accounting currency</strong> in the <strong>Currency type</strong> field.</td>
    </tr>
    <tr class="odd">
    <td>Balance limit type</td>
    <td><p>Select the type of balance limit:</p>
    <ul>
    <li><strong>Maximum</strong> – The cash balance shouldn't exceed the <strong>Balance limit</strong> amount for the cash account (upper bound).</li>
    <li><strong>Minimum</strong> – The cash balance shouldn't be less than the <strong>Balance limit</strong> amount for the cash account (lower bound).</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Check balance limit</td>
    <td><p>Select what occurs during the approval process for cash documents if the <strong>Balance limit</strong> amount for the cash account is exceeded:</p>
    <ul>
    <li><strong>Accept</strong> – The limit can be exceeded.</li>
    <li><strong>Warning</strong> – The limit can be exceeded, but the user receives a warning message. The cash document is confirmed or approved.</li>
    <li><strong>Error</strong> – The limit can't be exceeded, and the user receives an error message. The cash document isn't confirmed or approved.</li>
    </ul>
    <p>For more information about the approval process for cash documents, see the <a href="#cash-transaction-approval-and-posting">Cash transaction approval and posting</a> section later in this article.</p></td>
    </tr>
    <tr class="odd">
    <td>Balance limit</td>
    <td>Enter a limit for the cash account balance. The amount should be in the specified currency.</td>
    </tr>
    </tbody>
    </table>

### Set up cash posting profiles

Cash posting profiles define postings to the general ledger. To set up a cash posting profile, follow these steps.

1. Go to **Cash** **and bank management** \> **Setup** \> **Cash posting profiles**.
2. Select or create a posting profile, and enter the following information.

    <table>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Valid for</td>
    <td><p>Select whether the posting profile applies to a specific cash account or all cash accounts:</p>
    <ul>
    <li><strong>Table</strong> – If there's a posting profile line for the cash account, that line is used for cash transaction posting.</li>
    <li><strong>All</strong> – There's no posting profile line for the cash account.</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Cash</td>
    <td>If you selected <strong>Table</strong> in the <strong>Valid for</strong> field, specify the cash account. This field remains blank if you selected <strong>All</strong> in the <strong>Valid for</strong> field.</td>
    </tr>
    <tr class="odd">
    <td>Main account</td>
    <td>Enter the number of the main account to use as the summary account for the cash account.</td>
    </tr>
    </tbody>
    </table>

### Set up number sequences for cash documents

To set up number sequences for cash documents, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank management parameters**.
2. On the **Number sequence** tab, specify number sequence codes for the **Cash reimbursement slips**, **Cash disbursement slips**, **Cash correction voucher**, and **Exchange adjustment** references.

### Set up default values for Cash and bank management parameters

To set up default values for Cash and bank management parameters for petty cash, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank management parameters**.
2. On the **Cash** tab, enter the following information.

    <table>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Cash</td>
    <td>Select the default cash account in journals.</td>
    </tr>
    <tr class="even">
    <td>Cash posting</td>
    <td>Enter the default cash posting profile that's used if no other posting profile is specified.</td>
    </tr>
    <tr class="odd">
    <td>Check for voucher used</td>
    <td><p>Select what occurs if duplicate numbers are found during the check of the cash document number:</p>
    <ul>
    <li>Reject duplicate</li>
    <li>Reject copies within fiscal year</li>
    <li>Accept duplicates</li>
    <li>Warn in case of duplicates</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Check operations limit</td>
    <td><p>Select what occurs if the limit for operations with counteragents is exceeded:</p>
    <ul>
    <li><strong>Accept</strong> – The limit can be exceeded.</li>
    <li><strong>Warning</strong> – The limit can be exceeded, but the user receives a warning message. The operation is posted.</li>
    <li><strong>Error</strong> – The limit can't be exceeded, and the user receives an error message. The operation isn't posted.</li>
    </ul></td>
    </tr>
    <tr class="odd">
    <td>Validation method</td>
    <td><p>Select the validation method that's used to control exceeded limit amounts for operations:</p>
    <ul>
    <li><strong>Operation</strong> – Validation is done per transaction.</li>
    <li><strong>Agreement</strong> – Validation is done per transaction that has a specified contract with a counteragent.</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Operations limit</td>
    <td>Enter the maximum amount that's allowed for operations with counteragents in cash.</td>
    </tr>
    <tr class="odd">
    <td>Posting on earlier date</td>
    <td>Select this checkbox to allow cash transactions to be posted before the last date of the cash transaction.</td>
    </tr>
    <tr class="even">
    <td>Dimensions</td>
    <td>Enter dimensions in the <strong>Department code</strong>, <strong>Analytical code</strong>, and <strong>Purpose code</strong> fields. The printing page for cash documents reflects this information.</td>
    </tr>
    <tr class="odd">
    <td>Use confirm status</td>
    <td>Select this checkbox to use an additional status, <strong>Confirmed</strong>, during the approval process for cash documents. </td>
    </tr>
    </tbody>
    </table>

### Set up cash journal names in General ledger

To create a journal for cash transaction posting, follow these steps.

1. Go to **General ledger** \> **Journal setup** \> **Journal names**, and create a record.
2. In the **Journal type** field, specify **Cash**. Define other default journal parameters as needed.

## Daily cash operations via a Slip journal

To create a cash document via a Slip journal, follow these steps.

1. Go to **Cash and bank management** \> **Petty cash** \> **Slip journal**, and create a journal.
2. On the Action Pane, select **Lines**.
3. Add a line, and enter the following information.

    <table>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Date</td>
    <td>Enter the date of the transaction.</td>
    </tr>
    <tr class="even">
    <td>Account</td>
    <td>Select the cash account. By default, a cash account is specified in Cash and bank management parameters.</td>
    </tr>
    <tr class="odd">
    <td>Description</td>
    <td>Enter text for the transaction.</td>
    </tr>
    <tr class="even">
    <td>Debit, Credit</td>
    <td><p>Enter the cash document amount in one of these fields:</p>
    <ul>
    <li><strong>Debit</strong> – Use this field to register cash receipts and a Cash reimbursement slip.</li>
    <li><strong>Credit</strong> – Use this field to register cash expenditures and a Cash disbursement slip.</li>
    </ul></td>
    </tr>
    <tr class="odd">
    <td>Offset account type, Offset account</td>
    <td>Select an offset account type and an offset account number.</td>
    </tr>
    <tr class="even">
    <td>Currency</td>
    <td>Select the transaction currency code.</td>
    </tr>
    <tr class="odd">
    <td>Voucher</td>
    <td>This field is set based on the journal setup.</td>
    </tr>
    <tr class="even">
    <td>Order number</td>
    <td>If no number sequence is set up for the cash account, this field is automatically set based on the number sequence that's specified in the parameters. You can manually enter an order number in this field. To help prevent inconsistent cash document numbering, the following control is applied: the number of a cash document that has an earlier date of operation can't be higher than number of a cash document that has a later date of operation. If you don't need this control, select the <strong>Posting on earlier date</strong> checkbox in Cash and bank management parameters.</td>
    </tr>
    <tr class="odd">
    <td>Approval status</td>
    <td>The first transaction status is <strong>None</strong>. For information about how to set the transaction status, see the <a href="#cash-transaction-approval-and-posting">Cash transaction approval and posting</a> section.</td>
    </tr>
    <tr class="even">
    <td>Document type</td>
    <td><p>This field on the <strong>Cash order</strong> tab is automatically set based on the amount that you entered for the cash document:</p>
    <ul>
    <li><strong>Cash reimbursement slip</strong> – You entered an amount in the <strong>Debit</strong> field for the cash account.</li>
    <li><strong>Cash disbursement slip</strong> – You entered an amount in the <strong>Credit</strong> field for the cash account.</li>
    <li><strong>Correction</strong> – You entered a negative amount in either the <strong>Debit</strong> field or the <strong>Credit</strong> field for the cash account.</li>
    </ul></td>
    </tr>
    <tr class="odd">
    <td>Sales tax group</td>
    <td>Specify a sales tax group to calculate taxes on the operation.</td>
    </tr>
    <tr class="even">
    <td>Item sales tax group</td>
    <td>Specify an item sales tax group to calculate taxes on the operation.</td>
    </tr>
    <tr class="odd">
    <td>Reason</td>
    <td>In this field on the <strong>Cash order</strong> tab, enter text to describe the transaction subject. This text is printed on the cash slip reporting page.</td>
    </tr>
    <tr class="even">
    <td>Document date</td>
    <td>Enter the description, number, and date of the primary document that's the reason for the transaction (for example, advance reports, invoice, or order).</td>
    </tr>
    <tr class="odd">
    <td>Representative type</td>
    <td><p>This field can have the following values:</p>
    <ul>
    <li><strong>Worker</strong> – If the <strong>Offset account</strong> field is set to <strong>Ledger</strong> or <strong>Bank</strong>, the <strong>Representative</strong> lookup contains a list of employees. If the <strong>Offset account</strong> field is set to <strong>Customer</strong> or <strong>Vendor</strong>, the <strong>Representative</strong> lookup contains a list of the counteragent contact persons. To set up representatives, go to <strong>Basic</strong> &gt; <strong>Setup</strong> &gt; <strong>Contacts</strong> &gt; <strong>Contact person</strong>.</li>
    <li><p><strong>Other</strong> – The <strong>Representative</strong> lookup contains a list of other clients. To set up receivers who don't appear in the <strong>Customers</strong> or <strong>Vendors</strong> table, go to <strong>General ledger</strong> &gt; <strong>Receivers</strong>.</p><p><strong>Note:</strong> This representative type is available only for Latvia. (The <strong>CSELatvia</strong> configuration key should be enabled.)</p></li>
    <li><strong>Vendor</strong> – The <strong>Representative</strong> lookup contains a list of vendors. To set up vendors, go to <strong>Accounts payable</strong> &gt; <strong>Vendors</strong>.</li>
    <li><strong>Customer</strong> – The <strong>Representative</strong> lookup contains a list of customers. To set up customers, go to <strong>Accounts receivable</strong> &gt; <strong>Customers</strong>.</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Representative</td>
    <td>Select a representative of the type that you specified in the <strong>Representative type</strong> field.</td>
    </tr>
    <tr class="odd">
    <td>Name of person</td>
    <td>This field is automatically set based on the <strong>Offset account</strong> and <strong>Representative</strong> values. The printing page for cash slips reflects this information.</td>
    </tr>
    <tr class="even">
    <td>Remainder</td>
    <td>The remaining amount that's calculated. Note that the whole transaction amount must be assigned to destination codes.</td>
    </tr>
    <tr class="odd">
    <td>Posting profile</td>
    <td>Enter the posting profile for the cash account. By default, the posting profile that's specified in Cash and bank management parameters is used.</td>
    </tr>
    <tr class="even">
    <td>Offset posting profile</td>
    <td>Enter the posting profile for the selected offset account.</td>
    </tr>
    <tr class="odd">
    <td>Total amount</td>
    <td>In the <strong>Total amount</strong> section at the bottom of the page, the <strong>Reimb</strong> field shows the total that's calculated for all Cash reimbursement slips that are entered in the current journal. The <strong>Disb</strong> field shows the total for all Cash disbursement slips.</td>
    </tr>
    </tbody>
    </table>

To review journal entries, on the Action Pane, select **Validate**.

## Daily cash operations via a General journal

To create a cash transaction via a General journal, follow these steps.

1. Go to **General ledger** \> **Journal entries** \> **General journals**, and create a journal.
2. On the Action Pane, select **Lines**.
3. Add a line, and enter the following information.

    <table>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Date</td>
    <td>Enter the date of the transaction.</td>
    </tr>
    <tr class="even">
    <td>Account type</td>
    <td>Select <strong>Petty cash</strong>.</td>
    </tr>
    <tr class="odd">
    <td>Account</td>
    <td>Select the cash account number.</td>
    </tr>
    <tr class="even">
    <td>Transaction text</td>
    <td>Enter explanatory text for the transaction.</td>
    </tr>
    <tr class="odd">
    <td>Debit, Credit</td>
    <td><p>Enter the cash document amount in one of these fields:</p>
    <ul>
    <li><strong>Debit</strong> – Use this field to register cash receipts and a Cash reimbursement slip.</li>
    <li><strong>Credit</strong> – Use this field to register cash expenditures and a Cash disbursement slip.</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Offset account type, Offset account</td>
    <td>Select an offset account type and an offset account number.</td>
    </tr>
    <tr class="odd">
    <td>Currency</td>
    <td>Select the code for the transaction currency.</td>
    </tr>
    </tbody>
    </table>

On the **Invoice** tab, specify posting profiles for the selected account and offset account. If the registered transaction is a prepayment, on the **Payment** tab, select the **Prepayment** checkbox. In the **Representative** section, set the fields to print on the **Cash** report. To review journal entries, on the Action Pane, select **Validate**.

## Cash transaction approval and posting

For cash transactions, the following statuses can be applied: 

- None
- Confirmed
- Approved
- Rejected

A **Use confirm status** parameter is available on the **Approval** FastTab of the **Cash** tab. Go to **Cash and bank management** \> **Setup** \> **Cash and bank management parameters** to activate two additional statuses: **Confirmed** and **Rejected**. 

Confirmation is appropriate when cash documents are issued, and cash receipts or expenditures are shared between two employees: an accountant and a cashier. The **Reset status** function changes the current transaction status. **Approved** becomes **Confirmed**, and **Confirmed** becomes **None**. Cash journal entries can be edited only when the status is **None**. Cash transactions can be rejected only when the transaction status is **Confirmed**. 

- To confirm a transaction, select the corresponding Slip journal line, and then select **Documents approval** \> **Confirm**. An order number is generated based on the specified number sequence. The transaction status is changed to **Confirmed**, and you can no longer edit the journal line. The cash account balance remains unchanged.
- To reject a cash document, select **Documents approval** \> **Reject**. This option is available only for documents that have **Confirmed** status.
- To approve a transaction, select the corresponding Slip journal line, and then select **Documents approval** \> **Approve**. The **Approved** status indicates that cash funds are received or expended. The cash balance is changed. The cash transaction can be posted.
- To cancel an **Approved** status and reset the status to **None**, select **Documents approval** \> **Reset status**. Only approved cash transactions can be posted. To post a journal, select **Post** \> **Post**.
- Journals with **Rejected** documents can be posted, but will not generate vouchers for these transactions. However, all rejected documents are logged and available to be reviewed in the **Cash transactions** page.
  
## Periodic tasks

To complete the following tasks, go to **Cash and bank management** \> **Periodic tasks**.

| Periodic task                       | Description |
|-------------------------------------|-------------|
| Check balance limit                 | Check the balance for the selected cash account on the specified date, and show the result in an information message. Only approved transactions can be counted in the balance calculation. |
| Cash balance recalculation          | Use this task to confirm that the ledger balances for cash accounts fit the cash balance. |
| Foreign currency revaluation - Cash | Use this task to ensure that you have an adequate balance in the default currency on the reporting date when the operations are entered in foreign currencies. Use the **Filter** function on the **Records to include** tab to specify the cash account to run the task for. In the dialog box for the task, use the **From currency** and **To Currency** fields to specify transaction currencies. The system compares the amount in the currency that was converted by using the exchange rate on the selected date with the amount in the default currency. The difference between the two amounts (excluding the previous exchange adjustment) is the calculated exchange adjustment. This task creates an approved cash transaction of the **Exchange adjustment** type. The ledger transaction is created by using the ledger account for cash that's specified in the **Unrealized profit** or **Unrealized loss** field in the **Currency** table. |

## Inquiries and reports

| Inquiry or report            | Description |
|------------------------------|-------------|
| Cash transactions            | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash transactions** to view cash transactions. Use the **Filter** function to specify additional criteria to limit the selection of cash transactions. |
| Cash balance                 | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash balance** to view the cash balance. |
| Cash - Ledger reconciliation | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** \> **Cash - Ledger reconciliation** to run this report. |
| Cash statement report        | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** \> **Cash statement report** to run this report. |
| Cash transaction report      | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** \> **Cash transactions report** to run this report. |
