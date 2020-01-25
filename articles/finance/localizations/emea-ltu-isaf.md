---
# required metadata

title: i.SAF reporting for Lithuania
description: This topic explains how to set up and work with i.SAF report for legal entities in Lithuania.
author: 
manager: AnnBe
ms.date: 25/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 266884
ms.search.region: Lithuania
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# i.SAF reporting for Lithuania

[!include [banner](../includes/banner.md)]

This topic explains how to set up and work with i.SAF report for legal entities in Lithuania.

## Introduction

According to the Order No VA-55 "On the Approval of Rules for the Processing and Submitting of the Data Taxes Invoice Registers", approved by the Head of the State Tax Inspectorate under the Ministry of Finance of the Republic of Lithuania in 2004, April 21 the processing and submission of data about value added tax invoice registers is updated to create conditions for the taxable persons to e-way present the data of issued and received invoices for the Tax Authority using standardized format for i.SAF application. i.SAF format must match the current standard of accounting data files technical specifications and technical requirements (FileVersion iSAF1.2).

## Overview

This document is a guidance for users of Microsoft Dynamics 365 Finance.

This guidance describes how to set up Electronic Reporting (ER) configurations for i.SAF report, how to set up and use Electronic Messages functionality (EM).

The document includes following parts:

•	Import and set up ER configurations and application-specific parameters

•	Set up EM functionality

•	Work with EM functionality to prepare i.SAF report.

## Import and set up Electronic Reporting configurations

To prepare Finance to i.SAF reporting, you must import the following ER configurations.

| Configuration name	| Configuration type |
|---------------------|--------------------|
| Invoices Communication Model	| Data model |
| i.SAF model mapping	| Model mapping |
| i.SAF format (LT) |	Format	|

Import the latest versions of these configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!NOTE]
> After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for the following configurations:
>
> - **Tax declaration model mapping**.

For more information about how to download ER configurations from Microsoft Dynamics Lifecycle Services (LCS), see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Standard VAT codes and application-specific parameters setup

Table 1 “VAT table” of the **“Tables of the Technical Specification of the Standard Accounting Data File”** (here and further “Standard VAT codes”) defines the following "Standard VAT codes" to be used by companies in Lithuania:



