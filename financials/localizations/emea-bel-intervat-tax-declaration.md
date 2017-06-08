---
# required metadata

title: INTERVAT tax declaration
description: This topic provides country/region-specific information about how to set up and create the INTERVAT tax declaration for legal entities in Belgium only.
author: v-oloski
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxIntervat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: AX 7.0.1, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 273023
ms.search.region: Belgium
ms.search.industry: All
ms.author: v-oloski
ms.dyn365.ops.version: AX 7.0.1
ms.search.validFrom: 2016-05-31

---

# INTERVAT tax declaration

[!include[banner](../includes/banner.md)]


This topic provides country/region-specific information about how to set up and create the INTERVAT tax declaration for legal entities in Belgium only.

You can create the INTERVAT tax declaration as an XML file. The INTERVAT declaration that you create can also include corrections from the previous year. Additionally, if you didn't have transactions for a turnover report or an annual listing during the previous financial year, you can indicate that this annual listing is an empty annual listing. Users can fill in correction data on the **Additional sales tax report boxes** page. In some cases, tax corrections are mandatory for the Belgian value-added tax (VAT) declaration. Examples are sales tax reporting codes 63 and 64, which are used for tax fines. Other examples are sales tax reporting codes 81, 82, 83, and so on. These codes aren't printed when the total amounts of the codes are negative. These negative amounts must be deducted from the next VAT declaration, when these cases are positive again. This task must be completed by using a tax correction. Before users make a tax correction, they must indicate which sales tax reporting codes are subject to tax corrections.

## Prerequisites
The following table shows the prerequisites that must be set up before you begin to work with the INTERVAT tax declaration.

|Category|Prerequisite||
|---------|----------------------------|---------------------------------------------|
|Setup|Legal entity|On the <strong>Legal entities</strong> page (click <strong>Organization administration</strong> &gt; <strong>Organizations</strong> &gt; <strong>Legal entities</strong>), select your legal entity. On the <strong>Addresses</strong> FastTab, create an address. Select <strong>Belgium</strong> in the <strong>Country/region</strong> field, fill in other address components, and mark the address as <strong>Primary</strong>. On the <strong>Tax registration</strong> FastTab, in the <strong>Tax registration number</strong> field, specify the tax registration number for your company. See the field descriptions in <a href="https://ax.help.dynamics.com/en/wiki/create-a-legal-entity/">Legal entity</a>.|
|Setup| Registration number|Set up registration number on the <strong>Legal entities</strong> page (click <strong>Organization administration</strong> &gt; <strong>Organizations</strong> &gt; <strong>Legal entities</strong>). Click <strong>Registration IDs</strong>, and then, on the <strong>Registration ID</strong> FastTab, click <strong>Add</strong>. Select a value in the <strong>Registration type</strong> field, and enter a value in the <strong>Registration number</strong> field. For more information, see <a href="emea-registration-ids.md">Registration number</a>.|
|Setup| Number sequences|Set up number sequences for <strong>Annual sales list ID</strong> and <strong>INTERVAT ID</strong> on the <strong>Number sequences</strong> tab of the <strong>General ledger parameters</strong> page (click <strong>General ledger</strong> &gt; <strong>Ledger setup</strong> &gt; <strong>General ledger parameters</strong>).</td>
|Setup| Posting journal|Set up posting journals on the <strong>Journal setup</strong> page (click <strong>General ledger</strong> &gt; <strong>Journal setup</strong>). </td>
|Setup| Sales tax authorities|Set up sales tax authorities on the <strong>Sales tax authorities</strong> page (click <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax authorities</strong>). The <strong>Report layout</strong> field should be set to <strong>Belgium report layout</strong>. See the field descriptions in <a href="https://ax.help.dynamics.com/en/wiki/set-up-sales-tax-authorities/">Sales tax authorities</a>.|
|Setup| Sales tax reporting codes|Set up sales tax reporting codes on the <strong>Sales tax reporting codes</strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Sales tax reporting codes</strong>). See the field descriptions in <a href="https://ax.help.dynamics.com/en/wiki/set-up-sales-tax-reporting-codes/">Sales tax reporting codes</a>. Sales tax reporting codes for which the <strong>Sales tax correction</strong> check box is selected are available for selection on the <strong>Additional sales tax report boxes</strong> page (click <strong>Tax corrections</strong> &gt; <strong>Adjustments</strong>). An example of sales tax reporting codes is included later in this topic.|
|Setup| Sales tax codes|Fill in the fields on the <strong>Report</strong> and <strong>Report - credit note</strong> tabs of the <strong>Sales tax codes</strong> page (click <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax codes</strong>). Select values from the <strong>Sales tax reporting codes</strong> table. See the field descriptions in <a href="https://ax.help.dynamics.com/en/wiki/set-up-sales-tax-codes/">Sales tax codes</a>.|
|Setup| INTERVAT setup|Create elements for INTERVAT on the <strong>INTERVAT setup</strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>INTERVAT setup</strong>). You can use INTERVAT to complete electronic tax declarations in Belgium. The information that you enter on this page is used when you click <strong>Open Web site</strong> on the <strong>INTERVAT tax declaration</strong> page. You should create an element for each language, and for the program that you use to browse websites. Fill in the following fields: Language, Description, URL.
|Setup| Tax exempt number|Create tax exempt numbers for your counterparties on the <strong>Tax exempt numbers</strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Tax exempt numbers</strong>). For each tax exempt number, create a record on the page, and specify the following information:|
|     |                  |Country/region</strong>  Select the country/region of the tax registration of the counterparty.|
|     |                  |Tax exempt number</strong>  Enter the tax exempt number of the counterparty.|
|     |                  |Company name</strong>  (Optional) Enter the name of the counterparty.|
|Setup|Foreign trade parameters|Set up foreign trade parameters on the <strong>Country/region properties</strong> tab of the <strong><strong>Foreign trade parameters</strong></strong> page (click <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Foreign trade</strong> &gt; <strong>Foreign trade parameters</strong>). |
|Setup|INTERVAT tax declaration configuration|Configure an Electronic reporting (ER) model and format for the report. See the &quot;Configure the Electronic reporting model and format for the report&quot; section later in this topic. For information about how to create and maintain ER configurations, see the ER documentation.|


