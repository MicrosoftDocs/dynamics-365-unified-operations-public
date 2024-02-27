---
title: Configure and report Italian sales tax books
description: The article describes how to set up and use Italian sales tax books.
author: liza-golub
ms.date: 02/22/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: 
ms.search.region: Italy
ms.author: egolub
ms.search.validFrom: 2024-02-22
ms.dyn365.ops.version: Version 1611
ms.search.form: CustParameters, LedgerJournalSetup, ProjJournalName, TaxBook, TaxBookSection, TaxBookSectionLookupVoucherSeries, TaxBookStatus, TaxBookTable, VendParameters, LedgerParameters
---

# Configure and report Italian sales tax books

[!include [banner](../../includes/banner.md)]

The article describes how to configure and generate Italian sales tax books.

According to Italian legislation, every value-added tax (VAT) transaction must be recorded in a tax book (*Libro IVA*) that will be used for tax reporting. 
To fulfill these legislative requirements, Dynamics 365 Finance implements **Italian sales tax books** functionality. 
Sales tax books can be of **Purchase** or **Sales** types. 
You can keep as many sales tax books as you require. 
Every tax book is divided into multiple tax book sections (*Sezionale IVA*). 
All sales tax transactions must be sequentially numbered (without gaps) and ordered by posting date within each sales tax book section. 
Tax transaction voucher in Finance is equivalent to the Italian *Protocollo IVA* that must always be applied during posting to help guarantee chronological order by posting date.

As of 10.0.39 version of Dynamics 365 Finance, the **Italian sales tax books** functionality supports reporting of Italian sales tax book in [Electronic reporting (ER) tool](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) and accomodates reporting for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md).

## Prerequisites

Before you begin, you must [Configure system parameters to report Sales tax books for Italy](emea-ita-vat-statements-details.md).

## Configure sales tax books

To set up Italian sales tax books, go to **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Italian sales tax books**. 
The following table describes the fields that are available on the **Italian sales tax books** page.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Sales tax book</strong></td>
<td>Enter the ID of the sales tax book.</td>
</tr>
<tr class="even">
<td><strong>Name</strong></td>
<td>Enter a description of the sales tax book.</td>
</tr>
<tr class="odd">
<td><strong>Sales tax book type</strong></td>
<td>Select the nature of the operations that will be performed through the sales tax book sections that you will attach to the sales tax book. The following values are available:
<ul>
<li><strong>Purchase</strong> – Select this value for purchase invoices and credit notes.</li>
<li><strong>Sales</strong> – Select this value for sales invoices and credit notes.</li>
<li><strong>Not included</strong> – Select this value for invoices and credit notes that come from countries/regions that are outside the European community. This type is used only for statistical purposes and won&#39;t be included on the final fiscal tax book reports.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Settlement period</strong></td>
<td>Select an existing sales tax settlement period. When a sales tax book is printed, if the <strong>Update</strong> check box is selected on the <strong>Sales tax payment</strong> page, the date in the <strong>From date</strong> field is compared to the selected settlement period. The settlement period is also used to identify which sales tax books and sales tax book sections must be closed when a sales tax settlement is updated for a settlement period.</td>
</tr>
<tr class="odd">
<td><strong>Closed to</strong></td>
<td>The latest closing date from the related sales tax book sections that belong to the selected sales tax book.</td>
</tr>
<tr class="even">
<td><strong>EU sales</strong></td>
<td>Select a sales tax book of the <strong>Sales</strong> type and attach it to the current sales tax book of the <strong>Purchase</strong> type. This field is used if the selected sales tax book must include European Union (EU) purchase transactions from the current book on sales tax reports. This field is unavailable for sales tax books of the <strong>Sales</strong> and <strong>Not included</strong> types.</td>
</tr>
<tr class="odd">
<td><strong>ATECOFIN Code</strong></td>
<td>Select the tax code for reporting.</td>
</tr>
<tr class="odd">
<td><strong>Include reverse transactions</strong></td>
<td>Select this option to include reverse documents in Sales tax books report for this book.</td>
</tr>
<tr class="odd">
<td><strong>Include zero lines</strong></td>
<td>Select this option to include documents with zero amount in Sales tax books report for this book.</td>
</tr>
<tr class="even">
<td><strong>Print summary and payment</strong></td>
<td>Select this option to print the summary and payment report. This field is available only for sales tax books of the <strong>Sales</strong> type.</td>
</tr>
</tbody>
</table>

