---
title: Sales tax reports for Poland
description: This article provides information about Polish VAT reporting and the information that is legally required in VAT registers for Poland.
author: mrolecki
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Poland
ms.author: mrolecki
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.custom: 274063
---

# Sales tax reports for Poland
[!include [banner](../includes/banner.md)]

This article provides information about Polish value-added tax (VAT) reporting and the information that is legally required in VAT registers for Poland.

## VAT report date codes

Per the Polish Accountancy Act, which took effect on September 29, 1994, VAT for sales, purchases, and imported products must be processed separately. For every posted sales transaction or purchase transaction where the **Date of VAT register** or **VAT report date code** field is set, the tax is accounted in relevant VAT registers. The **VAT report date code** field appears on several transaction pages. When you update or post transactions, information about the VAT report date code is posted to the tax tables. It will then be printed on the Polish VAT register.

To set up VAT report date codes, set the following fields on the **VAT report date codes** page (**Tax** &gt; **Setup** &gt; **Sales tax** &gt; **VAT report date codes**).

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
<li><strong>With VAT report date</strong> – The report shows the whole invoice amount if the calculated date in the <strong>Date of VAT register</strong> field on the <strong>Invoice posting</strong> page is in the date interval for the report.</li>
<li><strong>With VAT report date not later than</strong> – The report shows the whole invoice amount if the date in the <strong>Date of VAT register</strong> field is in the date interval for the report. The date is calculated based on the information in the <strong>Counted from</strong> and <strong>Number of days</strong> fields.</li>
<li><strong>With date of physical payment</strong> – If you select the <strong>Partial settlements</strong> check box, the report shows the settled part of the invoice amount if the reporting interval includes the payment dates. If the <strong>Partial settlements</strong> check box is cleared, the report doesn&#39;t show the invoice amount until the invoice is completely settled.</li>
<li><strong>With date of physical payment not later than</strong> – If you select the <strong>Partial settlements</strong> check box, the report shows settlements that occur in the date interval for the report. If the calculated value in the <strong>Date of VAT register</strong> field is in the date interval for the report, the report shows the whole invoice amount, except the settled amounts for the previous period. If the <strong>Partial settlements</strong> check box is cleared, select <strong>Transaction date</strong> or <strong>VAT date</strong> in the <strong>Counted from</strong> field to specify the criterion that is used to calculate the date of the VAT register.</li>
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
<li>Select <strong>Accounts payable</strong> &gt; <strong>Setup</strong> &gt; <strong>Accounts payable parameters</strong>.</li>
</ul></td>
<td>On the <strong>General</strong> tab, on the <strong>Vendor</strong> FastTab, enter the VAT report date code that should be used as the default code for new vendors.</td>
</tr>
<tr class="even">
<td>Accounts receivable parameters
<ul>
<li>Select <strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Accounts receivable parameters</strong>.</li>
</ul></td>
<td>On the <strong>General</strong> tab, on the <strong>Customer</strong> FastTab, enter the VAT report date code that should be used as the default code for new purchase orders.</td>
</tr>
<tr class="odd">
<td>Prepayment handling
<ol>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Vendor details</strong> &gt; <strong>Transactions</strong>.<br>
–or–<br>
Select <strong>Accounts receivable</strong> &gt; <strong>Customer details</strong> &gt; <strong>Transactions</strong>.</li>
<li>Select a prepayment transaction, and then select <strong>Prepayment handling</strong>.</li>
</ol></td>
<td>The <strong>VAT report date code</strong> field is visible if you selected <strong>Advanced</strong> in the <strong>Prepayment handling</strong> field on the <strong>Accounts payable parameters</strong> or <strong>Accounts receivable parameters</strong> page.</td>
</tr>
<tr class="even">
<td>Vendor invoice approval
<ul>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice approval journal</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Invoice pool
<ul>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice pool</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Vendor invoice register
<ul>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice register</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Vendor invoice journal
<ul>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Invoice journal</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>All purchase orders
<ul>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Purchase orders</strong> &gt; <strong>All purchase orders</strong>.</li>
</ul></td>
<td>The VAT report date code is shown on the header.</td>
</tr>
<tr class="odd">
<td>Specification
<ol>
<li>Select <strong>Accounts payable</strong> &gt; <strong>Vendors</strong> &gt; <strong>All vendors</strong>.</li>
<li>On the <strong>Invoice</strong> tab, in the <strong>Settle</strong> group, select <strong>Settle transactions</strong>.</li>
<li>Select <strong>Inquiry</strong> &gt; <strong>Specifications</strong>, and then, on the <strong>Setup</strong> tab, in the <strong>View</strong> field, select <strong>Purchase</strong>.</li>
</ol>
<p>–or–</p>
<ol>
<li>Select <strong>Accounts receivable</strong> &gt; <strong>Customers</strong> &gt; <strong>All customers</strong>.</li>
<li>On the <strong>Collect</strong> tab, in the <strong>Settle</strong> group, select <strong>Settle transactions</strong>.</li>
<li>Select <strong>Inquiry</strong> &gt; <strong>Specifications</strong>, and then, on the <strong>Setup</strong> tab, in the <strong>View</strong> field, select <strong>Sales order</strong>.</li>
</ol></td>
<td></td>
</tr>
<tr class="even">
<td>Journal voucher
<ul>
<li>On the general journal, periodic journal, slip journal, or expense journal page, select <strong>Lines</strong>.</li>
</ul></td>
<td>Review the <strong>Invoice</strong> or <strong>Payment</strong> tab.<strong>NOTE:</strong><br>For the expense journal, the <strong>Offset type account</strong> field should be set to <strong>Vendor</strong>.</td>
</tr>
<tr class="odd">
<td>Sales order
<ul>
<li>Select <strong>Accounts receivable</strong> &gt; <strong>Orders</strong> &gt; <strong>All sales orders</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="even">
<td>Free text invoice
<ul>
<li>Select <strong>Accounts receivable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Free text invoices</strong>.</li>
</ul></td>
<td></td>
</tr>
<tr class="odd">
<td>Posted sales tax
<ul>
<li>Select <strong>Tax</strong> &gt; <strong>Inquiries ad reports</strong> &gt; <strong>Sales tax inquiries</strong> &gt; <strong>Posted sales tax</strong>.</li>
</ul></td>
<td></td>
</tr>
</tbody>
</table>