For more information about how to set up the VAT statement, see [(EU) VAT reporting](emea-vat-reporting.md).

### Example: Setup of sales tax reporting codes

The following table shows an example of the sales tax reporting codes that can be created for users in legal entities in Belgium.

| Sales tax reporting code | Description                                                                                                                                                                                 |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 00                       | The sale of goods at the 0-percent sales tax rate                                                                                                                                           |
| 01                       | Taxable supplies and services at the 6-percent sales tax rate The delivery of a product or service transactions at the 6-percent sales tax rate                                             |
| 02                       | Taxable supplies and services at the 12-percent sales tax rate The delivery of a product or service transactions at the 12-percent sales tax rate                                           |
| 03                       | Taxable supplies and services at the 21-percent sales tax rate The delivery of a product or service transactions at the 21-percent sales tax rate                                           |
| 44                       | Taxable amount of services to taxable persons (B2B) in another European Union (EU) member state in which the VAT must be paid by the contractor that is established in another member state |
| 45                       | Taxable amount of construction works                                                                                                                                                        |
| 46                       | Intra-community supply of goods and similar transactions (shipments)                                                                                                                        |
| 47                       | The delivery of goods to a customer in another EU member state The supply of goods that involve assembly or installation abroad Remote selling And so on                                    |
| 48                       | Credit notes and other negative corrections for codes 44 and 46                                                                                                                             |
| 49                       | Revenue adjustments for codes 00, 01, 02, 03, 45, and 47                                                                                                                                    |
| 54                       | The total amount of VAT that is payable on the turnover that is included in codes 01, 02, and 03                                                                                            |
| 55                       | The total amount of VAT that is due on the amounts that are mentioned in codes 86 and 88.                                                                                                   |
| 56                       | Co-contractor goods and services                                                                                                                                                            |
| 57                       | Non-EU import, VAT domestic                                                                                                                                                                 |
| 59                       | The amount of deductible VAT that is indicated on incoming invoices that are related to the purchase of goods and services                                                                  |
| 62                       | Correction: total VAT recoverable                                                                                                                                                           |
| 64                       | VAT is recoverable in issued credit notes that are due and that pertain to invoices for which VAT was originally included in code 54.                                                       |
| 81                       | The amount of all purchases of goods, raw materials, and consumables, and related acquisition costs                                                                                         |
| 82                       | The amount of miscellaneous goods and services, regardless of whether they are subject to VAT                                                                                               |
| 83                       | The amount of purchases of capital goods, regardless of whether they are subject to VAT                                                                                                     |
| 84                       | Credit notes that are received that pertain to transactions that are related to intra-community acquisition and intra-community services for codes 86 and 88                                |
| 85                       | Credit notes that pertain to all transactions except those transaction that are included in code 84                                                                                         |
| 86                       | Intra-community acquisitions and similar transactions                                                                                                                                       |

