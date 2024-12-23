---
title: SAF Accounting Books Income Tax - JPK_KR_PD
description: This article explains how users in legal entities in Poland can generate a SAF Accounting Books Income Tax - JPK_KR_PD in XML format.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 11/26/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF Accounting Books Income Tax - JPK_KR_PD

[!include [banner](../../includes/banner.md)]

This article explains how users in legal entities in Poland can generate a SAF Accounting Books Income Tax - JPK_KR_PD in XML format.

JPK_KR_PD (Jednolity Plik Kontrolny – Księgi Rachunkowe Podatnika) is a new reporting standard in Poland that is mandatory for businesses as of January 1, 2025. It requires that taxpayers submit detailed accounting books in a structured electronic format. Large taxpayers must report the new SAF Accounting Books Income Tax - JPK_KR_PD for the first time in March 2026, which is their deadline for filing their 2025 tax returns.

> [!NOTE]
> For reporting periods before January 1, 2025, the earlier SAF Accounting Books - JPK_KR is required. Learn more about how to set up and generate a SAF Accounting Books - JPK_KR to report for periods before January 1, 2025, in [SAF Accounting Books - JPK_KR](emea-pol-standard-audit-file-saf-kr.md).
>
> As of January 1, 2026, the SAF Accounting Books - JPK_KR will be deprecated. You can find the deprecation announcement in [Removed or deprecated features in Dynamics 365 Finance in the Finance 10.0.43 release](/dynamics365/finance/get-started/removed-deprecated-features-finance#features-removed-or-deprecated-in-the-finance-10043-release).

## Setup

Before you can generate a SAF Accounting Books Income Tax - JPK_KR_PD, you must complete the following setup.

1. [Import Electronic reporting (ER) configurations](#er-import).
1. [Set up the ER format in General ledger parameters](#er-format-setup).
1. [Set up a sales tax authority](#tax-authorities).
1. [Set up consolidation accounting groups](#consolidation-accounting-groups).
1. [Configure application-specific parameters for the format of the report](#asp-setup).

### <a id="er-import"></a>Import ER configurations

In Microsoft Dynamics 365 Finance, import the following ER configurations from Dataverse. Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name | Type | Description |
|---|---|---|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| General ledger data model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| JPK_KR_PD XML (PL) - *Preview* | Format | (Preview) Standard Audit File Accounting Books Income Tax, JPK_KR_PD. |

> [!NOTE]
> The **JPK_KR_PD XML (PL) - Preview** ER configuration is provided only for early adoption and preparation for the new reporting requirements. This preview doesn't include the RDP component and is subject to further updates. It will eventually be replaced with the finalized **JPK_KR_PD XML (PL)** format. We recommend that users use this version only for preliminary familiarization.

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> If your organization is using other JPK reports, and the **Default for model mapping** option is set to **Yes** for the **Standard Audit File model mapping** configuration, you can keep that setting. In this case, when the **JPK_KR_PD XML (PL)** format is run from the **SAF Accounting Book Income Tax** menu item, it automatically uses the **General ledger data model mapping** configuration. To run the **JPK_KR_PD XML (PL)** format from other places in Finance, set the **Default for model mapping** option to **Yes** for the **General ledger data model mapping** configuration instead.

### <a id="er-format-setup"></a>Set up the ER format in General ledger parameters

To set up the ER format in General ledger parameters, follow these steps.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF Accounting Books Income Tax** field, select the **JPK_KR_PD XML (PL)** ER format.

### <a id="tax-authorities"></a>Set up a sales tax authority

You can find general information about how to set up a sales tax authority in [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).

To generate a SAF Accounting Books Income Tax - JPK_KR_PD in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities.

To set up the report layout for sales tax authorities, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
1. Set the **Report layout** field to **Default**.
1. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.
1. In the **Authority identification** field, specify the code of the tax office competent for the taxpayer's registered office. This code will be reported in the **\<KodUrzedu\>** field of the SAF Accounting Books Income Tax - JPK_KR_PD.

### <a id="consolidation-accounting-groups"></a>Set up consolidation accounting groups

Depending on the business needs of your organization, you might have to include the following information in the **ZOiS** (Turnover and balance statement) part of the SAF Accounting Books Income Tax - JPK_KR_PD.

| ZOiS field | Description (English) | Description (Polish) |
|---|---|---|
| S_12_1 | Account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field for entities applying IFRS) | Znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne dla jednostek stosujących MSSF) |
| S_12_2 | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne) |
| S_12_3 | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (PD) (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (PD) (pole opcjonalne) |

In addition to this requirement, if your organization uses a non-standard chart of accounts in Poland, the SAF Accounting Books Income Tax - JPK_KR_PD must reflect information that is aligned with the standard chart of accounts that is used in Poland.

Use the [Consolidation account groups and additional consolidation accounts](../../budgeting/consolidation-account-groups-consolidation-accounts.md) functionality to create the association between main accounts in Finance and applicable values of **S_12_1**, **S_12_2**, **S_12_3**, and standard main accounts in Poland.

1. Create a [consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#create-a-consolidation-account-group). For example, create a group that is named **S_12_3**.
1. [Add accounts to the consolidation account group](../../general-ledger/tasks/create-consolidation-groups.md#add-accounts-to-consolidation-account-group). In the **Consolidation account** field, specify the applicable value of the **S_12_3** enumeration. This value is reported in the **S_12_3** element in the **ZOiS** section of the SAF Accounting Books Income Tax - JPK_KR_PD.

You must create as many consolidation account groups as are required to cover the different account tag enumeration lists that are applicable to your organization's business operations. If your organization uses a non-standard chart of accounts in Poland, you should create a separate consolidation account group to establish the association between the main accounts and the standard chart of accounts that is used in Poland.

### <a id="asp-setup"></a>Configure application-specific parameters for the format of the report

Application-specific parameters of the **JPK_KR_PD** format in ER facilitate the mapping of your financial data to the required values that are defined by the **JPK_KR_PD** schema.

To prepare Finance to generate a SAF Accounting Books Income Tax - JPK_KR_PD in compliance with the required schema, follow these steps.

1. Open the **Electronic reporting** workspace**.
1. In the configuration tree, select **Standard Audit File (SAF-T)** \> **JPK_KR_PD XML (PL)**.
1. On the Action Pane, on the **Configurations** tab, in the **Applications specific parameters** group, select **Setup**.
1. On the left side of **Application specific parameters** page, select the latest version of the format.
1. On the **Lookups** FastTab, select a lookup field in the list. Detailed descriptions of all the lookup fields of the **JPK_KR_PD XML (PL)** format are provided after this procedure.
1. On the **Conditions** FastTab, define the required conditions, and specify the values in the **Lookup result** column.
1. As the last two lines, add lines that have the conditions **Not blank** and **Blank** where applicable.
1. Repeat steps 5 through 7 for each additional lookup field.
1. When all the lookup fields are set up, select **Completed** in the **State** field, and save the configuration.

#### OpisDziennika - Journal description

Use the free-text **OpisDziennika** lookup field to define the mapping of the journal description of general journal entries in Finance to the values that will be reported in the **D_2** field of the SAF Accounting Books Income Tax - JPK_KR_PD.

| ZOiS field | Description (English) | Description (Polish) |
|---|---|---|
| D_2 | Journal description - character field. Partial journals used by the entity as an element of accounting records in accordance with art. 14 sec. 3 and 4 of the Accounting Act. | Opis dziennika - pole znakowe. Dzienniki częściowe stosowane przez jednostkę, jako element ksiąg rachunkowych zgodnie z art. 14 ust. 3 i 4 UoR. Powinny one zostać opatrzone nazwą np. Zakup, Sprzedaż |

The following condition is available for mapping in this lookup field.

| Condition | Description |
|---|---|
| Original Document Type (OriginalDocumentType) | Select the original document types that are used in your business operations. In the **Lookup result** field, specify how they should be reported in the **Dziennik** section of the SAF Accounting Books Income Tax - JPK_KR_PD. |

As the last two lines, add lines that have the conditions **Not blank** and **Blank**.

#### ZOiSTyp - Turnover and balance statement type

Use the **ZOiSTyp** lookup field to define the type of ZOiS that is applicable for your organization. In the **Lookup result** column, select **ZOiSTyp**. Then, in the **Turnover and balance statement type** column, select which ZOiS type is applicable for your organization. The following values are available.

| ZOiS type | Description (English) | Description (Polish) |
|---|---|---|
| ZOiS1 | Turnover and balance statement for banks | Zestawienie obrotów i sald dla banków |
| ZOiS2 | Turnover and balance statement for insurers and reinsurers | Zestawienie obrotów i sald dla ubezpieczycieli i zakładów reasekuracji |
| ZOiS3 | Turnover and balance statement for public benefit and volunteer organizations | Zestawienie obrotów i sald dla organizacji pożytku publicznego i wolontariatu |
| ZOiS4 | Turnover and balance statement for investment funds | Zestawienie obrotów i sald dla funduszy inwestycyjnych |
| ZOiS5 | Turnover and balance statement for brokerage houses | Zestawienie obrotów i sald dla domów maklerskich |
| ZOiS6 | Turnover and balance statement for SKOK | Zestawienie obrotów i sald dla SKOK |
| ZOiS7 | Turnover and balance statement for other entities | Zestawienie obrotów i sald dla jednostek pozostałych |
| ZOiS8 | Turnover and balance statement for entities applying IFRS| Zestawienie obrotów i sald dla jednostek stosujących MSSF |

#### KodUrzedu - Tax authority identification

Use the **KodUrzedu** lookup field to define which tax authority should be reported in the **\<KodUrzedu\>** field. In the **Lookup result** column, select **KodUrzedu**. Then, in the **Tax authority identification** column, select which of the tax authorities that are set up in your legal entity should be used on the report.

#### PodatnikZnacznik - Taxpayer tag

Use the **PodatnikZnacznik** lookup field to specify the tag that is applicable to your organization. In the **Lookup result** column, select **PodatnikZnacznik**. Then, in the **Taxpayer tag** column, select which tag is applicable to your organization. The following values are available.

| Taxpayer tag (Tag) | Description (English) | Description (Polish) |
|---|---|---|
| EstonianCIT | Tag for Estonian CIT taxpayer | Znacznik dla podatnika CIT estońskiego |
| IFRS | Tag for taxpayer using IFRS | Znacznik dla podatnika stosującego MSSF |
| StandardPL | Standart Polish CIT | Standardowy polski CIT |

#### ZnacznikKonta - Account tags and Polish chart of accounts

Use the **ZnacznikKonta** lookup field to define which of the previously set up consolidation accounting groups that are applicable to your organization should be reported in which fields of the SAF Accounting Books Income Tax - JPK_KR_PD. In the **Lookup result** column, select the **PL_CoA** report tag for the standard chart of accounts. Then, in the **Consolidation group** column, select which consolidation accounting group should be used for the selected tag. The following lookup result values are available.

| Lookup field | Description (English) | Description (Polish) |
|---|---|---|
| S_12_1 | Account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field for entities applying IFRS) | Znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne dla jednostek stosujących MSSF) |
| S_12_2 | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (pole opcjonalne) |
| S_12_3 | Additional account tag resulting from the regulation on the additional scope of data to be supplemented in the accounting records (PD) (optional field) | Dodatkowy znacznik konta wynikający z rozporządzenia w sprawie dodatkowego zakresu danych, o które należy uzupełnić prowadzone księgi rachunkowe (PD) (pole opcjonalne) |
| PL_CoA | Consolidation account groups for Polish chart of accounts | Grupy kont konsolidacyjnych dla polskiego planu kont | 

#### RodzajDowodu - Accounting voucher type

Use the free-text **RodzajDowodu** lookup field to define the mapping of the type of accounting voucher of general journal entries in Finance to the values that should be reported in the **D_5** field of the SAF Accounting Books Income Tax - JPK_KR_PD.

| ZOiS field | Description (English) | Description (Polish) |
|---|---|---|
| D_5 | Type of accounting document (which is the basis for the accounting entry, as referred to in art. 23 sec. 2 item 2 of the Accounting Act) placed on the accounting document by the issuer, in accordance with art. 21 sec. 1 item 1 of the Accounting Act. | Rodzaj dowodu księgowego (który stanowi podstawę zapisu księgowego, o czym mowa w art. 23 ust. 2 pkt 2 UoR) umieszczony na dowodzie księgowym przez wystawcę, zgodnie z art. 21 ust. 1 pkt 1 UoR (pole znakowe). |

The following condition is available for mapping in this lookup field.

| Condition | Description |
|---|---|
| Original Document Type (OriginalDocumentType) | Select the original document types that are used in your business operations. In the **Lookup result** field, specify how they should be reported in the **Dziennik** section of the SAF Accounting Books Income Tax - JPK_KR_PD. |

As the last two lines, add lines that have the conditions **Not blank** and **Blank**.

## <a id="jpk-kr"></a>Generate a SAF Accounting Books Income Tax - JPK_KR_PD

To generate a SAF Accounting Books Income Tax - JPK_KR_PD, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File Accounting Books Income Tax**, set the following parameters, and then select **OK**.

| Parameter | Description |
|---|---|
| From date | Specify the first date to export reporting data for. |
| To date | Specify the last date to export reporting data for. |
| Print with zero balances | By default, the **ZOiS** section of the SAF Accounting Books Income Tax - JPK_KR_PD includes main accounts that have a non-zero opening balance and/or transactions in the reporting period. Select this checkbox if you also want to include main accounts that have a zero opening balance and no turnover during the reporting period. | 
| Purpose of submission | <p>Select one of the following values to specify the purpose of the report submission:</p><ul><li>JPK for the first time</li><li>JPK correction</li></ul> |
| Report composition | <p>Select one or more of the following values to specify the sections of the report that you want to generate:</p><ul><li>ZOiS</li><li>Dziennik (includes Dziennik, KontoZapis, Ctrl, Kontrahent)</li><li>RPD</li></ul> |
| Include closing transactions | Select this parameter to include closing transactions in the data that is exported. |
| Include reversal | Select this parameter to include reversed transactions in the data that is exported. |
| Posting layer | Select one or more posting layers to consider transactions from. This parameter affects all parts of the report. |
| Update balances | Select this checkbox to update balances before report generation. |

## Using a batch job to generate a SAF Accounting Books Income Tax - JPK_KR_PD

A SAF Accounting Books Income Tax - JPK_KR_PD for a long period, such as a month or a quarter, can include a large amount of data and take a long time to be generated. Therefore, we recommend that you use batch jobs. The dialog box for every SAF report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.

Learn more about how to configure a destination for each ER format configuration and its output component in [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).
