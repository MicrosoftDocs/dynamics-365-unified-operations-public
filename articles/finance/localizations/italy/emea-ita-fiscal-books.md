---
title: Italian sales tax books
description: Learn how to set up and use Italian sales tax books and Italian sales tax book sections, including an outline on setting up sales tax books.
author: liza-golub
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2016-11-30
ms.search.form: CustParameters, LedgerJournalSetup, ProjJournalName, TaxBook, TaxBookSection, TaxBookSectionLookupVoucherSeries, TaxBookStatus, TaxBookTable, VendParameters, LedgerParameters
ms.dyn365.ops.version: Version 1611
---

# Italian sales tax books

[!include [banner](../../includes/banner.md)]

This article describes how to set up and use Italian sales tax books and Italian sales tax book sections.

According to Italian fiscal legislation, every value-added tax (VAT) transaction must belong to a tax book (*Libro IVA*) that you use for tax reporting. To fulfill these legislative requirements, Dynamics 365 Finance implements Italian sales tax books. Sales tax books can be different types. You must specify the sales tax book type to help guarantee that all sales and purchase transactions are included on the **Italian sales tax payment** report. You can keep as many sales tax books of the **Sales** and **Purchase** types as you require. You can divide each tax book into multiple tax book sections (*Sezionale IVA*). You must sequentially number (without gaps) and order all sales tax transactions by posting date. A tax book section is equivalent to a number sequence for the Italian sales tax voucher number (*Protocollo IVA*) that you always apply during posting to help guarantee chronological order by posting date.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category | Prerequisite |
|---|---|
| **Setup:** Legal entity | The primary address of the legal entity must be in Italy. (Select **Organization administration** &gt; **Organizations** &gt; **Legal entities** &gt; **Addresses** &gt; **Country/region**.) |
| **Setup:** Number sequences | Set up as many number sequences as you require to cover all the required types of sales tax transactions. (Select **Organization administration** &gt; **Number sequences** &gt; **Number sequences**.) All these number sequences must be continuous and must have **Company** scope. |
| **Setup:** Journal names | Set up the required journal names. (Select **General Ledger** &gt; **Journal setup** &gt; **Journal names** or **Project management and accounting** &gt; **Setup** &gt; **Journals** &gt; **Journal names**.) On the **General** FastTab, in the **Sales tax** section, in the **Italian sales tax book** field, specify one of the following values:<ul><li>**Not included** – Select this value for invoices and credit notes that come from countries/regions that are outside the European community.</li><li>**Purchase** – Select this value for purchase invoices and credit notes.</li><li>**Sales** – Select this value for sales invoices and credit notes.</li><li>**Empty** – Select this value for all other types of transactions.</li></ul>In some cases, the system sets the **Italian sales tax book** field automatically, based on the **Journal type** value. For example, if you set the **Journal type** field to **Invoice register**, the **Italian sales tax book** field is set to **Purchase** by default. |
| **Setup:** Module parameters | To make vouchers follow the number sequences of the related invoices and credit notes, select the **Reuse numbers** check box when you define the number sequences for those invoices and credit notes. You can find this check box on the **Number sequences** tab of the following pages:<ul><li>Accounts receivable parameters</li><li>Accounts payable parameters</li><li>Project management and accounting parameters</li></ul>For example, on the **Accounts receivable parameters** page, on the **Number sequences** tab, select the **Reuse numbers** check box for **Free text invoice voucher** to synchronize number allocation for free text invoice vouchers and free text invoices.<br><br>In the Italian localization, corrections to the Italian sales tax payment report for an already settled sales tax period aren't supported. So on the **General ledger parameters** page, on the **Sales tax** tab, set the Special report **Include corrections** option to **NO**. |
| **Setup:** Sales tax settlement period | For a **Sales tax settlement period** that you set up and use for sales tax accounting, specify the parameters, **Include zero lines** and **Include reverse transactions** to determine whether zero and reverse transactions are included into sales tax books by default. Values from these parameters are used as default values during the sales tax settlement process. For each period interval of the sales tax settlement, these parameters can be changed specifically during the sales tax settlement process. If the sales tax settlement process is run in batch, Finance applies the default parameter values of **Include zero lines** and **Include reverse transactions** parameters from the **Sales tax settlement period** setup. You can see the values of the **Include zero lines** and **Include reverse transactions** parameters that were used for each closed period interval of sales tax settlement period on the **Sales tax payment** page. You can't change the values of the parameters **Include zero lines** and **Include reverse transactions** for the closed period interval of the sales tax settlement period. Including zero and reverse transactions to the sales tax books might impact the page numbering in the report. |

## Set up sales tax books

Use sales tax books for sales tax reporting. To set up Italian sales tax books, go to **Tax** > **Setup** > **Sales tax** > **Italian sales tax books**. The following table describes the fields that are available on the **Italian sales tax books** page.

