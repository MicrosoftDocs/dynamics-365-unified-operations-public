---
title: SAF Accounting Books Income Tax - JPK_KR_PD
description: Users in legal entities in Poland can generate a SAF Accounting Books Income Tax - JPK_KR_PD in XML format and preview in Excel.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF Accounting Books Income Tax - JPK_KR_PD

[!include [banner](../../includes/banner.md)]

The JPK_KR_PD (Jednolity Plik Kontrolny – Księgi Rachunkowe Podatnika) is a new mandatory reporting standard in Poland, 
requiring taxpayers to submit detailed accounting books in a structured electronic format. 
This requirement is mandatory for businesses starting January 1, 2025.
Large taxpayers need to report the new JPK_KR_PD for the first time in March 2026, in line with the deadline for filing their 2025 tax return. 

> [!NOTE]
> Previouse version of SAF Accounting books (JPK_KR) report is required for reporting periods before January 1, 2025. For more information about how to set up and generate JPK_KR to report for periods before January 1, 2025, see [SAF Accounting Books - JPK_KR](emea-pol-standard-audit-file-saf-kr.md).
> The SAF Accounting books (JPK_KR) report will be deprecated as of Janury 1, 2026. For deprecation announcement of SAF Accounting books (JPK_KR), see [Removed or deprecated features in Dynamics 365 Finance in the Finance 10.0.43 release](https://learn.microsoft.com/en-us/dynamics365/finance/get-started/removed-deprecated-features-finance#features-removed-or-deprecated-in-the-finance-10043-release)

## Setup

Before you can generate a SAF Accounting Books Income Tax report, you must complete the following setup.

1. [Import Electronic reporting configurations](#er-import)
2. [Set up Electronic reporting format in General ledger parameters](#er-format-setup)
3. [Set up sales tax authority](#tax-authorities)
4. [Set up consolidation accounting groups](#consolidation-accounting-groups)
5. [Configure Application-specific parameters for the format of the report](#asp-setup)

### <a id="er-import"></a> Import Electronic reporting configurations

In Finance, import the following Electronic reporting (ER) configurations from Dataverse.

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name       | Type          | Description |
|-----------------------------|---------------|-------------|
| Standard Audit File (SAF-T) | Model         | The common data model for different audit reports. |
| General ledger data model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| JPK_KR_PD XML (PL) - *Preview*  | Format        | *Preview* (Preview) Standard Audit File Accounting Books Income Tax, JPK_KR_PD. |

> [!NOTE]
> The **JPK_KR_PD XML (PL) - Preview** is provided solely for early adoption and preparatory purposes regarding the new reporting requirements.
> Please note that this preview does not include the RDP component and is subject to further updates.
> It will eventually be replaced with the finalized "JPK_KR_PD XML (PL)" format.
> Users are advised to use this version for preliminary familiarization only.

Import the most recent versions of the configurations. 
The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> In case your organization is using other JPK reports and **Standard Audit File model mapping** configuration is set as **Default for model mapping**,
> you can keep this setting and **JPK_KR_PD XML (PL)** format will use the **General ledger data model mapping** automatically, when run from **SAF Accounting Book Income Tax** menu item.
>
> To run **JPK_KR_PD XML (PL)** format from other places in your Dynamics 365 Finance, set the **General ledger data model mapping** as **Default for model mapping**. 

### <a id="er-format-setup"></a> Set up Electronic reporting format in General ledger parameters

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF Accounting Books Income Tax** field, select the ER format, **JPK_KR_PD XML (PL)**. 

### <a id="tax-authorities"></a> Set up sales tax authority

For general information about how to set up a sales tax authority, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md). 
To generate a JPK_KR_PD in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities. 

1. On the **Sales tax authorities** page (**Tax > Indirect taxes > Sales tax > Sales tax authorities**), 
set the **Report layout** field to **Default**. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.
2. In the **Authority identification** specify the the code of the tax office competent for the taxpayer's registered office, that will be reported in `<KodUrzedu>` field of JPK_KR_PD.

### <a id="consolidation-accounting-groups"></a> Set up consolidation accounting groups

Depending on business needs of your organization you may need to include following information in `ZOiS` (Turnover and balance statement) part of the JPK_KR_PD report.

| ZOiS field | Description En | Description PL |
|-----------|-------------|--------------|
| **S_12_1** | Account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field for entities applying IFRS) | Znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne dla jednostek stosujących MSSF) |
| **S_12_2** | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne) |
| **S_12_3** | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (PD) (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (PD) (pole opcjonalne) |
 
In addition to this requirement, if your organization employs a non-standard chart of accounts in Poland, the JPK_KR_PD must reflect information aligned with the standard chart of accounts used in Poland.

Use the [Consolidation account groups and additional consolidation accounts](../../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create the association of main accounts in your Finance and applicable values of S_12_1, S_12_2, S_12_3 and standard main accounts in Poland.

1. Create a [consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group that's named **S_12_3**.
2. [Add accounts to the consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify the applicable value of S_12_3 enumeration. This value is reported in the **S_12_3** element of JPK_KR_PD in the **ZOiS** section.

You must create as many consolidation account groups as necessary to cover the different account tag enumeration lists applicable to your organization's business operations. If your organization uses a non-standard chart of accounts in Poland, you should create a separate consolidation account group to establish the association between the main accounts and the standard chart of accounts used in Poland.

### <a id="asp-setup"></a> Configure Application-specific parameters for the format of the report

Application-specific parameters of JPK_KR_PD format in Electronic Reporting (ER) facilitate the mapping of your financial data to the required values defined by the JPK_KR_PD schema.

To prepare your Finance for generating JPK_KR_PD in compliance with the required schema, follow these steps.

1. Open the **Electronic reporting workspace**, and then, in the configuration tree, select **Standard Audit File (SAF-T) \> JPK_KR_PD XML (PL)**.
2. On the Action Pane, select **Configurations \> Applications specific parameters \> Setup**.
3. Select the latest version of the format on the left hand side of **Application specific parameters** page.
4. On the **Lookups** FastTab, select the lookup field. Detailed description of all the lookup fields of the JPK_KR_PD XML (PL) format is provided further in this topic.
5. On the **Conditions** FastTab, define the required conditions and specify the values in the **Lookup result** column.
6. As the last two lines, add lines that have the conditions **Not blank** and **Blank** where applicable.
7. Select the next lookup field from the list on the **Lookups** FastTab and repeat the steps 5 and 6.
8. When all the lookup fields are set up, in the **State** field, select **Completed**, and save the configuration.

#### OpisDziennika - Journal description

Use the free-text **OpisDziennika** lookup field to define mapping of journal description of general journal entries in your Fiannce to the values that will be reported in D_2 field of JPK_KR_PD.

| ZOiS field | Description En | Description Pl |
|-----|-----|----|
| D_2 | Journal description - character field. Partial journals used by the entity as an element of accounting records in accordance with art. 14 sec. 3 and 4 of the Accounting Act. | Opis dziennika - pole znakowe. Dzienniki częściowe stosowane przez jednostkę, jako element ksiąg rachunkowych zgodnie z art. 14 ust. 3 i 4 UoR. Powinny one zostać opatrzone nazwą np. Zakup, Sprzedaż |

The following condition is available for mapping in this lookup field.

| Condition | Description |
|-----------|-----------|
| Original Document Type (OriginalDocumentType) | Select original document types that are used in your busines oprations and and specify in the **Lookup result** field how they should be reported in JPK_KR_PD \> Dziennik.  |

As the last two lines, add lines that have the conditions **Not blank** and **Blank**.

#### ZOiSTyp - Turnover and balance statement type

Use the **ZOiSTyp** lookup field to define the type of ZOiS applicable for your organization. In **Lookup result** column select **ZOiSTyp** and then in **Turnover and balance statement type** column, select which ZOiS type is applicable for your organization. The following values are available.

| ZOiSTyp | Description Pl | Description En |
|-----|-----|----|
| ZOiS1 |  Zestawienie obrotów i sald dla banków | Turnover and balance statement for banks |
| ZOiS2 | Zestawienie obrotów i sald dla ubezpieczycieli i zakładów reasekuracji | Turnover and balance statement for insurers and reinsurers |
| ZOiS3 | Zestawienie obrotów i sald dla organizacji pożytku publicznego i wolontariatu | Turnover and balance statement for public benefit and volunteer organizations |
| ZOiS4 | Zestawienie obrotów i sald dla funduszy inwestycyjnych | Turnover and balance statement for investment funds |
| ZOiS5 | Zestawienie obrotów i sald dla domów maklerskich | Turnover and balance statement for brokerage houses |
| ZOiS6 | Zestawienie obrotów i sald dla SKOK | Turnover and balance statement for SKOK |
| ZOiS7 | Zestawienie obrotów i sald dla jednostek pozostałych | Turnover and balance statement for other entities |
| ZOiS8 | Zestawienie obrotów i sald dla jednostek stosujących MSSF | Turnover and balance statement for entities applying IFRS|

#### KodUrzedu - Tax authority identification

Use the **KodUrzedu** lookup field to define the tax authority to be reported in `<KodUrzedu>` field. 
In **Lookup result** column select **KodUrzedu** and then in **Tax authority identification** column, select which tax authorty set up in your legal entity will be used in the report.

#### PodatnikZnacznik - Taxpayer tag

Use the **PodatnikZnacznik** lookup field to specify the tag aplicable to your organization.
In **Lookup result** column select **PodatnikZnacznik** and then in **Taxpayer tag** column, select which tag is aplicable to your organization. The following values are available.

| Taxpayer tag (Tag) | Description Pl | Description En |
|-----|-----|----|
| EstonianCIT | Znacznik dla podatnika CIT estońskiego | Tag for Estonian CIT taxpayer |
| IFRS | Znacznik dla podatnika stosującego MSSF | Tag for taxpayer using IFRS |
| StandardPL | Standardowy polski CIT | Standart Polish CIT |

#### ZnacznikKonta - Account tags and Polish chart of accounts

Use the **ZnacznikKonta** lookup field to define which of the previously set up consolidation accounting groups that are appicable to your organization applicable should be reported in which fields of JPK_KR_PD.

In **Lookup result** column select the report tag ot **PL_CoA** for standard chart of accounts and then in **Consolidation group** column, select which consolidation accounting group should be used for the tag selected. The following lookup result values are available:

| Lookup field | Description En | Description PL |
|-----------|-------------|--------------|
| **S_12_1** | Account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field for entities applying IFRS) | Znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne dla jednostek stosujących MSSF) |
| **S_12_2** | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne) |
| **S_12_3** | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (PD) (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (PD) (pole opcjonalne) |
| **PL_CoA** | Consolidation account groups for Polish chart of accounts | Grupy kont konsolidacyjnych dla polskiego planu kont | 

#### RodzajDowodu - Accounting voucher type

Use the free-text **RodzajDowodu** lookup field to define mapping of the type of accounting voucher of general journal entries in your Fiannce to the values that will be reported in D_5 field of JPK_KR_PD.

| ZOiS field | Description En | Description Pl |
|-----|-----|----|
| D_5 | Type of accounting document (which is the basis for the accounting entry, as referred to in art. 23 sec. 2 item 2 of the Accounting Act) placed on the accounting document by the issuer, in accordance with art. 21 sec. 1 item 1 of the Accounting Act. | Rodzaj dowodu księgowego (który stanowi podstawę zapisu księgowego, o czym mowa w art. 23 ust. 2 pkt 2 UoR) umieszczony na dowodzie księgowym przez wystawcę, zgodnie z art. 21 ust. 1 pkt 1 UoR (pole znakowe). |

The following condition is available for mapping in this lookup field.

| Condition | Description |
|-----------|-----------|
| Original Document Type (OriginalDocumentType) | Select original document types that are used in your busines oprations and and specify in the **Lookup result** field how they should be reported in JPK_KR_PD \> Dziennik.  |

As the last two lines, add lines that have the conditions **Not blank** and **Blank**.

## <a id="jpk-kr"></a> Generate a Standard Audit File Accounting Books Income Tax file (JPK_KR_PD)

To generate a Standard Audit File Accounting Books Income Tax - JPK_KR_PD file, click **General ledger > Inquiries and reports > Standard Audit File for Tax (SAF-T) > Standard Audit File Accounting Books Income Tax**, and set the following parameters.

| Parameter                                   | Description |
|---------------------------------------------|-------------|
| From date                                   | Specify the first date to export reporting data for. |
| To date                                     | Specify the last date to export reporting data for. |
| Print with zero balances | By default, the ZOiS section of JPK_KR_PD includes main accounts with a non-zero opening balance and/or transactions within the reporting period. Select this checkbox if you also want to include main accounts with a zero opening balance and no turnover during the reporting period. | 
| Purpose of submission | Select what is the relevant purpose of the report submission. The following values are available: <li> JPK for the first time, <li> JPK correction. |
| Report composition | Select one or many sections of the report that you want to generate: <li> ZOiS <li> Dziennik (includes Dziennik, KontoZapis, Ctrl, Kontrahent) <li> RPD.   |
| Include closing transactions                | If this parameter is selected, closing transactions will be included in the data that is exported. |
| Include reversal | If this parameter is selected, reversed transactions will be included in the data that is exported. |
| Posting layer                               | Select one or more posting layers from which to consider transactions. This parameter affects all parts of the report. |
| Update balances | Select this checkbox to update balances before the report generation.  |

## Using batch jobs for JPK_KR_PD

Generating JPK_KR_PD report for a long period such as month or a quarter can include a huge data and take a long time. 
For such cases, it is recommended to use batch jobs. 
Dialog page for every SAF report has a **Run in the background** tab. 
Open this tab to set up report's generation in batch mode. Select **Batch processing** check box. 
To learn more about batch processing, see [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md). To review batch jobs or find a generated file, go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**, and find a line related to your job. Select **Show log** on the **Main menu**. If nothing is shown, no messages were produced when the file was generated. To see the file, select **Show files** on the **Main menu**, find a file that you need, and select **Open** on the **Main menu**.  

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as 
an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**. 
For more information about how to configure a destination for each ER format configuration and its output component, 
see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
