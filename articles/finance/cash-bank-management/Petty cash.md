---
title: Petty cash
description: This article provides information about the global petty cash functionality that is available in all countries.
author: EricWang
ms.date: 01/08/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: 
ms.author: wangchen
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 
ms.custom: 
ms.search.form:  
---

# Petty cash 

[!include [banner](../../includes/banner.md)]

This article provides information about the petty cash functionality that extends existing localization feature [Petty cash for Eastern Europe and Russia - Finance | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/europe/emea-petty-cash) as a global feature for all countries in the system.

You can use the petty cash functionality to automate operations for receipts and expenditures of cash, the creation of primary documents, and the printing of related reports. The petty cash functionality lets you perform the following operations:

-   Account the receipt and expenditure of available cash assets.
-   Generate typical cash forms: Cash reimbursement slips, Cash disbursement slips, and a Journal of registration for cash slips.
-   Control the maximum cash amount that is allowed for operations with customers, vendors, and so on.
-   Reflect cash operations in various currencies in the system.
-   Convert the amounts of cash operations in foreign currency to the default currency to provide accounting reporting.

## Prerequisites
Before you can use the petty cash functionality, you must complete the following prerequisites:

-   Enable petty cash
-   Set up cash accounts.
-   Set up cash posting profiles.
-   Set up number sequences for cash document numbering.
-   Set up default values for Cash and bank management parameters.
-   Set up cash journal names in General ledger.

### Enable petty cash

- Turn on feature **Petty cash** in feature management workspace.

- Turn on parameter **Enable petty cash** in **Cash and bank management parameters > Cash**

### Set up cash accounts

To set up a Cash, open **Cash and bank management** &gt; **Petty cash** &gt; **Cash accounts**, and enter the following information.

| Field                 | Description                                                                                                          |
|-----------------------|----------------------------------------------------------------------------------------------------------------------|
| Cash                  | Enter a code to identify the cash account (cash).                                                                    |
| Name                  | Enter a description of the cash account.                                                                             |
| Currency              | Select the default currency code for cash transactions.                                                              |
| Number sequence group | If the numbering of cash documents must differ from the numbering that is specified in the parameters, enter a code. |
| More currencies       | Select this check box to allow currencies that differ from the accounting currency to be posted.                     |
| Negative cash         | Select this check box to allow negative cash balances in any currency.                                               |

To set up cash balance control rules for a cash account, select the cash account, and then, on the Action Pane, on the **Cash account** tab, in the **Balance limit** group, click **Balance limit**. Enter the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Currency type</td>
<td>Select the type of currency:
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
<td>Select one of the available values:
<ul>
<li><strong>Maximum</strong> – The cash balance should not be allowed to exceed the <strong>Balance limit</strong> amount for the cash account (upper bound).</li>
<li><strong>Minimum</strong> – The cash balance should not be allowed to go below the <strong>Balance limit</strong> amount for the cash account (bottom bound).</li>
</ul></td>
</tr>
<tr class="even">
<td>Check balance limit</td>
<td>Select what occurs during the approval process for cash documents if the <strong>Balance limit</strong> amount for the cash account is exceeded:
<ul>
<li><strong>Accept</strong> – The limit can be exceeded.</li>
<li><strong>Warning</strong> – The limit can be exceeded, but the user receives a warning message. The cash document is confirmed or approved.</li>
<li><strong>Error</strong> – The limit can&#39;t be exceeded. The user receives an error message, and the cash document isn&#39;t confirmed or approved.</li>
</ul>
For more information about the approval process for cash documents, see the &quot;Cash transaction approval and posting&quot; section, later in this article.</td>
</tr>
<tr class="odd">
<td>Balance limit</td>
<td>Enter a limit for the cash account balance. The amount should be in the currency that you specified.</td>
</tr>
</tbody>
</table>

### Set up cash posting profiles