| **Standard VAT code** | **Description**                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PVM1                  | Goods and/or services supplied within the territory of the country (Article 19(1) of the Law of the Republic of Lithuania on Value Added Tax (hereinafter – LVAT))                                                                                                                                                                                                                                 |
| PVM2                  | Goods and/or services supplied within the territory of the country (Article 19(3) of the LVAT)                                                                                                                                                                                                                                                                                                     |
| PVM3                  | Goods and/or services supplied within the territory of the country (Article 19(4), (5) of the LVAT)                                                                                                                                                                                                                                                                                                |
| PVM4                  | Cases where the buyer must withhold and pay VAT on goods and services supplied to him (Article 96 of the LVAT) Exp. on 2016-03-31                                                                                                                                                                                                                                                                  |
| PVM25                 | Cases where the buyer must withhold and pay VAT on goods and services supplied to him (Article 96 of the LVAT) Rate 21%                                                                                                                                                                                                                                                                            |
| PVM26                 | Cases where the buyer must withhold and pay VAT on goods and services supplied to him (Article 96 of the LVAT) Rate 9%                                                                                                                                                                                                                                                                             |
| PVM27                 | Cases where the buyer must withhold and pay VAT on goods and services supplied to him (Article 96 of the LVAT) Rate 5%                                                                                                                                                                                                                                                                             |
| PVM5                  | Cases of supplies of goods and services exempt from VAT (Articles 20–33 and 112 of the LVAT)                                                                                                                                                                                                                                                                                                       |
| PVM6                  | Cases of supplies of goods (services) for private use of a VAT payer (Articles 5 and 6 of the LVAT) Rate 21%                                                                                                                                                                                                                                                                                       |
| PVM7                  | Cases of supplies of goods (services) for private use of a VAT payer (Articles 5 and 6 of the LVAT) Rate 9%                                                                                                                                                                                                                                                                                        |
| PVM8                  | Cases of supplies of goods (services) for private use of a VAT payer (Articles 5 and 6 of the LVAT) Rate 5%                                                                                                                                                                                                                                                                                        |
| PVM28                 | Cases of supplies of goods (services) for private use of a VAT payer (Articles 5 and 6 of the LVAT) Rate 0%                                                                                                                                                                                                                                                                                        |
| PVM29                 | Cases of supplies of goods (services) for private use of a VAT payer (Articles 5 and 6 of the LVAT) Rate -                                                                                                                                                                                                                                                                                         |
| PVM9                  | Manufacture of tangible fixed assets by a VAT payer himself and material improvement of the building (structure) owned or not owned by a VAT payer (Article 6 of the LVAT) Rate 21%                                                                                                                                                                                                                |
| PVM30                 | Manufacture of tangible fixed assets by a VAT payer himself and material improvement of the building (structure) owned or not owned by a VAT payer (Article 6 of the LVAT) Rate 9%                                                                                                                                                                                                                 |
| PVM31                 | Manufacture of tangible fixed assets by a VAT payer himself and material improvement of the building (structure) owned or not owned by a VAT payer (Article 6 of the LVAT) Rate 5%                                                                                                                                                                                                                 |
| PVM10                 | Cases when taxation of transactions is subject to a special taxation scheme (margin) (Articles 101–105, 106–110 of the LVAT) Exp.on 31-03-2016 Rate 21, 9, 5, 0                                                                                                                                                                                                                                    |
| PVM32                 | Cases where transactions are subject to a special taxation scheme (margin) to transactions (Sections II, III of the LVAT) Rate 21%                                                                                                                                                                                                                                                                 |
| PVM33                 | Cases of application of special taxation scheme (margin) to transactions (Sections II, III of the LVAT) Rate 0%                                                                                                                                                                                                                                                                                    |
| PVM12                 | Export of goods (Article 41 of the LVAT) Rate 0%                                                                                                                                                                                                                                                                                                                                                   |
| PVM13                 | Goods supplied to the EU VAT payers (Article 49(1), (4) of the LVAT) Rate 0%                                                                                                                                                                                                                                                                                                                       |
| PVM14                 | Other transactions (Articles 42, 43, 44, 45, 46, 47, 48, 49(2) and (3), 51, 52, 53(1), (5), (6) and (10) of the LVAT) Rate 0%                                                                                                                                                                                                                                                                      |
| PVM15                 | Goods and/or services supplied outside Lithuania (cases where VAT is not chargeable because the supply of goods and/or services is considered to have taken place outside Lithuania and is not subject to VAT in Lithuania, but VAT can be deducted according to the provisions of Article 58(1)(2) of the LVAT) Rate -                                                                            |
| PVM34                 | Goods and/or services supplied outside Lithuania (cases where VAT is not chargeable because the supply of goods and/or services is considered to have taken place outside Lithuania and VAT cannot be deducted according to the provisions of Article 58 of the LVAT) Rate -                                                                                                                       |
| PVM16                 | Cases where acquisition of goods from other Member States is considered to have taken place within the territory of the country (Articles 41 and 122 of the LVAT) Rate 21%                                                                                                                                                                                                                         |
| PVM17                 | Cases where acquisition of goods from other Member States is considered to have taken place within the territory of the country (Articles 41 and 122 of the LVAT) Rate 9%                                                                                                                                                                                                                          |
| PVM18                 | Cases where acquisition of goods from other Member States is considered to have taken place within the territory of the country (Articles 41 and 122 of the LVAT) Rate 5%                                                                                                                                                                                                                          |
| PVM35                 | Cases where acquisition of goods from other Member States is considered to have taken place within the territory of the country (Articles 41 and 122 of the LVAT) Rate 0%                                                                                                                                                                                                                          |
| PVM36                 | Cases where acquisition of goods from other Member States is considered to have taken place within the territory of the country (Articles 41 and 122 of the LVAT) Rate -                                                                                                                                                                                                                           |
| PVM19                 | Cases goods acquired by a VAT payer of the Republic of Lithuania, who is an intermediary (second party) in three-way trading were directly exported from one Member State to other Member State and supplied to a VAT payer of such other Member State (Article 122(3) of the LVAT) Rate -                                                                                                         |
| PVM20                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate 21%                                                                                                                                                                                                                                     |
| PVM37                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate 5%                                                                                                                                                                                                                                      |
| PVM38                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is not calculated by the buyer (Article 95(1)(3) of the LVAT) Rate 0%                                                                                                                                                                                                                               |
| PVM39                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is not calculated by the buyer (Article 95(1)(2) of the LVAT) Rate -                                                                                                                                                                                                                                |
| PVM21                 | Services acquired from the EU VAT payers the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate 21%                                                                                                                                                                                                                                                                   |
| PVM40                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate 5%                                                                                                                                                                                                                                      |
| PVM41                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate 0%                                                                                                                                                                                                                                      |
| PVM42                 | Services acquired from foreign countries (excluding the EU VAT payers) the output VAT on which is calculated by the buyer (Article 95(2) of the LVAT) Rate -                                                                                                                                                                                                                                       |
| PVM22                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Exp. on 31-03-2016 Rate 21, 9, 5                                                                                                              |
| PVM43                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Rate 21%                                                                                                                                      |
| PVM44                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Rate 9%                                                                                                                                       |
| PVM45                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Rate 5%                                                                                                                                       |
| PVM46                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Rate 0%                                                                                                                                       |
| PVM47                 | Cases where VAT on goods and/or services supplied by a foreign taxable person not established within the territory of the country (excluding the cases of PVM18, PVM19) is calculated and paid by the buyer (Article 95(3), (4) and (5) of the LVAT) Rate -                                                                                                                                        |
| PVM23                 | Calculated import VAT. Rate 21, 9, 5                                                                                                                                                                                                                                                                                                                                                               |
| PVM24                 | Import VAT the offsetting of which is controlled by the STI. Rate 21, 9, 5                                                                                                                                                                                                                                                                                                                         |
| PVM48                 | Goods and/or services acquired outside Lithuania (including the cases of charging VAT of a foreign country and of the import of goods for domestic consumption)) (cases where the acquisition of goods and/or services is considered to have taken place outside the Republic of Lithuania and the output VAT is not chargeable because the acquisition is not subject to VAT in Lithuania) Rate - |
| PVM49                 | Cases where agricultural products and services are purchased from farmers who are subject to the compensatory VAT rate scheme Rate 6%                                                                                                                                                                                                                                                              |
| PVM100                | Other cases                                                                                                                                                                                                                                                                                                                                                                                        |