## Name of services for VAT reporting

Service tariff numbers are required when you report information about VAT that involves a transaction with a party that isn't in Poland. You set up service tariff numbers on the **Service tariff numbers** page. To set up service tariff numbers, select **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Service tariff number**, and then set the following fields.

| Field                      | Description                                                                          |
|----------------------------|--------------------------------------------------------------------------------------|
| Service tariff number      | Enter the service tariff number that the government authority assigned to the party. |
| Service tariff description | Enter a description of the service tariff number.                                    |

You can also make the service tariff number mandatory. Select **Tax** &gt; **Sales tax** &gt; **Sales tax group**, and then, on the **General** FastTab, set the **Mandatory service tariff number** field. The **Mandatory service tariff number** parameter affects the following pages:

- Header and lines on the **All sales orders** page (Select **Accounts receivable** &gt; **Orders** &gt; **All sales orders**.)
- Header and lines on the **All free text invoices** page (Select **Accounts receivable** &gt; **Invoices**&gt; **All free text invoices**.)
- **Voided sales orders** page (Select **Sales and marketing** &gt; **Inquiries and reports** &gt; **History** &gt; **Voided sales orders**, and then select **Show**.)

The following shared functionality works on all the preceding pages:

- When you create a line, the service tariff number is copied from the header to the line.
- If the **Mandatory service tariff number** parameter is enabled on the sales tax group, the invoice is stopped, and you receive an error message.
- When you post an invoice, sales tax transactions are split by service tariff number. The sales tax group and item sales tax group are the same.
- When you create a credit note for any posted invoice where the lines have a value in the **Service tariff number** field, the service tariff number is copied to the credit note lines from the original document, not from the credit note header. The service tariff number can be edited on the correction line.

## Base amount for VAT

The **Base amount for VAT** field is enabled when you enter a tax transaction in the following journals. (Tax transactions are transactions where the **Tax code** field on journal lines has a value.)

- Invoice journal (Select **Accounts payable** &gt; **Journals** &gt; **Invoices** &gt; **Invoice journal**, select **Lines**, and then select the **General** tab.)
- General journal (Select **General ledger** &gt; **Journals** &gt; **General journal**, select **Lines**, and then select the **General** tab.)
- Slip journal (Select **Cash and bank management** &gt; **Cash transactions** &gt; **Slip journal**, select **Lines**, and then select the **General** tab.)

In the **Base amount for VAT** field, you manually enter the tax base amount. After you post a journal, the value from the **Base amount for VAT** field is transferred to the **Amount origin** field in tax transactions.

## Sales tax (VAT) reporting

