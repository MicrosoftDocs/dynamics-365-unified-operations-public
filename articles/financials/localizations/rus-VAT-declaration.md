---
# required metadata
title: VAT declaration (Russia)
description: This topic provides information about VAT declaration for Russia.
author: anasyash
manager: AnnBe
ms.date: 11/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-11-23
ms.dyn365.ops.version: 8.1.1

---

# VAT declaration (Russia)

[!include [banner](../includes/banner.md)]

To start to work with the value-added tax (VAT) declaration, follow these steps.

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the VAT declaration format.

    For example, to generate the VAT declaration for the year 2018 reporting period, download the latest versions of the following configurations:

    - VAT declaration model (RU)
    - VAT declaration model mapping (RU)
    - VAT declaration format 5.05

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2. Optional: Set up a financial report for the VAT declaration. Set up calculation rules for financial report cells.

    You should complete this optional step if you will use financial reports to generate data for some cells in section 3 of the VAT declaration, based on the setup of financial report cells.

    For more information about how to set up financial reports for Russia, see [Financial reporting (Russia)](rus-financial-reports.md).

3. Optional: For the first use, you can upload Data management package settings to work with the Russian VAT declaration. Follow these steps:

    1. In the LCS Shared asset library, select **Data package** as the asset type. Download the package that is named **RU VAT Declaration demo setup**. The file that is downloaded is named RU VAT Declaration.zip.
    2. In Microsoft Dynamics 365 for Finance and Operations, in the **Data management** workspace, select **Import**.
    3. In the **Job details** section, set the following values:

        - Enter a name for the job.
        - In the **Data source format** field, select **Package**.

    4. In the **Upload data file** field, select **Upload**, and then select the **RU VAT Declaration.zip** file that you downloaded earlier.
    5. After the data entities are uploaded, select **Import**.
    6. Go to **General ledger \> Financial reports setup \> Financial reports**, and validate the financial report that you imported.

## Russian VAT declaration version 5.05 in XML format

You configure the Russian VAT declaration version 5.05 in XML format in the **Electronic reporting** module. It contains the following information:

- **Section 1** – The total VAT amount that must be paid to budget or reclaimed. This section contains cumulative amounts from sections 3 through 7.
- **Section 2** – The VAT amount that must be paid to budget by the tax agent.
- **Section 3** – Calculation of VAT amounts that must be paid to budget or reclaimed.

    - **Application 1 to section 3** – The VAT amounts that were previously deducted, and that are now subject to restoration and payment to budget for fixed assets that were used in non-taxable operations.

- **Section 4** – Calculation of VAT amounts for export sales where a tax rate of 0 percent was confirmed during the period.
- **Section 5** – Calculation of deductible VAT amounts for the reporting period, for export sales where a tax rate of 0 percent was either confirmed or unconfirmed in previous periods.
- **Section 6** – Calculation of VAT amounts for export sales where a tax rate of 0 percent should have been confirmed during the period but wasn't confirmed.
- **Section 8** – Information from the purchase book.

    - **Section 8.1** – Appendix to Section 8. Information from additional sheets for the purchase book.

- **Section 9** – Information from the sales book.

    - **Section 9.1** – Appendix to Section 9. Information from additional sheets for the sales book.

- **Section 10** – Information about intermediary deals from the Issued factures journal.
- **Section 11** – Information about intermediary deals from the Received factures journal.

For more information, see [Sales books, purchase books, and invoice-factures journals](rus-sales-books-purchase-books.md).

## Section 2 – The VAT amount that must be paid to budget by the tax agent

Section 2 of the VAT declaration contains VAT amounts that are calculated based on tax agent transactions.

For more information, see [Value-added tax (VAT) for tax agents (Russia)](rus-tax-agent.md).

A separate section is created for each tax agent. Each section contains the following information:

- The name of the organization that the legal entity is acting as a tax agent for (line 020)
- The tax registration ID of the type of organization that the legal entity is acting as a tax agent for (line 030)
- The budget classification code (line 040)
- The territory code (line 050)
- The VAT amount that is calculated for tax agent transactions (line 060)
- The VAT operation code (line 070)

## Section 3 – Calculation of VAT amounts that must be paid to budget or reclaimed