Cash posting profiles define postings to the general ledger. To set up a cash posting profile, go to **Cash** **and bank management** &gt; **Setup** &gt; **Cash posting profiles**, and select or create a posting profile. Enter the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Valid for</td>
<td>Select whether the posting profile applies to a specific cash account or all cash accounts:
<ul>
<li><strong>Table</strong> – If there is a posting profile line for the cash account, that line is used for cash transaction posting.</li>
<li><strong>All</strong> – There is no posting profile line for the cash account.</li>
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

To set up number sequences for cash documents, go to **Cash and bank management** &gt; **Setup** &gt; **Cash and bank management parameters**. On the **Number sequence** tab, specify number sequence codes for the **Cash reimbursement slips**, **Cash disbursement slips**, **Cash correction voucher**, and **Exchange adjustment** documents.

### Set up default values for Cash and bank management parameters

To set up default values for Cash and bank management parameters for the petty cash functionality, go to **Cash and bank management** &gt; **Setup** &gt; **Cash and bank management parameters**. On the **Cash** tab, enter the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
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
<td>Enter the default cash posting profile that is used if no other posting profile is specified.</td>
</tr>
<tr class="odd">
<td>Check for voucher used</td>
<td>Select what occurs if duplicate numbers are found during the check of the cash document number:
<ul>
<li>Reject duplicate</li>
<li>Reject copies within fiscal year</li>
<li>Accept duplicates</li>
<li>Warn in case of duplicates</li>
</ul></td>
</tr>
<tr class="even">
<td>Check operations limit</td>
<td>Specify what occurs if the limit for operations with counteragents is exceeded:
<ul>
<li><strong>Accept</strong> – The limit can be exceeded.</li>
<li><strong>Warning</strong> – The limit can be exceeded, but the user receives a warning message. The operation is posted.</li>
<li><strong>Error</strong> – The limit can&#39;t be exceeded. The user receives an error message, and the operation isn&#39;t posted.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Validation method</td>
<td>Select the validation method that is used to control exceeded limit amounts for operations:
<ul>
<li><strong>Operation</strong> – Validation is done per transaction</li>
<li><strong>Agreement</strong> – Validation is done per transaction that has a specified contract with a counteragent.</li>
</ul></td>
</tr>
<tr class="even">
<td>Operations limit</td>
<td>Enter the maximum amount that is allowed for operations with counteragents in cash.</td>
</tr>
<tr class="odd">
<td>Posting on earlier date</td>
<td>Select this check box to enable cash transactions to be posted before the last date of the cash transaction.</td>
</tr>
<tr class="even">
<td>Dimensions</td>
<td>Enter dimensions in the <strong>Department code</strong>, <strong>Analytical code</strong>, and <strong>Purpose code</strong> fields. The printing form for cash documents will reflect this information.</td>
</tr>
<tr class="odd">
<td>Use confirm status</td>
<td>Select this check box to use an additional status, <strong>Confirmed</strong>, during the approval process for cash documents. </td>
</tr>
</tbody>
</table>


### Set up cash journal names in General ledger

To create a journal for cash transaction posting, go to **General ledger** &gt; **Journal setup** &gt; **Journal names**, and create a new record. In the **Journal type** field, specify **Cash**. Define other default journal parameters as you require.