The sales tax (VAT reporting) feature is used in ledger journals where multiple lines have the same voucher. When the following fields are changed on one line, a message box appears that lets you update the fields on other lines that have the same voucher:

- Invoice
- Document date
- Address
- Tax exempt number
- Customer/ Vendor
- Date of VAT register
- VAT report date code

> [!NOTE]
> The message box appears only when the fields are changed for a line where a sales tax group, item sales tax group, and sales tax code are set up. The message box is triggered on the following journal pages:
>
> - General journal (Select **General ledger** &gt; **Journals** &gt; **General journal**, and then select **Lines**.)
> - Invoice journal (Select **Accounts payable** &gt; **Journals** &gt; **Invoices** &gt; **Invoice journal**, and then select **Lines**.)

## Tax direction for the line

The sales tax direction feature is related to postings that are done through the general journal that involves sales tax transactions. Based on the account type that was used for the posting, the system automatically determines the sales tax direction that should be assigned to tax transactions that are created. This feature helps guarantee that main accounts are determined correctly and that the sales tax direction is assigned correctly for general journal lines in the same voucher. Lines must meet one of the following conditions:

- The account type is **Customer**, **Vendor**, or **Petty cash**, and the offset account type is **Ledger**. The offset account must be specified.
- The account type is **Ledger**, and the offset account type is **Customer**, **Vendor**, or **Petty cash**. The offset account must be specified.

For general journal lines that meet the preceding conditions, the system assigns a separate sales tax direction:

- **Sales tax payable** for the **Customer** account type
- **Sales tax receivable** for the **Vendor** account type
- **Sales tax payable** for the **Petty cash** account type

### Example

You create the following general journal lines.

| Account type | Account number | Debit | Credit | Offset account type | Offset account number | Sales tax posting group | Item sales tax posting group |
|--------------|----------------|-------|--------|---------------------|-----------------------|-------------------------|------------------------------|
| Customer     | 1101           |       | 800    | Ledger              | 0101                  | AR-DOM                  | FULL                         |
| Vendor       | 1001           |       | 800    | Ledger              | 0101                  | AR-DOM                  | FULL                         |
| Ledger       | 0102           | 700   |        |                     |                       | AR-DOM                  | FULL                         |
| Ledger       | 0103           |       | 700    |                     |                       | AR-DOM                  | FULL                         |

Here are the results of the posting:

- Line 1 has a tax transaction that has a sales tax direction of **Sales tax payable**.
- Line 2 has a tax transaction that has a sales tax direction of **Sales tax receivable**.
- Line 3 has a tax transaction that has a sales tax direction of **Sales tax receivable**.
- Line 4 has a tax transaction that has a sales tax direction of **Sales tax payable**.

## SSRS VAT register report

The **VAT register** report is a Microsoft SQL Server Reporting Services (SSRS) report that is considered the main tax summary document. It's a basic document that is used in Polish accounting as the basis for reporting taxes to the tax authorities. It's also the main audit document for tax reporting in every Polish company. The VAT for sales, purchases, and imported products must be processed separately. The VAT statement is prepared based on the **VAT register** report. 

The legislation also defines several official reports for VAT, and conditions for transactions that must be included on the reports.

The VAT registers are printed regularly for reporting periods. (They are usually printed every month.) The reports must be printed on paper, and they must be signed by one or more authorities, such as a chief accountant or a chief financial officer (CFO). They are used as the basis for the monthly VAT 7 tax declaration. You can access **VAT register** reports from several places:

- **Tax** &gt; **Inquiries and reports** &gt; **Sales tax reports** &gt; **EU summary VAT register**
- **Tax** &gt; **Inquiries and reports** &gt; **Sales tax reports** &gt; **Purchase VAT register**
- **Tax** &gt; **Inquiries and reports** &gt; **Sales tax reports** &gt; **Sales VAT register**

## Allowance for bad debts

Polish VAT law regulations affect situations where unpaid invoices occur and VAT adjustments are required.

- On the creditor side, output VAT on unpaid invoices (receivables) can be corrected under the following conditions:

    - Goods or services were delivered to an active VAT taxpayer.
    - On the day before the VAT statement where the bad debt allowance will be used is submitted, the debtor is an active VAT taxpayer, and hasn't been the subject of bankruptcy or liquidation.
    - The receivable isn't more than two years overdue.