Section 3 of the VAT declaration contains the amounts of the registered factures, incoming VAT amounts, and restored VAT amounts from the sales and purchase books, as shown in the following tables. These amounts are automatically generated based on registered documents.

### VAT payable

| Line number | Column number | Name | XML attribute/element name | Description |
|---|---|---|---|---|
| 010 | 3 | Transfer of goods, services and property rights | РеалТов18/НалБаза | The tax base of outgoing customer invoices that have VAT at 18 percent. |
| 010 | 4 | Transfer of goods, services and property rights | РеалТов18/СумНал | The VAT amount of outgoing customer invoices that have VAT at 18 percent. |
| 020 | 3 | Transfer of goods, services and property rights | РеалТов10/НалБаза | The tax base of outgoing customer invoices that have VAT at 10 percent. |
| 020 | 4 | Transfer of goods, services and property rights | РеалТов10/СумНал | The VAT amount of outgoing customer invoices that have VAT at 10 percent. |
| 070 | 3 | Prepayments or partial payments received from customers for future shipments | ОплПредПост/НалБаза | The tax base of factures on prepayments that were received from customers for future shipments. |
| 070 | 4 | Prepayments or partial payments received from customers for future shipments | ОплПредПост/СумНал | The VAT amount of factures on prepayments that were received from customers for future shipments. | 
| 080 | 4 | Tax amounts that were accepted for deduction, which are subject to restoration, total | СумНалВосст/СумНалВс | The amount of restored VAT, based on the following outgoing VAT processing data:<ul><li>Incoming factures that are related to non-taxable shipments for the current reporting period</li><li>Outgoing factures on prepayments that were made to vendors</li><li>Fixed assets that were used in non-taxable operations</li></ul> |
| 090 | 4 | Tax amounts that were accepted for deduction and which are subject to restoration, for prepayments to vendors | СумНалВосст/СумНал170.3.3 | The amount of restored VAT, based on outgoing factures on prepayments that were made to vendors. The VAT restoration occurs in the current reporting period. | 
| 100 | 4 | Tax amounts that were accepted for deduction and which are subject to restoration for operations subject to 0% VAT rate | СумНалВосст/СумНалОперСт0 | The amount of restored VAT for all export factures during the current reporting period. |

### VAT receivable/deductible

| Line number | Column number | Name | XML attribute/element name | Description |
|---|---|---|---|---|
| 120 | 3 | Tax amount accepted during acquisition of goods, services, and property rights that are subject to tax deduction | НалПредНППриоб | The amount of incoming VAT that is subject to reimbursement of factures on purchase invoices. The purchases include goods, services, and property rights that are subject to tax deduction. |
| 130 | 3 | Tax amounts accepted when prepayments are made to vendors for future acquisitions that are subject to tax deduction | НалПредНППок | The amount of incoming VAT that is subject to reimbursement of factures on prepayments that were made to vendors. |
| 150 | 3 | Tax amount that was accepted for deduction when goods were imported for internal consumption | НалУплТамож | The VAT amount of factures of the GTD (Custom declaration) and KTS (Customs values correction) types when goods are imported from territories other than Belarus. |
| 160 | 3 | Tax amount that was accepted for deduction when goods were imported from Belarus | НалУплНОТовТС | The VAT amount of factures of the GTD and KTS types when goods are imported from Belarus. |
| 170 | 3 | Tax amount that was accepted for deduction after delivery of goods to customers | НалИсчПрод | The incoming VAT amount of factures on prepayments that were received from customers for future shipments. The amount is subject to refund after goods are delivered or services are rendered. |
| 180 | 3 | Tax amount that was accepted for deduction for a buyer-tax agent | НалУплПокНА | The VAT amount of factures on tax agent transactions where the **Facture source** value is **Tax correction**. |

In section 3, you can also get the amounts of the financial report that is set up for the VAT declaration.

You should set up the financial report and financial report cells to calculate required cells values. For more information, see [Financial reporting (Russia)](rus-financial-reports.md).

You should define the following names for financial report cells. In this way, the calculated amounts will be automatically exported to section 3 of VAT declaration version 5.05.

**Tax payable**

