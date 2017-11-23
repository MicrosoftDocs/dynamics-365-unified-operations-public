---
# required metadata

title: Sales tax reports for Poland (setting up tax information and other features)
description: This topic provides information about Polish VAT reporting and the information that is legally required in VAT registers for Poland. 
author: ShylaThompson
manager: AnnBe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 274063
ms.search.region: Poland
# ms.search.industry: 
ms.author: shylaw
ms.dyn365.ops.version: AX 7.0.1
ms.search.validFrom: 2016-05-31

---

# Sales tax reports for Poland (setting up tax information and other features)
[!include[banner](../includes/banner.md)]

This topic provides information about Polish VAT reporting and the information that is legally required in VAT registers for Poland. 

## Poland - VAT report date codes

Per the Polish Accountancy Act, which took effect on September 29, 1994, value-added tax (VAT) for sales, purchases, and imported products must be processed separately. For every posted sales transaction or purchase transaction where the **Date of VAT register** or **VAT report date code** field is set, the tax will be accounted in relevant VAT registers. The **VAT report date code** field appears on several transaction pages. When you update or post transactions, information about the VAT report date code is posted to the tax tables. It will then be printed on the Polish VAT register. To set up VAT report date codes, open the **VAT report date codes** page (**Tax** &gt; **Setup** &gt; **Sales tax** &gt; **VAT report date codes**), and set the following fields.

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
<td>VAT report date code</td>
<td>Enter the VAT report date code.</td>
</tr>
<tr class="even">
<td>Description</td>
<td>Enter a description of the VAT report date code.</td>
</tr>
<tr class="odd">
<td>Include in VAT report</td>
<td>Select one of the following options:
<ul>
<li><strong>With VAT report date</strong> - The report shows the whole invoice amount if the calculated date in the <strong>Date of VAT register</strong> field on the <strong>Invoice posting</strong> page is in the date interval for the report.</li>
<li><strong>With VAT report date not later than</strong>  The report shows the whole invoice amount if the date in the <strong>Date of VAT register</strong> field is in the date interval for the report. The date is calculated based on the information in the <strong>Counted from</strong> and <strong>Number of days</strong> fields.</li>
<li><strong>With date of physical payment</strong> - If you select the <strong>Partial settlements</strong> check box, the report shows the settled part of the invoice amount if the reporting interval includes the payment dates. If the <strong>Partial settlements</strong> check box is cleared, the report doesn't show the invoice amount until the invoice is completely settled.</li>
<li><strong>With date of physical payment not later than</strong> - If you select the <strong>Partial settlements</strong> check box, the report shows settlements that occur in the date interval for the report. If the calculated value in the <strong>Date of VAT register</strong> field is in the date interval for the report, the report shows the whole invoice amount, except the settled amounts for the previous period. If the <strong>Partial settlements</strong> check box is cleared, select <strong>Transaction date</strong> or <strong>VAT date</strong> in the <strong>Counted from</strong> field to specify the criterion that is used to calculate the date of the VAT register.</li>
</ul></td>
</tr>
<tr class="even">
<td>Number of days</td>
<td>Enter the number of days after the VAT date register. This field is available only when the <strong>Include in VAT report</strong> field is set to either <strong>With VAT report date not later than</strong> or <strong>With date of physical payment not later than</strong>.</td>
</tr>
<tr class="odd">
<td>Counted from</td>
<td>Select one of the following options:
<ul>
<li>Transaction date</li>
<li>VAT date</li>
</ul></td>
</tr>
<tr class="even">
<td>Partial settlements</td>
<td>Select this check box to partially settle the payments. This check box is available only when the <strong>Include in VAT report</strong> field is set to either <strong>With date of physical payment</strong> or <strong>With date of physical payment not later than</strong>.</td>
</tr>
<tr class="odd">
<td>VAT date is the same as payment date</td>
<td>Select this check box to show the VAT report date code only if the date of payment for VAT is the same as the date in the VAT register.</td>
</tr>
</tbody>
</table>