Starting from **52.4** version of **i.SAF format (LT)** ER configuration, format includes application-specific parameters, where a user must define which **Sales tax codes** in the system (here and further “System Sales tax codes”) corresponds to which values from the enumerated list of VAT codes prescript as "Standard VAT codes".

To setup application-specific parameter, open **Electronic Reporting** workspace, select **i.SAF format (LT)** format and select **Configurations** > **Application specific parameters** > **Setup** on the Action pane, select **ReportTaxCodesLookup** on **Lookups** fast tab for the latest version of the format and on the **Conditions** fast tab define which “Standard VAT codes” must correspond to which “System Sales tax codes”.

As for example, if you have in the system two “System Sales tax codes” (VAT1, VAT2) which must be reported in one “Standard VAT codes” (PVM1), you would need to add the following lines on the Conditions fast tab:

| Lookup result | Line | Tax Code |
|---------------|------|----------|
| **PVM1** (the value must be selected from the predefined enumerated list) | 1 | **VAT1** (the value must be selected from the list of values which are entries in the Sales tax codes table) |
| **PVM1** (the value must be selected from the predefined enumerated list) | 2 | **VAT2** (the value must be selected from the list of values which are entries in the Sales tax codes table) |

Column “Line” is the counter which controls order of execution of the conditions of lookup field.

Add all necessary for your Legal entity conditions for those “Standard VAT codes” which must be reported for your Legal entity. According to the documentation the list of “Standard VAT codes” is the following:

> [!NOTE]

> It is important to add “PVM100” which must collect data by “other cases” as the last in the list (its “Line” value must be the last in your table).  Set it up as following:

| **Lookup result** | **Line**              | **Tax Code**      |
|-------------------|-----------------------|-------------------|
| **PVM100**        | The last in your list | **\*Not blank\*** |

This setup means that all the tax transactions for **Sales tax code** of which there
is no specific setup (no “Standard VAT code” is defined for it specifically)
will be considered for **PVM100.** It is mandatory to define such lookup result
field at the end of the list of your conditions.

You can easily export the setup of application-specific parameters from one version of a report and import it into another version. You can also export the setup from one report and import it into another report, provided that both reports have the same structure of lookup fields.

When you've finished setting up conditions, change the value of the **State** field to **Completed**, save your changes, and close the page.

## Import a package of data entities that includes a predefined electronic message setup

**Electronic Messages** functionality is provided to maintain different processes of electronic reporting of different document types. For more information about Electronic messages, see [Electronic messaging](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/electronic-messaging).

The process of setting up the Electronic messages functionality for i.SAF has many steps. Because the names of some predefined entities are used in the ER configurations, it's important that you use a set of predefined values that are delivered in a package of data entities for the related tables.