## <a id="sales-tax-book-sections"></a> Configure sales tax book sections
Sales tax book sections are a repository where ledger transactions are posted according to their nature. The voucher numbering is driven by the sales tax book sections. To set up Italian sales tax book sections, click **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Italian sales tax book sections**. The following table describes the fields that are available on the **Italian sales tax book sections** page.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Field</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Sales tax book</strong></td>
<td>Select one of the existing sales tax books that the sales tax book section is attached to.</td>
</tr>
<tr class="even">
<td><strong>Sales tax book section</strong></td>
<td>Enter the ID of sales tax book section.</td>
</tr>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Enter a description of the sales tax book section.</td>
</tr>
<tr class="even">
<td><strong>Number sequence code</strong></td>
<td>Select the number sequence code for the sales tax book section that you previously set up in [Number sequences and number sequence groups](emea-ita-vat-statements-details.md#number-sequences) section. The number sequence code that you select depends on the type of sales tax book that the sales tax book section is attached to:
<ul>
<li>For a sales tax book of the <strong>Purchase</strong> type: Select number sequence codes that are defined for purchase invoice vouchers or purchase credit note vouchers on the <strong>Accounts payable parameters</strong> page, or number sequence codes that are used on the <strong>Journal names</strong> page for vouchers that have the <strong>Italian sales tax book</strong> field set to <strong>Purchase</strong>.</li>
<li>For a sales tax book of the <strong>Sales</strong> type: Select number sequence codes that are defined for sales invoice vouchers or sales credit note vouchers or free text invoice vouchers or free text credit note vouchers on the <strong>Accounts receivable</strong> <strong>parameters</strong> page, or number sequence codes that are used on the <strong>Journal names</strong> page for vouchers that have the <strong>Italian sales tax book</strong> field set to <strong>Sales</strong>.</li>
<li>For a sales tax book of the <strong>Not included</strong> type: Select any suitable number sequence code.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Closed to</strong></td>
<td>Enter the end date of the last closed sales tax settlement period. This field is used to filter data on the sales tax report. If the field is filled in with date before reporting period and there are no transactions in reporting period for this sales tax book section, the section is not included in the report.</td>
</tr>
<tr class="even">
<td><strong>Close Italian sales tax book section</strong></td>
<td>The closing date of the Italian sales tax book for a tax period. You can&#39;t post or reverse an invoice that has a date that is earlier than the closing date of the tax period. This field is updated with the closing date of the tax period. The <strong>Update</strong> check box must also be selected on the <strong>Sales tax payment</strong> page.</td>
</tr>
</tbody>
</table>

**Create** button on the Action pane of **Italian sales tax book sections** page automatically creates all the required sales tax book sections for existing sales tax books of the **Sales** and **Purchase** types. 
Sales tax book sections are created for every number sequence that is defined for purchase invoice vouchers or purchase credit note vouchers or sales invoice vouchers or sales credit note vouchers or free text invoice vouchers or free text credit note vouchers on the **Accounts payable parameters**, **Accounts receivable parameters**, or **Project management and accounting parameters** page, and for every number sequence that is used on the **Journal names** page for vouchers that have the **Italian sales tax book** field set to **Purchase** or **Sales**. 
Every sales tax book section that is created is automatically attached to the default sales tax book. (The sales tax book must be created before the sales tax book sections.) If several sales tax books of the same sales tax book type (**Sales** or **Purchase**) exist, the first sales tax book is used by default. However, you can manually change this attachment. If no sales tax book exists, no sales tax book sections are automatically created. 

### <a id="unified-posting-date-control"></a> Unified posting date control

You can configure chronology control of invoice posting dates within a specific sales tax book section. 

1. In the Feature management workspace, turn on the **(Italy) Unified posting date control** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
2. When the feature is enabled, you can see **Skip posting date control** column on **Italian sales tax book sections** page. Select whether posting date control is required for a selected sales tax book section.

![Posting date control.](../media/emea-ita-post-date-control.jpg)

 If the field isn't enabled, which is the default option, the system doesn't allow posting of new invoices with dates earlier than the date of the latest posted invoice.  
 
 If the field is enabled, the system allows posting with any date.

## Sales tax book status

When a new **Sales tax settlement period** is created, **Sales tax book status** records are automatically created for every sales tax book that exists in your legal entity. 
If an additional sales tax book is created, lines can be manually created for existing periods that haven't been closed. 
Click **Tax** &gt; **Indirect taxes** &gt; **Sales tax** &gt; **Sales tax settlement periods**, and then click **Sales tax book status** on the Action pane. 

The following table describes the fields that are available on **Sales tax book status** page.

| Field                 | Description                                                                                      |
|-----------------------|--------------------------------------------------------------------------------------------------|
| **Sales tax book**    | Select the sales tax book ID that you set up on the **Italian sales tax books** page. |
| **Name**              | Name of selected **Sales tax book** is displayed.                             |
| **First page number** | The first page number that will be used by Italian sales tax books report. |
| **Changed to**        | When you update the **First page number** by using **Change first page number** function, this field represents the first page number after the update. |
| **Last page number**  | The last page number that is used on the final page of Italian sales tax report for this period.  |
| **Settlement period** | This field displays the settlement period that is used in the sales tax book. |
| **From date**         | This field displays the start date for the settlement period.  |
| **To date**           | This field displays the end date for the settlement period.    |
| **To date**           | This field displays the end date for the settlement period.    |
| **Print blank page with no transactions** | This field displays the state of **Print blank page with no transactions** parameter of related [Sales tax authority](emea-ita-vat-statements-details.md#sales-tax-authority) when the Italian sales tax books electronic report was generated for the selected period interval. |
| **Include zero lines** | This field displays the state of **Include zero lines** parameter of related [Italian sales tax book](emea-ita-sales-tax-books.md#configure-set-up-sales-tax-books) when the Italian sales tax books electronic report was generated for the selected period interval.    |
| **Include reverse transactions** | This field displays the state of **Include reverse transactions** parameter of related [Italian sales tax book](emea-ita-sales-tax-books.md#configure-set-up-sales-tax-books) when the Italian sales tax books electronic report was generated for the selected period interval.    |
| **Printout status** | This field displays the status of generation of Italian sales tax books electronic report in PDF format. Following values are available: <br> **- Not generated:** when Italian sales tax books electronic report in PDF format has not been generated for selected period interval with enabled **Update number of pages** checkbox parameter. <br> **- Generated:** when Italian sales tax books electronic report in PDF format has been generated for selected period interval with enabled **Update number of pages** checkbox parameter. You can review the generated report as an attachment for each **Sales tax book status** line if **Attach report to Sales tax book status** checkbox was selected for the **Sales tax settlement period**.   |

Use **Change first page number** button on the Action pane to open the **Change first page number** dialog box, to change the first page number that will be used for the current open settlement period. 
The page number then appears in the **Changed to** column on the **Sales tax book status** page and is used as the first page number of the final sales tax report that is printed for the current tax period. 

When **Attach report to Sales tax book status** checkbox is marked for selected **Sales tax settlement period**, use **Attachments** button in the upper-right corner of **Sales tax book status** page to review previously created Italian sales tax books electronic reports.

## Set up Italian sales tax books electronic report

As of 10.0.39 version of Dynamics 365 Finance, you can use Italian sales tax books electronic report in PDF format. To prepare your Finance to generate Italian sales tax books electronic report in PDF format, follow these steps.

1. Import the following ER configurations.

| ER configuration name             | Type | Description |
|-----------------------------------|------|-------------|
| Tax declaration model              | Model | A generic model for different tax declarations. |
| Tax declaration model mapping (IT) | Model mapping | Model mapping for Italian sales tax books. |
| VAT Declaration PDF (IT)           | Format (exporting) | The PDF format of Italian sales tax books. |

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version. Use the Issue search tool in [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2) to find the KB article by number.

For more information about how to download ER configurations from the Microsoft global repository, see [Download ER configurations from the Global repository](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

> [!NOTE]
> After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for the **Tax declaration model mapping (IT)** configuration on the **Configurations** page.
>

2. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
3. To define the **VAT Declaration PDF (IT)** format, go to **Tax** \> **Setup** \> **General ledger parameters**. On the **Sales tax** tab, in the **Tax options** section, in the **VAT statement format mapping** field, enter the format information.

> [!IMPORTANT]
> The **VAT Declaration PDF (IT)** electronic reporting format is generated using specifically prepared data for Italian sales tax books. It is important to set up parameters of **Sales tax authority** and **Sales tax settlement periods** in accordance to guidance provided in [Configure system parameters to report Sales tax books for Italy](emea-ita-vat-statements-details.md) section of documentation.

## Generate Italian sales tax books electronic report

To generate Italian sales tax books electronic report, follow these steps.

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**. The **Report sales tax for settlement period** dialog is shown.
2. In the **Settlement period** field, select the sales tax settlement period to generate the report for.
3. In the **From date** field, specify a date in the interval of the settlement period that you want to generate the report for.
4. In the **Sales tax payment version** field, select **Original** and click **OK** button. For **Sales tax settlement periods** associated with **Sales tax authority** connected to a **Vendor account** with address in Italy, only **Original** **Sales tax payment version** can be selected.
5. The **Sales tax (Italy)** dialog is shown. In the **Settlement period** field of **Sales tax (Italy)** dialog the previously selected **Settlement period** is displayed for information.
6. When **Variative period** checkbox of the **Sales tax (Italy)** dialog is not selected, in the **From date** and **To date** fields of **Sales tax (Italy)** dialog you can see the beginning and end dates of period interval where **From date** that was selected on previous dialog belongs to. Use **Variative period** checkbox of the **Sales tax (Italy)** dialog to generate Italian sales tax books electronic report for a period different from the interval of **Sales tax settlement period**. When **Variative period** checkbox is selected, the **Last page number** value in related **Sales tax book status** cannot be updated.
7. In the **Sales tax book type** field, select the type of sales tax book to generate the report for. If this field is blank, the report is generated for all types.
8. In the **From sales tax book** and **To sales tax book** fields, specify the sales tax books to generate the report for. If these fields are blank, the report is generated for all sales tax books.
9. In the **Printout** group of parameters, select the **Sales tax books** checkbox to generate a report that includes the details of the taxable documents in the sales tax books.
10. In the **Printout** group of parameters, select the **Sales tax summary** checkbox to generate a report that includes a summary section of the sales tax books.
11. In the **Printout** group of parameters, select the **Sales tax payment** checkbox to generate a report that includes the **Sales tax payment** page of the report.
12. In the **Printout** group of parameters, select **Plafond** checkbox to generate a report that includes the **Tax plafond** section of the Sales tax payment report. For more information, see [Tax plafond](emea-ita-exil-tax-plafond.md).
13. In the **Printout** group of parameters, select the language that you want to generate report on in **Language** field.
14. In the **Update** group of parameters, select **Update number of pages** checkbox to update  **Last page number** value in related **Sales tax book status** record for the sales tax settlement period.

> [!IMPORTANT]
> It is important to generate **Italian sales tax books electronic report** with selected **Update number of pages** checkbox at least onece per each interval of sales tax settlement period to support correct numbering of pages. When **Update number of pages** checkbox is selected and **Attach report to Sales tax book status** checkbox is selected in parameters of the **Sales tax settlement period**, you can find the generated **Italian sales tax books electronic report** attached to the **Sales tax book status** records.

15. When **Sales tax payment** checkbox is selected, the **Sales tax payment** FastTab of the **Sales tax (Italy)** dialog is available and represents following fields necessary for sales ta payment report:
   - **Sales tax balance in period**. This field displays the sales tax balance in period.
   - **Previous sales tax credit (-)**. Enter manually previous sales tax credit amount.
   - **Sales tax credit for compensation (-)**. Enter manually sales tax credit for compensation amount.
   - **Previous sales tax debit (+)**. Enter manually previous sales tax debit amount.
   - **Sales tax paid in advance (-)**. Enter manually sales tax paid in advance.
   - **Sales tax balance**. This field displays calculated sales tax balance for selected period.
   - **Amount of payment**. Enter manually amount of payment.
   - **Date of payment**. Enter manually the date of payment.
   - **Bank account**. Enter manually the bank account.
   - **Bank reference ABI**. Enter manually the bank reference ABI.
   - **Bank reference CAB**. Enter manually the bank reference CAB.
16. On the **Run in the background** FastTab, set up batch parameters if you want to generate the report in batch mode. When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
17. Select **OK** to generate the report. When **Update number of pages** checkbox is selected and **Attach report to Sales tax book status** checkbox is selected in parameters of the **Sales tax settlement period**, you can find the generated **Italian sales tax books electronic report** attached to the **Sales tax book status** records and the **Last page number** value in related **Sales tax book status** record for the sales tax settlement period is updated. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