| Field | Description |
|---|---|
| Sales tax book | Enter the ID of the sales tax book. |
| Name | Enter a description of the sales tax book. |
| Sales tax book type | Select the nature of the operations that the sales tax book sections perform. Attach these sections to the sales tax book. The following values are available:<ul><li>**Purchase** – Select this value for purchase invoices and credit notes.</li><li>**Sales** – Select this value for sales invoices and credit notes.</li><li>**Not included** – Select this value for invoices and credit notes that come from countries or regions that are outside the European community. Use this type only for statistical purposes. It isn't included on the final fiscal tax book reports.</li></ul> |
| Settlement period | Select an existing sales tax settlement period. When you print a sales tax book, if you select the **Update** check box on the **Sales tax payment** page, the date in the **From date** field is compared to the selected settlement period. The settlement period also identifies which sales tax books and sales tax book sections must be closed when a sales tax settlement is updated for a settlement period. |
| Closed to | The latest closing date from the related sales tax book sections that belong to the selected sales tax book. |
| EU sales | Select a sales tax book of the **Sales** type, and attach it to the current sales tax book of the **Purchase** type. Use this field if the selected sales tax book must include European Union (EU) purchase transactions from the current book on sales tax reports. This field is unavailable for sales tax books of the **Sales** and **Not included** types. |
| ATECOFIN Code | Select the tax code for reporting. |
| Print summary and payment | Select this option to print the summary and payment report. This field is available only for sales tax books of the **Sales** type. |

## Set up sales tax book sections

Sales tax book sections act as a repository where you post ledger transactions according to their nature. The sales tax book sections drive the voucher numbering. To set up Italian sales tax book sections, select **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Italian sales tax book sections**. The following table describes the fields that are available on the **Italian sales tax book sections** page.

| Field | Description |
|---|---|
| Sales tax book | Select one of the existing sales tax books to attach the sales tax book section. |
| Sales tax book section | Enter the ID of the sales tax book section. |
| Name | Enter a description of the sales tax book section. |
| Number sequence code | Select the number sequence code for the sales tax book section. The number sequence code that you select depends on the type of sales tax book that the sales tax book section is attached to:<ul><li>For a sales tax book of the **Purchase** type: Select number sequence codes that are defined for purchase invoice vouchers or purchase credit note vouchers on the **Accounts payable parameters** page, or number sequence codes that are used on the **Journal names** page for vouchers that have the **Italian sales tax book** field set to **Purchase**.</li><li>For a sales tax book of the **Sales** type: Select number sequence codes that are defined for sales invoice vouchers or sales credit note vouchers or free text invoice vouchers or free text credit note vouchers on the **Accounts receivable parameters** page, or number sequence codes that are used on the **Journal names** page for vouchers that have the **Italian sales tax book** field set to **Sales**.</li><li>For a sales tax book of the **Not included** type: Select any suitable number sequence code.</li></ul> |
| Closed to | Enter the end date of the last closed sales tax settlement period. This field filters data on the sales tax report. |
| Close Italian sales tax book section | Enter the closing date of the Italian sales tax book for a tax period. You can't post or reverse an invoice that has a date that's earlier than the closing date. This field is updated with the closing date of the tax period. The **Update** check box must also be selected on the **Sales tax payment** page. |

The following button is also available.

| Button | Description |
|---|---|
| Create | Automatically creates all the required sales tax book sections for existing sales tax books of the **Sales** and **Purchase** types. The process creates sales tax book sections for every number sequence that's defined for purchase invoice vouchers or purchase credit note vouchers or sales invoice vouchers or sales credit note vouchers or free text invoice vouchers or free text credit note vouchers on the **Accounts payable parameters**, **Accounts receivable parameters**, or **Project management and accounting parameters** page. It also creates sales tax book sections for every number sequence that's used on the **Journal names** page for vouchers that have the **Italian sales tax book** field set to **Purchase** or **Sales**. The process automatically attaches each created sales tax book section to the default sales tax book. (You must create the sales tax book before creating the sales tax book sections.) If several sales tax books of the same sales tax book type (**Sales** or **Purchase**) exist, the process uses the first sales tax book by default. However, you can manually change this attachment. If no sales tax book exists, the process doesn't automatically create sales tax book sections. |

## Sales tax book status

When you create a new sales tax period, the system automatically creates sales tax book lines for every existing sales tax book. If you create an additional sales tax book, you can manually create lines for existing periods that aren't closed. Select **Tax** &gt; **Indirect taxes** &gt; **Sales tax** &gt; **Sales tax settlement periods**, and then select **Sales tax book status**. The following table describes the tabs on the **Sales tax book status** page.

| Tab | Description |
|---|---|
| Overview | View the page status of the sales tax books. All the fields are locked for manual updates. |
| General | View the same information that appears on the **Overview** tab, but only for the selected sales tax book. |