- Output VAT can be corrected for the period when the receivable is proved to be unrecoverable. In other words, the invoice wasn't paid within 150 days of the original due date. (The receivable wasn't sold, and the invoice wasn't paid.)
- On the debtor side, the debtor is obliged to correct input VAT in a period where 150 days passed from the original due date of the purchase invoice for payables that aren't paid. This requirement is unconditional. Therefore, the correction must be done even if the debtor didn't use the allowance for bad debts.
- If an invoice is paid (or a receivable is sold by the creditor) after the allowance for bad debts is used, the allowance should be reversed on the VAT statement for the period when the invoice was paid (or the receivable was sold by the creditor). If the payment was a partial payment, the reversal should also be partial and should be in proportion to the original invoice amount.
- The accountant who works with Accounts payable or Accounts receivable must periodically identify bad debts. Debts are considered bad debts when the invoices aren't paid more than 150 days but less than two years after the planned due date.
- The incoming and outgoing VAT may and should be corrected (reversed) for the identified debts. However, the accountant is responsible for making the final decision. Therefore, the accountant can manually exclude some invoices that were automatically identified.
- If the debts are paid in the next accounting period, the VAT must be reversed in proportion to the payment sum.
- A periodic procedure identifies the bad debts, based on the vendor's or customer's open transactions and settlements on one side, and on the payment schedule on the other side.
- The VAT in the identified debt sum is allocated between the VAT codes on the invoice lines that will be reversed.
- The sums of settled payments are also allocated in the same manner to the VAT codes on the invoice lines that will be reversed.
- If there is a mistake, the journals can be canceled, starting from the last journal. The transactions will be reversed.
- VAT sums are allocated through posting.
- You must set up general ledger accounts for VAT correction posting and periods for bad debts.

To set up the functionality for bad debt allowances, you must configure the system. Follow these steps.

1. Select **General ledger** &gt; **Journal setup** &gt; **Overdue debt journal calculation** to set up the calculation for the overdue debt journal.
2. Select a journal type:

    - Customer VAT journal
    - Vendor VAT journal

3. For each journal, set the following fields:

   - **Minimum number of days:** Enter the minimum period that indicates that an invoice is overdue. The minimum period is usually 150 days.
   - **Maximum number of days:** Enter the maximum period that an invoice isn't considered overdue. The maximum period is usually two years, or 720 days.
   - **Calculation type:** Select the type of date for each overdue invoice that should be calculated. The available values are **Due date** and **Invoice date**.
   - **Validate:** Select this check box to validate that the transaction balances don't change on the date of the last posted journal.

     > [!NOTE]
     > Leave the **Condition** and **Payment term days** fields blank.

4. On the **Accounts receivable parameters** and **Accounts payable parameters** pages, set up the following number sequence references:

    - Journal number for overdue debt VAT
    - Overdue debt VAT journal

5. Select **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Ledger posting group**, and select the general ledger accounts for **Offset Reversed Incoming Tax** and **Offset Reversed Outgoing Tax**.

After you've configured the system, you can use the **Overdue debt VAT** periodic function in Accounts receivable and Accounts payable to manage your overdue debts. You can perform the following actions on the page:

- **Create a journal** – Set up the date when the debt amount should be calculated. The date interval is automatically calculated, based on the setup of the overdue debt journal calculation.

    > [!NOTE]
    > When you create a journal, all overdue unpaid invoices for journal periods are automatically included. The journal also includes invoices that payments were processed for in that period. Information is available in the **Paid amount** and **Paid tax amount** fields.
	
    You can select a journal number to view the journal details and review the tabs:

    - **Overdue debt VAT journal header** – You can change the view between the **Lines** view and the **Header** view.
    - **Overdue debt VAT journal lines** – The lines include information about the customer's or vendor's invoices that are classified as having bad debts in the reporting period. You can use the **Exclude** check box to exclude any invoice that you don't want to process from the journal. You can't exclude an invoice if any part of it has already been processed (that is, if the VAT refund has been completed). The total amounts in the columns are reflected on the header. The amounts are recalculated when the lines are filtered.
    - **Line details** – The information includes details about the customer or vendor account, the transaction, and the overdue debt amount.

- **Post a journal** – You can create a VAT reversal transaction for invoices that are included in the journal. After the journal has been posted, it can be canceled.
- **Cancel posted journal** – The Cancel function is available only for the last journal. During cancellation, you can select the type of correction transaction (correction or reversal) by using the **Correction** check box in the dialog box.
- **Review vouchers** – View the voucher transactions that are created during posting or cancellation.
- **Review Posted sales tax** – View posted sales tax transactions that are allocated to tax codes from invoices.
- **Open counting** – View the summary information for customer or vendors, and invoices for those customers or vendors that are included in the journal.