The following pages include the VAT report date code.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Page</th>
<th>More information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Accounts payable parameters
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Setup</strong> &gt; <strong>Accounts</strong> <strong>payable</strong> <strong>parameters</strong>.</li>
</ul></td>
<td>On the <strong>General</strong> tab, on the <strong>Vendor</strong> FastTab, enter the VAT report date code that should be used as the default code for new vendors.</td>
</tr>
<tr class="even">
<td>Accounts receivable parameters
<ul>
<li>Click <strong>Accounts</strong> <strong>receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Accounts</strong> <strong>receivable</strong> <strong>parameters</strong>.</li>
</ul></td>
<td>On the <strong>General</strong> tab, on the <strong>Customer</strong> FastTab, enter the VAT report date code that should be used as the default code for new purchase orders.</td>
</tr>
<tr class="odd">
<td>Prepayment handling
<ol>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Vendor</strong> <strong>details</strong> &gt; <strong>Transactions</strong>. -or- Click <strong>Accounts receivable</strong> &gt; <strong>Customer</strong> <strong>details</strong> &gt; <strong>Transactions</strong>.</li>
<li>Select a prepayment transaction, and then click <strong>Prepayment handling</strong>.</li>
</ol></td>
<td>The <strong>VAT report date code</strong> field is visible if you selected <strong>Advanced</strong> in the <strong>Prepayment handling</strong> field on the <strong>Accounts payable parameters</strong> page or the <strong>Accounts receivable parameters</strong> page.</td>
</tr>
<tr class="even">
<td>Vendor invoice approval
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice approval journal</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Invoice pool
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice pool</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Vendor invoice register
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice register</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Vendor invoice journal
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice journal</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>All purchase orders
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Purchase orders</strong> &gt; <strong>All purchase orders</strong>.</li>
</ul></td>
<td>The VAT report date code is shown on the header.</td>
</tr>
<tr class="odd">
<td>Specification
<ul>
<li>Click <strong>Accounts payable</strong> &gt; <strong>Vendors</strong> &gt; <strong>All vendors</strong>. On the <strong>Invoice</strong> tab, in the <strong>Settle</strong> group, click <strong>Settle transactions</strong>. Click <strong>Inquiry</strong> &gt; <strong>Specifications</strong>, Then, on the <strong>Setup</strong> tab, in the <strong>View</strong> field, select <strong>Purchase</strong>. -or- Click <strong>Accounts receivable</strong> &gt; <strong>Customers</strong> &gt; <strong>All customers</strong>. On the <strong>Collect</strong> tab, in the <strong>Settle</strong> group, click <strong>Settle transactions</strong>. Click <strong>Inquiry</strong> &gt; <strong>Specifications</strong>. Then, on the <strong>Setup</strong> tab, in the <strong>View</strong> field, select <strong>Sales order</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Journal voucher
<ul>
<li>On the general journal, periodic journal, slip journal, or expense journal page, click <strong>Lines</strong>.</li>
</ul></td>
<td>Review the <strong>Invoice</strong> tab or the <strong>Payment</strong> tab. <strong>Note:</strong> For the expense journal, the <strong>Offset type account</strong> field should be set to <strong>Vendor</strong>.</td>
</tr>
<tr class="odd">
<td>Sales order
<ul>
<li>Click <strong>Accounts receivable</strong> &gt; <strong>Orders</strong> &gt; <strong>All sales orders</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Free text invoice
<ul>
<li>Click <strong>Accounts receivable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Free text invoices</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Posted sales tax
<ul>
<li>Click <strong>Tax</strong> &gt; <strong>Inquiries ad reports</strong> &gt; <strong>Sales tax inquiries</strong> &gt; <strong>Posted sales tax</strong>.</li>
</ul></td>
<td></td>
</tr>
</tbody>
</table>

## Poland - Name of services for VAT reporting
Service tariff numbers are required when you report information about VAT that involves a transaction with a party that isn't located in Poland. You set up service tariff numbers on the **Service tariff numbers** page. To set up service tariff numbers, click **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Service tariff number**, and set the following fields.

| Field                      | Description                                                                          |
|----------------------------|--------------------------------------------------------------------------------------|
| Service tariff number      | Enter the service tariff number that the government authority assigned to the party. |
| Service tariff description | Enter a description of the service tariff number.                                    |

You can also set a parameter to make the service tariff number mandatory. Click **Tax** &gt; **Sales tax** &gt; **Sales tax group**, and then, on the **General** FastTab, set the **Mandatory service tariff number** field. The **Mandatory service tariff number** parameter affects the following pages:

-   **All sales orders** (click **Accounts receivable** &gt; **Orders** &gt; **All sales orders**) (Header and lines)
-   **All free text invoices** (click **Accounts receivable** &gt; **Invoices**&gt; **All free text invoices**) (Header and lines)
-   **Voided sales orders** (click **Sales and marketing** &gt; **Inquiries and reports** &gt; **History** &gt; **Voided sales orders**, and then click **Show**)

The following shared functionality works on all the preceding pages:

-   When you create a new line, the service tariff number is copied from the header to the line.
-   If the **Mandatory service tariff number** parameter is enabled on the sales tax group, the invoice is stopped, and you receive an error message.
-   When you post an invoice, sales tax transactions are split by service tariff number. Even the sales tax group and item sales tax group are the same.
-   When you create a credit note for any posted invoice where the lines have a value in the **Service tariff number** field, the service tariff number is copied to credit note lines from the original document, not from the credit note header. The service tariff number can be edited on for the correction line.

## Poland - Base amount for VAT
The **Base amount for VAT** field is enabled when you enter a tax transaction (the **Tax code** field has a value on journal lines) in the following journals:

-   Invoice journal (click **Accounts payable** &gt; **Journals** &gt; **Invoices** &gt; **Invoice journal**, click **Lines**, and then click the **General** tab)
-   General journal (click **General ledger** &gt; **Journals** &gt; **General journal**, click **Lines**, and then click the **General** tab)
-   Slip journal (click **Cash and bank management** &gt; **Cash transactions** &gt; **Slip journal**, click **Lines**, and then click the **General** tab)

In the **Base amount for VAT** field, you manually enter the tax base amount. After you post a journal, the value from the **Base amount for VAT** field transferred to **the Amount origin** field in tax transactions.

## Poland - Sales tax (VAT) reporting
This feature is used in ledger journals where multiple lines have the same voucher. When the following fields on one line are changed, a message box appears that lets you update the fields on other lines that have the same voucher:

-   Invoice
-   Document date
-   Address
-   Tax exempt number
-   Customer/ Vendor
-   Date of VAT register
-   VAT report date code

> [!NOTE]
> The message box appears only when the fields were changed for a line where a sales tax group, item sales tax group, and sales tax code are set up. The message is triggered on the following journal pages:

-   General journal (click **General ledger** &gt; **Journals** &gt; **General journal**, and then click **Lines**)
-   Invoice journal (click **Accounts payable** &gt; **Journals** &gt; **Invoices** &gt; **Invoice journal**, and then click **Lines**)

## Poland - Tax direction for the line
The feature is related to postings through the general journal that involves sales tax transactions. The system automatically determines the sales tax direction that should be assigned to tax transactions that are created, based on the account type that was used for the posting. This feature enables main accounts to be determined correctly and the sales tax direction to be assigned correctly for general journal lines within the same voucher. Lines must meet one of the following conditions:

-   The account type is **Customer**, **Vendor**, or **Petty cash**, and the offset account type is **Ledger**. The offset account must be specified.
-   The account type is **Ledger**, and the offset account type is **Customer**, **Vendor**, or **Petty cash**. The offset account must be specified.

For general journal lines that meet the preceding conditions, the system assigns a separate sales tax direction, as follows:

-   **Sales tax payable** for the **Customer** account type
-   **Sales tax receivable** for the **Vendor** account type
-   **Sales tax payable** for the **Petty cash** account type

### Example

You create the following general journal lines.

| Account type | Account number | Debit | Credit | Offset account type | Offset account number | Sales tax posting group | Item sales tax posting group |
|--------------|----------------|-------|--------|---------------------|-----------------------|-------------------------|------------------------------|
| Customer     | 1101           |       | 800    | Ledger              | 0101                  | AR-DOM                  | FULL                         |
| Vendor       | 1001           |       | 800    | Ledger              | 0101                  | AR-DOM                  | FULL                         |
| Ledger       | 0102           | 700   |        |                     |                       | AR-DOM                  | FULL                         |
| Ledger       | 0103           |       | 700    |                     |                       | AR-DOM                  | FULL                         |

Here are the results of the posting:

-   Line 1 has a tax transaction that has a sales tax direction of **Sales tax payable**.
-   Line 2 has a tax transaction that has a sales tax direction of **Sales tax receivable**.
-   Line 3 has a tax transaction that has a sales tax direction of **Sales tax receivable**.
-   Line 4 has a tax transaction that has a sales tax direction of **Sales tax payable**.

## Poland - SSRS VAT register report
The **VAT register** report is considered the main tax summary document. The VAT statement is prepared based on this report. It's the main tax reporting audit document in every Polish company. The VAT for sales, purchases, and imported products must be processed separately. The legislation also defines several official reports for VAT and conditions for transactions that must be included on the reports. The **VAT register** report is a basic document that is used in Polish accounting as the basis for reporting taxes to the tax authorities. The VAT registers are printed regularly for reporting periods. (They are usually printed every month.) The reports must be printed on paper, and they must be signed by one or more authorities, such as a chief accountant or a CFO. They are used as the basis for the monthly VAT 7 tax declaration. You can access **VAT register** reports from several places:

-   Tax &gt; Inquiries and reports &gt; Sales tax reports &gt; EU summary VAT register
-   Tax &gt; Inquiries and reports &gt; Sales tax reports &gt; Purchase VAT register
-   Tax &gt; Inquiries and reports &gt; Sales tax reports &gt; Sales VAT register

## Poland - Allowance for Bad Debts
Polish value-added tax (VAT) law regulations among others apply to situations where unpaid invoices occur and VAT adjustments are required. The regulations are following:

-	On the creditor side, it is possible to correct output VAT on unpaid invoices (receivables) under following conditions:
	- Delivery of goods or services was provided to an active VAT taxpayer.
	- Debtor, on the day before submission VAT statement in which bad debt allowance will be used is an active VAT taxpayer, has not been the subject of bankruptcy or liquidation.
	- Receivable is not overdue more than 2 years.