The following table describes the fields that are available.

| Field | Description |
|---|---|
| Sales tax book | Select the sales tax book ID that you set up on the **Italian sales tax books** page. |
| Name | Enter the name of the tax book. |
| First page number | The first page number that's used on the final sales tax report for this sales tax period. |
| Changed to | The page number that you specify in the **Change first page number** dialog box. |
| Last page number | The last page number that's used on the final sales tax report for this sales tax period. |
| Settlement period | The settlement period that's used in the sales tax book. |
| From date | The start date for the settlement period. |
| To date | The end date for the settlement period. |

The following button is also available.

| Button | Description |
|---|---|
| Change first page number | Open the **Change first page number** dialog box, where you can change the first page number that's used for the current open settlement period. |

### Change first page number dialog box

Use the **Change first page number** dialog box to change the number of the first page on the final sales tax report for this sales tax settlement period. The page number then appears in the **Changed to** column on the **Sales tax book status** page and is used as the first page number of the final sales tax report that you print for the current tax period. The following table describes the fields that are available in the **Change first page number** dialog box.

| Field | Description |
|---|---|
| First page number | The current first page number for the selected sales tax book. |
| Changed to | Enter the new first page number to use on the final sales tax report. |

## Using sales tax books

When you complete the setup, the sales tax book section that corresponds to the appropriate number sequence code appears in the **Sales tax book section** column on the **Number sequences** tab of the following pages:

- Accounts receivable parameters
- Accounts payable parameters
- Project management and accounting parameters

You must assign voucher numbers during posting in sequential order by posting date. You must post sales tax transactions that use the same number sequence code in order. If the voucher numbers aren't sequentially ordered, you receive an error message. Additionally, posting is interrupted if a sales tax transaction isn't assigned to a sales tax book section when you update an invoice. When you post a voucher through a sales tax book section, the identifiers of the related sales tax book and sales tax book section are saved in the tax transactions. (Go to **Tax** \> **Sales tax inquiries** \> **Posted sales tax**, and then select the **Posting** tab.) You can use this data during further sales tax reporting. Italian sales tax books are used for filtering, grouping, and sorting on the **Sales Tax (Italy)** report.

## Sales Tax (Italy) report

To report sales tax for Italy, follow these steps:

1. Go to **Tax** \> **Declarations** \> **Sales tax** \> **Sales Tax (Italy)**.
1. In the **Settlement period** field, select the sales tax settlement period to generate the report for.
1. In the **From date** field, specify a date in the interval of the settlement period that you want to generate the report for.
1. In the **Sales tax book type** field, select the type of sales tax book to generate the report for. If this field is blank, the report is generated for all types.
1. In the **From sales tax book** and **To sales tax book** fields, specify the sales tax books to generate the report for. If these fields are blank, the report is generated for all sales tax books.
1. In the **Printout** section, select the **Sales tax books** checkbox to generate a report that includes the details of the taxable documents in the sales tax books.
1. Select the **Sales tax summary** checkbox to generate a report that includes a summary section of the sales tax books.
1. Select the **Sales tax payment** checkbox to generate a report that includes the **Sales tax payment** page of the report.
1. Select the **Include zero lines** checkbox if you selected the **Sales tax books** checkbox and want to generate a report that includes details and zero-line details of the taxable documents in the sales tax books.
1. Select the **Include reverse transaction** checkbox if you selected the **Sales tax books** checkbox and want to generate a report that includes details and reverse transaction details of the taxable documents in the sales tax books.
1. On the **Destination** FastTab, set up a destination where the report must be generated.
1. On the **Run in the background** FastTab, set up batch parameters if you want to generate the report in batch mode.
1. Select **OK** to generate the report.

## Related information

Because of the fiscal requirements for sequential document numbering and how this information is used in the sales tax books, users in Italy shouldn't access the following functions:

- Reverse customer transaction (**All customers** page, select **Transactions** > **Reverse**)
- Reverse vendor transaction (**All vendors** page, select **Transactions** > **Reverse**).

Use the Privileges functionality to hide these functions. For more information, see [Role based security privileges](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#privileges).

To hide these functions from the user interface for all security roles, follow these steps:

1. Go to **System administration** > **Security** > **Security configuration**.
1. On the **Privileges** tab, select **Reverse customer transactions**.
1. Select **Action menu items** > **TransactionReversal_Cust**.
1. Select **Deny** for **Read**, **Update**, **Create**, and **Delete**.

:::image type="content" source="../media/security-configuration.png" alt-text="Screenshot of the Security configuration page.":::

1. On the **Unpublished objects** tab, select **Publish all**.

:::image type="content" source="../media/unpublished-objects.png" alt-text="Screenshot of the Unpublished objects page.":::

1. Repeat these steps for the privilege, **Reverse vendor transactions**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