To set up an assignment of sales tax reporting codes to sales tax codes, go to **Sales tax codes** &gt; **Report setup/Report setup - Credit note**.

## Configure the ER model and format for the report
To review or change the configuration of the INTERVAT declaration for legal entities in Belgium, on the **Reporting configurations** page, select **INTERVAT model** in the list of models. This model is used for the Belgian INTERVAT declaration. On the Action Pane, click **Designer** to review or change the model. To review or change the format of the INTERVAT declaration for legal entities in Belgium, on the **Reporting configurations** page, select **INTERVAT model** in the list of models, and then, under **INTERVAT model**, select **INTERVAT format (BE)**. On the Action Pane, click **Designer** to review or change the format.

## Generate an INTERVAT tax declaration
At the end of the VAT reporting period, run the INTERVAT tax declaration (click **Tax** &gt;**Declarations** &gt; **Sales tax**) to calculate declaration lines for the definition of sales tax reporting codes that you created. The following table describes the fields that you must set.

| Field                    | Description                                                                                                                                                                                                                                                                                                                                                    |
|--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period        | Select the applicable reporting period.                                                                                                                                                                                                                                                                                                                        |
| From date                | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page.                                                                                                                                                                      |
| Transaction date         | Enter the date when the sales tax report is calculated. The default value is the current date. The end date of the settlement period that is shown in the **From** field corresponds to the **To** field on the **Sales tax settlement periods** page. The sales tax payment is calculated for all transactions that were posted during the settlement period. |
| Update                   | Select this check box to update a declaration that was previously submitted.                                                                                                                                                                                                                                                                                   |
| Replaced VAT declaration | Enter the identification number of the declaration to replace.                                                                                                                                                                                                                                                                                                 |
| File                     | Enter the file name that the INTERVAT tax declaration will be exported to.                                                                                                                                                                                                                                                                                     |
| Format mapping           | Specify **INTERVAT format (BE)**.                                                                                                                                                                                                                                                                                                                              |

The system automatically generates an INTERVAT XML file and then offers to open it.

## Generate an INTERVAT summary tax declaration
To create an INTERVAT tax declaration for several tax periods and INTERVAT tax declaration IDs, click **Tax** &gt; **Inquiries and Reports** &gt; **Sales tax reports** &gt; **INTERVAT summary tax declaration**, and then use the filters to specify criteria for selecting data.

## Additional sales tax report boxes
To create corrections of the INTERVAT tax declaration for the previous period, click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **Additional sales tax report boxes**. The following table describes the fields that you must set.

| Field             | Description                                                                                                                                                                               |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period | Select the applicable reporting period.                                                                                                                                                   |
| From date         | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page. |
| To date           | Enter the last date.                                                                                                                                                                      |

To enter correction, click **Tax corrections** &gt; **Adjustments**, and fill in the following fields.

| Field             | Description                                                                                                                                                                               |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Settlement period | Select the applicable reporting period.                                                                                                                                                   |
| From date         | Enter the first day of the sales tax settlement period to calculate sales tax for. This value corresponds to the date in the **From** field on the **Sales tax settlement periods** page. |
| To date           | Enter the last date.                                                                                                                                                                      |
| Reporting code    | Select reporting code. Only the reporting codes that tax corrections are enabled for will be available during tax correction entry.                                                       |
| Amount            | Enter the correction amount.                                                                                                                                                              |



Additional resources
--------

[Belgian sales tax reporting codes](http://www.taxexpert.be/bestand/Betekenis%20vakken%20BTW-aangifte.pdf)