## Daily cash operations via a Slip journal
To create a cash document via a Slip journal, go to **Cash and bank management** &gt; **Petty cash** &gt; **Slip journal**, and create a new journal. On the Action Pane, click **Lines**. Add a new line, and enter the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
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
<td>Select the cash account. By default, a cash account is specified in the Cash and bank management parameters.</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Enter explanatory text for the transaction.</td>
</tr>
<tr class="even">
<td>Debit Credit</td>
<td>Enter cash document amount in one of these fields:
<ul>
<li><strong>Debit</strong> – Use this field to register cash receipts and a Cash reimbursement slip.</li>
<li><strong>Credit</strong> – Use this field to register cash expenditures and a Cash disbursement slip.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Offset account type Offset account</td>
<td>Select an offset account type and offset account number.</td>
</tr>
<tr class="even">
<td>Currency</td>
<td>Select the code for the transaction currency.</td>
</tr>
<tr class="odd">
<td>Voucher</td>
<td>This field is filled in automatically, based on the journal setup.</td>
</tr>
<tr class="even">
<td>Order number</td>
<td>If no other number sequence is set up for the cash account, this field is filled in automatically, based on the number sequence that is specified in the parameters. You can manually enter an order number in this field as you require. To prevent inconsistence in cash document numbering, the following control is applied: the number of a cash document that has an earlier date of operation can&#39;t be higher than number of a cash document that has a later date of operation. If you don&#39;t require this control, select the <strong>Posting on earlier date</strong> check box in the Cash and bank management parameters.</td>
</tr>
<tr class="odd">
<td>Approval status</td>
<td>The first transaction status is <strong>None</strong>. For information about how to set the transaction status, See the &quot;Cash transaction approval and posting&quot; section.</td>
</tr>
<tr class="even">
<td>Document type</td>
<td>This field on the <strong>Cash order</strong> tab is filled in automatically, based on the amount that you entered for the cash document:
<ul>
<li><strong>Cash reimbursement slip</strong> – This value is used if you entered an amount in the <strong>Debit</strong> field for the cash account.</li>
<li><strong>Cash disbursement slip</strong> – This value is used if you entered an amount in the <strong>Credit</strong> field for the cash account</li>
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
<td>On the <strong>Cash order</strong> tab, enter text that describes the transaction subject. This text will be printed on the cash slip reporting form.</td>
</tr>
<tr class="even">
<td>Document Date</td>
<td>Enter the description, number, and date of the primary document that is the reason for the transaction (for example, advance reports, invoice, or order).</td>
</tr>
<tr class="odd">
<td>Representative type</td>
<td>This field can have the following values:
<ul>
<li><strong>Worker</strong> – The <strong>Representative</strong> lookup contains a list of employees if the <strong>Offset account</strong> field is set to <strong>Ledger</strong> or <strong>Bank</strong>, or a list of the counteragent&#39;s contact persons if the <strong>Offset account</strong> field is set to <strong>Customer</strong> or <strong>Vendor</strong>. To set up representatives, go to <strong>Basic</strong> &gt; <strong>Setup</strong> &gt; <strong>Contacts</strong> &gt; <strong>Contact person</strong>.</li>
<li><strong>Other</strong> – The <strong>Representative</strong> lookup contains a list of other clients. To set up receivers who don&#39;t appear in the <strong>Customers</strong> or <strong>Vendors</strong> table, go to <strong>General ledger</strong> &gt; <strong>Receivers</strong>. This type is available only for Latvia. (The <strong>CSELatvia</strong> configuration key should be enabled.)</li>
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
<td>This field is filled in automatically, based on the <strong>Offset account</strong> and <strong>Representative</strong> fields. The printing form for cash slips will reflect this information.</td>
</tr>
<tr class="even">
<td>Remainder</td>
<td>The remaining amount that is calculated. Note that the whole transaction amount must be assigned to destination codes.</td>
</tr>
<tr class="odd">
<td>Posting profile</td>
<td>Enter the posting profile for the cash account. By default, the posting profile that is specified in the Cash and bank management parameters is used.</td>
</tr>
<tr class="even">
<td>Offset posting profile</td>
<td>Enter the posting profile for the selected offset account.</td>
</tr>
<tr class="odd">
<td>Total amount</td>
<td>In the <strong>Total amount</strong> field group at the bottom of the page, the <strong>Reimb</strong> field shows the total that is calculated for all Cash reimbursement slips that are entered in the current journal, and the <strong>Disb</strong> field shows the total for all Cash disbursement slips.</td>
</tr>
</tbody>
</table>

To check journal entries, on the Action Pane, click **Validate**.