| Name of cell | Line-column in section 3 |
|---|---|
| РеалТов18НалБаза | 010-3\* |
| РеалТов18СумНал | 010-4\* |
| РеалТов10НалБаза | 020-3\* |
| РеалТов10СумНал | 020-4\* |
| РеалСрок151.1\_118НалБаза | 041-3 |
| РеалСрок151.1\_118СумНал | 041-4 |
| РеалСрок151.1\_110НалБаза | 042-3 |
| РеалСрок151.1\_110СумНал | 042-4 |
| РеалПредИКНалБаза | 050-3 |
| РеалПредИКСумНал | 050-4 |
| ВыпСМРСобНалБаза | 060-3 |
| ВыпСМРСобСумНал | 060-4 |
| ОплПредПостНалБаза | 070-3\* |
| ОплПредПостСумНал | 070-4\* |
| СумНалВосстСумНалВс | 080-4\* |
| СумНалВосстСумНал170.3.3 | 090-4\* |
| СумНалВосстСумНалОперСт0 | 100-4\* |
| КорРеалТов18НалБаза | 105-3 |
| КорРеалТов18СумНал | 105-4 |
| КорРеалТов10НалБаза | 106-3 |
| КорРеалТов10СумНал | 106-4 |
| КорРеалТов118НалБаза | 107-3 |
| КорРеалТов118СумНал | 107-4 |
| КорРеалТов110НалБаза | 108-3 |
| КорРеалТов110СумНал | 108-4 |
| КорРеалПредИКНалБаза | 109-3 |
| КорРеалПредИКСумНал | 109-4 |
| УплДеклар151.1НалБаза | 110-3 |
| УплДеклар151.1СумНал | 110-4 |
| УплДеклар173.6НалБаза | 115-3 |
| УплДеклар173.6СумНал | 115-4 |

**Tax receivable/deductible**

| Name of cell | Line-column in section 3 |
|---|---|
| НалПредНППриоб | 120-3\* |
| НалПредНПКапСтр | 125-3 |
| НалПредНППок | 130-3\* |
| НалИсчСМР | 140-3 |
| НалУплТамож | 150-3\* |
| НалУплНОТовТС | 160-3\* |
| НалИсчПрод | 170-3\* |
| НалУплПокНА | 180-3\* |
| НалВыч171.14 | 185-3 |