The FactBox pane shows amounts for all invoices that have bad debts that haven't been paid as of the end of the reporting period. The overdue amount and overdue tax amount are also shown.

## Remove costs from overdue invoices

Polish taxation rules require that companies not have overdue payments to contractors. Companies are also penalized if they don't pay on time. The penalty is that you can't treat costs from overdue invoices as costs that are deductible from personal income tax (PIT)/corporate income tax (CIT).

The invoices can't be treated as tax-deductible in either of the following conditions:

- The term for the original due date is shorter than 60 days, and the invoice isn't paid within 30 days of the original due date.
- The term for the original due date is longer than 60 days, and the invoice isn't paid within 90 days of the date that is included in tax costs (for example, the posting date or period).

For PIT/CIT purposes, the correction of costs should be done in the month when they were excluded from tax costs, and the correction can be reverted in the month when that invoice was finally paid. If the invoice was partly paid, a partial correction or reversal of the correction can also be done.

The correction of costs is used when the invoice is a direct cost (for example, office rent), or when the invoice isn't posted directly to cost accounts. For example, the invoice is related to the purchase of a fixed asset, and the depreciation of the fixed asset isn't tax-deductible cost. Alternatively, the invoice is related to the purchase of goods for resale, and the cost of the goods that are sold isn't tax-deductible cost.

> [!NOTE]
> The functionality that is described here only lets you identify whether any invoices should be considered for correction. It's your responsibility to apply the required adjustments when you post.

To use this functionality, you must configure the system. Follow these steps.

1. Select **General ledger** &gt; **Journal setup** &gt; **Overdue debt journal calculation** to set up overdue debt intervals.

    Here is an example of a typical interval setup.

    - **Period 1:** Create a new entry, select the **Vendor CIT and PIT** journal type, and then set the following fields:

        - **Minimum number of days:** Specify the minimum number of days. The minimum number of days is usually 30.
        - **Maximum number of days:** Specify the maximum number of days. The maximum number of days is usually 360.
        - **Calculation type:** This field is used to define the date for each overdue invoice that should be calculated. Select **Due date**.
        - **Condition:** Specify **<**.
        - **Payment term days:** Specify the overdue days. The number of days is usually 60.
        - **Validate:** Set this field to **True** if validation is required when invoices are entered and settled.

    - **Period 2:** Create a new entry, select the **Vendor CIT and PIT** journal type, and then set the following fields:

        - **Minimum number of days:** Specify the minimum number of days. The minimum number of days is usually 90.
        - **Maximum number of days:** Specify the maximum number of days. The maximum number of days is usually 360.
        - **Calculation type:** This field is used to define the date for each overdue invoice that should be calculated. Select **Invoice date**. (In this case, the shipment date is considered.)
        - **Condition:** Specify **>=**.
        - **Payment term days:** Specify the overdue days. The number of days is usually 60.
        - **Validate:** Set this field to **True** to indicate that invoice transactions must be validated so that the total overdue debt amount remains the same as the amount on the date of the last overdue debt journal.

2. On the **Accounts payable parameters** page, set the following fields:

    - **Dimension to calculate the CIT and PIT correction:** Specify the dimension that should be used to allocate bad debts. (To access this field, select **Ledger and sales tax**, and then select the **Corporate Income Tax (CIT) and Personal Income Tax (PIT)** tab.)
    - **Number sequence:** Set up the **Overdue debt CIT and PIT journal** reference.

After you've set up non-deductible costs, you can perform the following tasks on the **Overdue vendor debt CIT and PIT journals** page:

- **Create a journal** – In the **Date** field, set the reporting date to the last date of the journal reporting period. Documents are selected based on the two conditions that you set up earlier. When the journal is created, the sum of debts is allocated proportionally among the financial dimensions that are assigned on the invoice lines.

    > [!NOTE]
	> The **New** button is available only when the page is empty, or when the last journal is approved.

    You can select a journal number to view the journal details and review the tabs:

    - **Overdue debt CIT and PIT journal header** – You can change the view between the **Lines** view and the **Header** view.
    - **Overdue debt CIT and PIT journal lines** – You can include information about vendor invoices that are selected according to configured criteria for the period. You can use the **Exclude** check box to exclude any invoice from a journal.
    - **Line details**

- **Approve a journal**
- **Cancel a journal approval** – The Cancel function is available only for the last approved journal.
- **View distributions** – View the distribution of the debt sum by financial dimension.
- **Print report**

The FactBox pane shows the totals in the journal and the total overdue amount.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