In [LCS](https://lcs.dynamics.com/v2), go to the Shared asset library, and select the **Data package** asset type. Then find **LT i.SAF setup for Electronic messages.zip** in the list of data package files, and download it to your computer.

After the **LT i.SAF setup for Electronic messages.zip** file is downloaded, open Finance, select the company that you will interoperate with HMRC from, and then go to **Workspaces** \> **Data management**.

Before you import setup data from the package of data entities, follow these steps to make sure that the data entities in your application are refreshed and synced.

1. In the **Data management** workspace, go to **Framework parameters** \> **Entity settings**, and then select **Refresh entity list**. Wait for confirmation that the refresh has been completed. For more information about how to refresh the entity list, see [Entity list refresh](../../dev-itpro/data-entities/data-entities.md#entity-list-refresh).
2. Validate that the source data and target data are correctly mapped. For more information, see the section about validation in [Data import and export jobs](../../dev-itpro/data-entities/data-import-export-job.md#validate-that-the-source-data-and-target-data-are-mapped-correctly).
3. Before the data entities are used for the first time to import the data from the package, sync the mapping of source data and target data. In the list for the package, select a data entity, and then, on the Action Pane, select **Modify target mapping**. Then, above the grid for the package, select **Generate mapping** to create a mapping from scratch. 
4. Save the mapping.
5. Repeat steps 3 through 4 for each data entity in the package before you start the import.

For more information about data management, see [Data management](../../dev-itpro/data-entities/data-entities-data-packages.md). 

You must now import data from the **LT i.SAF setup for Electronic messages.zip** file into the selected company. In the **Data management** workspace, select **Import**, and set the **Source data format** field to **Package**. Select **Upload and add**, select the **LT i.SAF setup for Electronic messages.zip** file on your computer, and upload it.

You will get a notification in the Messages or you may manually refresh the page to see data importing progress. When the importing process is completed you will see the results on Execution summary page.

The **LT i.SAF setup for Electronic messages.zip** package provides a setup for **"i.SAF"** processing that supports the process of i.SAF reporting composed generaly of three steps:

1.	**Populate invoices** – invoices will be added to the Message item table,
2.	**Attributes evaluation** – Document type field values will be evaluated for all the added invoice.
3.	**Generate message** – a message will be generated and related Message items according to their status and criteria setup will be added to the generated message.

## Set up data sources to collect documents to be reported

**i.SAF** processing let you collect invoices to be reported in the legal entity. You can then generate report in i.SAF format. The collection of invoices is implemented by using the **Populate invoices** action of the **Populate record** type. To correctly collect invoices, you must define a period for the **Populate invoices** action.

Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**, and select **Populate invoices**. 

For **i.SAF** processing default data sources set up includes following three data sources:

-   **VendInvoiceJour** (**Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**)

-   **CustInvoiceJour** (**Accounts receivable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**)

-   **ProjInvoiceJour** (**Project management and accounting** \> **Project invoices** \> **Project invoices**)

By default, all the records from these data sources will be populated to the **Message item** table on **Populate records** action run.

On the **Datasource setup** FastTab, select the **Vendor invoice journal** record, and then select **Edit query**. 

For the **Date** field of the **Vendor invoice journal** table, define the period from which vendor invoices from the selected legal entity must be reported in i.SAF format. You can specify other selection criteria here to reflect specific requirements of your company to i.SAF report. Repeat the same setup for other data sources of the report (Sales invoice journal, Project invoice journal) or delete unnecessary for your company data sources from the list.

![Populate invoices data sources](media/isaf-populate-records.jpg)


## Set up Electronic messaging parameters for i.SAF

After Data entities are imported to the data base, Electronic Messages functionality is almost ready for work. You need to additionally do the following steps:

1.  Open **Tax** \> **Setup** \> **Electronic messages** \> **Executable class settings**, select **EvaluateInvoiceType_LT** executable class and click **Parameters** on Action pane. Select in the **Invoice type** field **InvoiceType** and click **OK.**

2.  Set up GER configurations for Electronic messages processing actions. Open **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions** and set up related GER configurations in Format mapping field for the following actions:

| **Message processing actions name** | **GER configuration** |
|-------------------------------------|-----------------------|
| GenerateMessage                     | i.SAF format (LT)     |

3.  Number sequences in **General ledger parameters**:

| **Number sequences reference** | **Number sequences description**                                                                                                                                                                                                                         |
|--------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Message                        | Unique key for message. Set up a non-continuous number sequence for this Reference. This number sequence will be used for numbering messages on their generation. This number is not used in the reporting for SII**.**                                  |
| Message item                   | Unique key for message item. Set up a non-continuous number sequence for this Reference. This number sequence will be used for numbering message items on their population from the source tables. |