> [!NOTE]
> Requisites that are marked with an asterisk (\*) in the preceding tables are automatically calculated based on registered documents, as described earlier in this topic. If you set up financial report cell calculation rules for them, the calculated amounts of the financial report will be added to the automatically calculated amounts. If you want to replace the automatic calculation with the financial report cell calculation, see the [Customize section 3 of the VAT declaration](#customize-section-3-of-the-vat-declaration) section of this topic. You can download a demo setup of the financial report for the VAT declaration from the **RU VAT declaration demo setup** data package in the LCS Shared asset library.

### Customize section 3 of the VAT declaration

In the **VAT declaration model (RU)** ER configuration, section 3 is represented by the **Declaration items** element. In the **VAT declaration model mapping (RU)** ER configuration, this element is bound to the **$RRG.$Section3.$data** data source. This data source is configured as **$RRG.$Section3.$data = LISTJOIN(@.'$dataStd', @.'$dataCustom')**. It refers to two data sources:

- **$RRG.$Section3.$data.$dataStd** – This data source is configured to access the **VAT Declaration helper (RU)** application class by calling the **getSection3data** method. This method produces a list that has the amounts of several boxes in section 3.
- **$RRG.$Section3.$data.$dataCustom** – This data source is configured to access the **LedgerRRGCustomReportHelper\_RU** application class by calling the **getCustomReportData** method. This method produces the record list that has calculated amounts for some financial report cells that were configured by the user.

To customize the declaration, follow one of these steps.

- Set up the financial report to calculate cells that aren't automatically calculated by the **VAT Declaration helper (RU)** class.

    In this case, you should to set up financial report calculation rules for report cells that aren't marked with an asterisk (\*) in the tables in the previous section.

- Set up the financial report to fully calculate cells based on the user setup instead of through automatic calculation.

    In this case, follow these steps:

    1. Set up financial report calculation rules for all required cells, including the cells that marked with an asterisk (\*) in the tables in the previous section.
    2. Create a customized **Model mapping** ER configuration. Derive it from the configuration that is provided by the Microsoft configuration provider.
    3. In the customized **Model mapping** ER configuration that you created in the previous step, redefine the model mapping data source so that it's configured as **$RRG.$Section3.$data = '$dataCustom'** instead of **$RRG.$Section3.$data = LISTJOIN(@.'$dataStd', @.'$dataCustom')**.

- Extend the **VAT Declaration helper (RU)** class (use methods that start with **getSection3data**, such as **getSection3dataDomesticVAT**). Or, in a similar manner, create alternative helper methods that calculate the required cells values.

    In this case, follow these steps:

    1. Create a customized **Model mapping** ER configuration. Derive it from the configuration that is provided by the Microsoft configuration provider.
    2. Redefine the **$RRG.$Section3.$data.$dataStd** data source element of the model mapping.

For more information about how to create a derived version of ER configurations to do customization, see [ER Upgrade your format by adopting a new, base version of that format](../../dev-itpro/analytics/tasks/er-upgrade-format.md).

For more information about how to define model mappings, see [Define ER model mappings and select data sources for them](../../dev-itpro/analytics/tasks/er-define-model-mapping-select-data-sources-2016-11.md).

## Application 1 to section 3

Application 1 contains information about fixed assets that are used in non-taxable activities. It's generated in the last reporting period of the calendar year and contains the restored VAT amount for the fixed asset that was calculated for the whole calendar year. Data for application 1 is generated based on VAT restoration journal entries.

Application 1 contains the following information:

- The name of the fixed asset (line 010)
- The date when the fixed asset was put into operation (line 030)
- The depreciation start date (line 040)
- The initial cost of the fixed asset (line 050)
- The incoming VAT amount that is related to the fixed asset and that was deducted (line 060)
- The year when VAT restoration begins, until the tenth year of depreciation for the fixed asset (line 070, column 1)
- The date when the fixed asset was first used in non-taxable operations (line 070, column 2)
- The percentage of revenue for non-taxable goods and export operations (line 070, column 3)
- The VAT amount that was restored for the fixed asset in a year (line 070, column 4)

## Sections for exports that are taxed at a rate of 0 percent

Before you generate the sections of VAT declaration for exports that are taxed at a rate of 0 percent, follow these steps.

1. Go to **Tax \> Setup \> Sales tax \> VAT operation codes**, and create VAT operation codes for export trade.
2. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**, and assign VAT operation codes to sales tax codes.

### Overview and example

Sections for export are generated based on the registration of export factures and on VAT restoration journal entries. For more information about how to process export transactions, see the "Processing invoice factures for export trade" topic (not currently available).

**Example**

- **January 2018:** Products are purchased and documents Invoice V1 and Facture1 are received.

    - Invoice V1/Facture1: 10 pieces for a total amount of 118,000 Russian rubles (RUB), which includes 18-percent VAT (18,000 RUB)

- **January 2018:** Incoming VAT deduction for Facture1.

    - 82,600 RUB, which includes 18-percent VAT (12,600 RUB)

    Note that the incoming facture includes only some of the goods that were purchased by using invoice V1.

- **April 2018:** Products are sold for export, at an exchange rate of 45 RUB to 1 US dollar (USD).

    - Invoice C1: 2 pieces at 600 USD = 27,000 RUB (The corresponding incoming VAT amount is 3,600 RUB.)
    - Invoice C2: 8 pieces at 2,400 USD = 108,000 RUB (The corresponding incoming VAT amount is 14,400 RUB.)

    In this example, September 2018 is the deadline for collecting all the documents for confirmation of export at a rate of 0 percent.

- **August 2018:** Export for invoice C1 is confirmed before the deadline.
- **September 2018:** Export for invoice C2 isn't confirmed before the deadline. Therefore, VAT for this invoice is calculated at the domestic VAT rate of 18 percent (108,000 × 18 percent = 19,440 RUB).

    The amount of the corresponding incoming VAT deduction for the unconfirmed export is 9,000 RUB.

- **November 2018:** Facture2 is received for the remaining goods that were purchased by using invoice V1. Therefore, the incoming VAT deduction for the remaining part of invoice V1 is posted.

    - 35,400 RUB, which includes 18-percent VAT (5,400 RUB) (This amount is for the goods that were purchased by using invoice C2.)

The VAT declaration for the third quarter of 2018 will contain Section 4 and Section 6.

The VAT declaration for the fourth quarter of 2018 will contain Section 5.

The following sections provide more details for this example.

### Section 4 – Calculation of VAT amounts for export sales where a tax rate of 0 percent was confirmed during the period

Section 4 of the VAT declaration represents amounts for export factures if a rate of 0 percent was confirmed during the reporting period. Data is grouped by VAT operation code.

The following data is exported:

- The VAT operation code (line 010)
- The tax base (line 020)
- The deductible VAT amount from the purchase of items that are used in an export that was confirmed at a rate of 0 percent (line 030)
- Adjustment: The deductible VAT amount that was paid in previous periods when a rate of 0 percent wasn't yet confirmed (line 040)
- Adjustment: The restored VAT amount that was deducted in previous periods for an unconfirmed export (line 050)

If goods are returned, the following data is exported for corrections of amounts:

- The VAT operation code (line 060)
- The tax base (line 070)

**Example**

For the previous example, the following data will be present in section 4 of the VAT declaration for the third quarter of 2018.

| Requisite | Line | Value |
|---|---|---|
| VAT operation code | 010 | 1011410 (per the user setup for the appropriate sales tax code) |
| Tax base | 020| 27,000 |
| Deductible VAT amount from the purchase of items that are used in an export that was confirmed at a rate of 0 percent | 030 | 3,600 |

### Section 5 – Calculation of deductible VAT amounts for the reporting period, for export sales where a tax rate of 0 percent was either confirmed or unconfirmed in previous periods

Section 5 of the VAT declaration represents VAT amounts deductible in the reporting period for export sales where a rate of 0 percent was either confirmed or unconfirmed in previous periods (that is, "later" deductions of VAT amounts). Data is grouped by the period when the corresponding export was declared, and also by VAT operation code.

The following data is exported:

- The year when the corresponding export was declared (line 010)
- The code for the reporting period when the corresponding export was declared (line 020)
- The VAT operation code (line 030)
- The tax base from the purchase of items that are used in a confirmed export (line 040)
- The deductible VAT amount from the purchase of items that are used in a confirmed export (line 050)
- The tax base from the purchase of items that are used in an unconfirmed export (line 060)
- The deductible VAT amount from the purchase of items that were used in an unconfirmed export (line 070)

**Example**

For the earlier example, the following data will be present in section 5 of the VAT declaration for the fourth quarter of 2018.

| Requisite | Line | Value |
|---|---|---|
| Year when the corresponding export was declared | 010 | 2018 |
| Code for the reporting period when the corresponding export was declared | 020 | 23 (period code for the third quarter) |
| VAT operation code | 030 | 1011410 |
| The tax base from the purchase of items that are used in an unconfirmed export | 060 | 108,000 |
| THe deductible VAT amount from the purchase of items that are used in an unconfirmed export | 070 | 5,400 |

### Section 6 – Calculation of VAT amounts for export sales where a tax rate of 0 percent should have been confirmed during the period but wasn't confirmed

Section 6 of the VAT declaration represents amounts for export factures if a rate of 0 percent wasn't confirmed, and if the deadline expired during the reporting period. Data is grouped by VAT operation code.

The following data is exported:

- The VAT operation code (line 010)
- The tax base (line 020)
- The VAT amount payable that is calculated from the tax base for an unconfirmed export (line 030)
- The deductible VAT amount from the purchase of items that are used in an unconfirmed export (line 040)

Corrections of amounts for the return of goods:

- The VAT operation code (line 070)
- The tax base of the return of goods (line 080)
- The VAT amount of the return of goods that is decreasing the VAT amount payable (line 090)
- Adjustment: The VAT amount, from the purchase of items that are used in an export, that was previously deducted and must be restored for the return of goods (line 100)

For the earlier example, the following data will be present in section 6 of the VAT declaration for the third quarter of 2018.

| Requisite | Line | Value |
|---|---|---|
| VAT operation code | 010 | 1011410 (per the user setup for the appropriate sales tax code) |
| Tax base | 020 | 108,000 |
| VAT amount payable that is calculated from the tax base for the unconfirmed export | 030 | 19,440 |
| The deductible VAT amount from the purchase of items that are used in an unconfirmed export | 040 | 9,000 |

## Additional resources

[How to start working with VAT declaration](https://support.microsoft.com/help/4477332/rusrussiavatdeclarationinelectronicformat)