## Daily cash operations via a General journal
To create a cash transaction via a General journal, go to **General ledger** &gt; **Journal entries** &gt; **General journals**, and create a new journal. On the Action Pane, click **Lines**. Add a new line, and enter the following information.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
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
<td>Debit Credit</td>
<td>Enter cash document amount in one of these fields:
<ul>
<li><strong>Debit</strong> – Use this field to register cash receipts and a Cash reimbursement slip.</li>
<li><strong>Credit</strong> – Use this field to register cash expenditures and a Cash disbursement slip.</li>
</ul></td>
</tr>
<tr class="even">
<td>Offset account type Offset account</td>
<td>Select an offset account type and offset account number.</td>
</tr>
<tr class="odd">
<td>Currency</td>
<td>Select the code for the transaction currency.</td>
</tr>
</tbody>
</table>

On the **Invoice** tab, you can specify posting profiles for the selected account and offset account. If the registered transaction is a prepayment, select the **Prepayment** check box on the **Payment** tab. In the **Representative** field group, fill in the fields as you did for the Slip journal lines to print on the **Cash** report. To check journal entries, on the Action Pane, click **Validate**.

## Cash transaction approval and posting
For cash transactions, the following statuses can be applied: 

- None
- Confirmed
- Approved
- Rejected

A **Use confirm status** parameter on the **Approval** FastTab of the **Cash** tab at **Cash and bank management** &gt; **Setup** &gt; **Cash and bank management parameters** lets you activate two additional statuses: **Confirmed** and **Rejected**. Confirmation is appropriate when cash documents are issued, and cash receipts or expenditures are shared between two employees: accountant and cashier. The **Reset status** function changes the current transaction status. **Approved** becomes **Confirmed**, and **Confirmed** becomes **None**. Cash journal entries can be edited only when the status is **None**. Cash transactions can be rejected only if the transaction status is **Confirmed**. To confirm a transaction, select the corresponding Slip journal line, and then click **Documents approval** &gt; **Confirm**. An order number is generated, based on the specified number sequence. The transaction status is changed to **Confirmed**, and you can no longer edit the journal line. The cash account balance remains unchanged. To reject a cash document, click **Documents approval** &gt; **Reject**. This option is available only for documents that have **Confirmed** status. To approve a transaction, select the corresponding Slip journal line, and then click **Documents approval** &gt; **Approve**. The **Approved** status indicates that cash funds are received or expended. The cash balance is changed. The cash transaction can be posted. To cancel an **Approved** status and reset the status to **None**, click **Documents approval** &gt; **Reset status**. Only approved cash transactions can be posted. To post a journal, click **Post** &gt; **Post**.



## Periodic tasks
The following tasks can be performed at **Cash and bank management** &gt; **Periodic tasks**.

| Periodic task                       | Description                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| Check balance limit                 | Check the balance for the selected cash account on the specified date, and show the result in an information message. Only approved transactions can be counted in the balance calculation. |
| Cash balance recalculation          | Use this task to make sure that the ledger balances for cash accounts fit the cash balance. |
| Foreign currency revaluation - Cash | Use this task to have an adequate balance in the default currency on the reporting date when the operations are entered in foreign currencies. Use the Filter function on the Records to include tab to specify the cash account to run the task for. In the dialog box for the task, use the From currency and To Currency fields to specify transaction currencies. The system compares the amount in the currency that was converted by using exchange rate on the selected date with the amount in the default currency. The difference between the two amounts (excluding the previous exchange adjustment) is the calculated exchange adjustment. This task creates an approved cash transaction of the Exchange adjustment type. The ledger transaction is formed by using the ledger account for cash and the ledger account that is specified in Unrealized profit or Unrealized loss in the Currency table. |




## Inquiries and reports

| Inquiry or report            | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| Cash transactions            | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash transactions** to view cash transactions. Use the **Filter** function to specify additional criteria to limit the selection of cash transactions. |
| Cash balance                 | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash balance** to view cash balance. |
| Cash - Ledger reconciliation | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** > **Cash - Ledger reconciliation** to run this report. |
| Cash statement report        | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** > **Cash statement report** to run this report. |
| Cash transaction report      | Go to **Cash and bank management** &gt; **Inquiries and reports** &gt; **Cash reports** > **Cash transactions report** to run this report. |