-	Correction of output VAT can be done for period, in which receivable is proofed to be irrecoverable, which is meant as not paid within 150 days from original due date (It was neither sold nor paid).
-	On the debtor side, debtor is obliged to correct input VAT in period, in which passed 150 days from purchase invoice original due date for payables, which are not paid. This is unconditional requirement. It means that debtor is obliged to do correction, even if debtor did not used possibilities of allowance for bad debt. 
If an invoice was paid (or receivable was sold by creditor) after allowance for bad debts was used, allowance should be reversed in VAT statement for the period in which the invoice was paid (or receivable was sold by creditor). If the payment was partial, reversal should be done partly (proportionally to original invoice amount).
The accountant working with Account Payable or Account Receivable must identify periodically bad debts. The debts get bad when the invoices are not paid more than 150 days but less than 2 years later than the planned due date. 
The incoming and outgoing VAT may and should be corrected (reversed) for the identified debts but the final decision is up to the accountant. It means that the accountant can manually exclude some invoices identified automatically.
If the debts are paid in the next accounting period, the VAT will have to be be reversed back proportionally to the payment sum.

Periodical procedure identifies the bad debts based on the vendor's or customer's open transactions and settlements from one side and on the payment schedule from the other side. 
The VAT in identified debt sum is allocated between the VAT codes in invoice lines to be reversed.
The sums of settled payments are also allocated in the same manner to the VAT codes in invoice lines to be reversed back. 
The journals may be cancelled starting from the last one if there is a mistake. The transactions will be reversed.
The allocation of VAT sums happened by posting.
General ledger (GL) accounts for VAT correction posting and periods for bad debts must be set up.

To use that functionality, you need to configure system. These are the main configuration areas:
 
Complete Overdue debt journal calculation setup in **General ledger > Journal setup > Overdue debt journal calculation**. The available journal type options are following:

 - Customer VAT journal
 - Vendor VAT journal

You have to set up for each journal following information:
-	**Minimum number of days**: Minimum period that invoice is overdue, it is usually 150 days.
-	**Maximum number of days**: Maximum period that invoice will not be considered as overdue, it is usually 2 years – 720 days.
-	**Calculation type** field: Defines date for each overdue to be calculated. Available values are Due date and Invoice date.
-	**Validate** option. If the check box is selected, it validates that transactions do not change balance on date of last posted journal.
**Note**: The Condition and the Payment term dates should remain empty.

In the parameters for the Accounts Receivable module and the Accounts Payable module, on the **Number sequences** tab, two number sequence references must be set up:
Journal number for overdue debt VAT
Overdue debt VAT journal

Specify the general ledger accounts for the **Offset Reversed Incoming Tax** and the **Offset Reversed Outgoing Tax** in Tax > Setup > Sales tax > Ledger posting group


Once you have system configured to working with overdue debts you use the **Overdue debt VAT** periodic function in the accounts receivable and the accounts payable modules to manage your overdue debts. 

You can perform following actions in the form:

 - **Create** a journal. You set up the date on which debt amount will be calculated. Interval of dates will be calculated automatically based on setup in the Overdue journal calculation settings.
**Note**: When you create a journal, all overdue unpaid invoices for journal periods are automatically included. It also includes invoices for which payments were processed in that period. Information will be available in the **Paid amount** and the **Paid tax amount** fields.
You can click on a journal number to open journal details and review tabs:
	 - **Overdue debt VAT journal header** (you can change the view between Lines and Header)
	 - **Overdue debt VAT journal lines** including information about customer's or vendor's invoices that contain bad debts classified in reporting period. The **Exclude** check box allows you to exclude any invoice from journal that you don’t want to process. If any part of that invoice is already processed (VAT refund is finished), such an invoice cannot be excluded. Totals amounts that are presented in the columns are reflected on the header of the form. The amounts are recalculated when filtering the lines. 
	 - **Line details** – showing customer or vendor account, transaction and overdue debt amount details.
 - **Post** a journal. It allows you to create VAT reverse transaction for invoices that are included in the journal. Posted journal can be cancelled.
 - **Cancel** posted journal. The Cancel function is available only for the last journal. During cancelation you can select the type of correction transaction, either correction or reverse. There is a Correction check box in the dialog to indicate your choice.
 - Review **vouchers** – View voucher transactions that are created during post or cancelation.
 - Review **Posted sales tax** – View posted sales tax transactions that are allocated into tax codes from invoices.
 - Open **counting** – View the summary information for customer or vendors, and their invoices included in the journal.

The Fact boxes pane displays amounts for all invoices that contain bad debts and are not paid until the end of reporting period. There are overdue amount and overdue tax amount there as well.


