---
# required metadata
title: Profit tax declaration 
description: This topic provides information about the profit tax declaration for Russia.
author: anasyash
manager: AnnBe
ms.date: 01/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2020-01-29
ms.dyn365.ops.version: 10.0.9

---

# Profit tax declaration

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

You can generate profit tax declarations in an electronic format. To generate the declaration, you must first set up the rules for collecting data from ledger accounts or profit tax registers in the appropriate Financial report for Profit tax declaration.

A data package that contains pre-defined cells names for Profit tax declaration is available. Electronic reporting (ER) configuration is available that considers the pre-defined cells names. The following sections of Profit tax declaration are available in the data package and configured in ER configuration:

| **Section**                   | **Element in XML**  |
|-------------------------------|---------------------|
| Section 1                     | **НалПУ**           |
| Subsection 1.1                | **НалПУАв**         |
| Subsection 1.2                | **НалПУМес**        |
| Sheet 02                      | **РасчНал**         |
| Appendix 1 to Sheet 02        | **ДохРеалВнеРеал**  |
| Appendix 2 to Sheet 02        | **РасхРеалВнеРеал** |
| Appendix 3 to Sheet 02        | **РасчРасхОпер**    |
| Appendix 1 to tax declaration | **ДохНеУч_РасхУч**  |

## Set up profit tax declaration

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for profit tax declaration. For example, to generate a profit tax declaration in XML format for the 2019 year, download the latest versions of the following configurations:

- Financial reports model
- Financial reports model mapping (RU)
- Profit tax declaration format 5.08 (RU)

For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

2. Upload the Data management package settings. The data package contains the following items:

    - Financial report and financial report cells for the profit tax declaration.
    - Electronic message settings for generating profit tax declaration in electronic format.


     1. In the LCS Shared asset library, select **Data package** as the asset type.
     2. Download the **RU Profit Tax 5.08 2019 package** package. The file that is downloaded is named **RU Profit Tax 5.08 2019 package.zip**.
     3. In Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
     4. In the **Job details** section, enter a name for the job.
     5. In the **Data source format** field, select **Package**.
     6. In the **Upload data file** field, select **Upload**, and then select the **RU Profit Tax 5.08 2019 package.zip** file that you downloaded earlier.
     7. After the data entities are uploaded, select **Import**.

3. Go to **General ledger** \> **Financial reports setup** \> **Financial reports**, and validate the financial report that is imported. All the data that is imported is presented only in the Russian language.

| **Report**             | **Report code** | **Description**             |
|------------------------|-----------------|-----------------------------|
| Profit tax declaration | Прибыль  (2019)        | Декларация по налогу на прибыль (2019) |

4.  Set up financial report cell operations for the financial reports that are imported.
    
> [!NOTE]
> Sort financial report cells which are loaded from the package by the **Description** column so that cells are shown on the page in the same sequence that they are presented in the paper form of the declaration.

For more information about how to set up financial reports for Russia, see [Financial reporting (Russia)](https://docs.microsoft.com/dynamics365/finance/localizations/rus-financial-reports).

5. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that is imported. Most of the data that is imported is presented in the Russian language.

| **Processing**         | **Processing code** | **Description**                        |
|------------------------|---------------------|----------------------------------------|
| Profit tax declaration | НалПриб 5.08 (2019) | Декларация по налогу на прибыль (2019) |

6. Set up the reference information that is used in the profit tax declaration.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**.
    2. In the left pane, select the field. Then, on the **Value** FastTab, select **Add**. In the **Field value** field, enter the value of the field. The following values could be defined:

| **Field**                            | **Description**                                                                                                                                                                                                                                                                               |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **BudgetClassificationCodeFederal**  | Enter the budget classification code for payment of profit tax to the Federal budget (**КБК федеральный**)                                                                                                                                                                                    |
| **BudgetClassificationCodeRegional** | Enter the budget classification code for payment of profit tax to the Federal budget (**КБК Региональный**)                                                                                                                                                                                   |
| **FinancialReport**                  | Enter the code of the financial report for profit tax declaration. For example, enter **Прибыль 2019**                                                                                                                                                                                        |
| **TaxRateFederal**                   | Enter profit tax rate for payment of profit tax to the Federal budget (**Ставка налога в федеральный бюджет**)                                                                                                                                                                                |
| **TaxRateRegional**                  | Enter profit tax rate for payment of profit tax to the Regional budget (**Ставка налога в бюджет субъекта Российской Федерации**)                                                                                                                                                             |
| **TaxRateRegionalLaw**               | Enter the reference to law number which enforced the regional tax rate which you apply. This value must have the following format: XXXX/YYYY/ZZZZ/NNNNNNNNNNNNNNN, Where XXXX - law article number, YYYY - point of law article, ZZZZ - subpoint of law article, NNNNNNNNNNNNNNN – law number |

   3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
   4.  On the **Message additional fields** FastTab, select default values for the fields.

7.  Set up the ER format that is run when profit tax declaration is generated in electronic format.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**.
    2. In the left pane, select the action that is named **Generate PRIB 5.08**, and then select **Edit**.
    3. Set the **Show dialog** option to **Yes**.
    4. In the **Format mapping** field, select the **Profit tax declaration format 5.08 (RU)** configuration that you downloaded earlier.

For more information about how to set up electronic messaging functionality, see [Electronic messaging (https://docs.microsoft.com/dynamics365/finance/general-ledger/electronic-messaging).

**Generate profit tax declaration in electronic format**

1. To generate the profit tax declaration file, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select the report format to generate. For example, select **НалПриб 5.08 (2019)**.
3. On the **Messages** FastTab, select **New**. Then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that was created. Enter a description and specify the start date and end date for the report. The end date is treated as the base date for financial reports.
5. Optional: On the **Message additional fields** FastTab, enter the following information.

| **Field name**   | **Description**             | **Field value**                                                                                                                                                                                                                    |
|------------------|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **CorrectionNumber** | **Номер коррекции**             | Enter the number of the correction for corrective declaration.                                                                                                                                                                     |
| **ReportingDate**    | **Отчетная дата для коррекции** | Enter the reporting date for corrective declaration. The calculation of cells on financial reports considers transactions of the base period and all later transactions, up to the reporting date, that correct the base period. |

6. On the **Messages** FastTab, select **Update status**, and in the **Run processing** dialog box, select **OK**.
7. Validate that the message status is changed to **Ready to generate**.
8. On the **Messages** FastTab, select **Generate report**.
9. In the **Electronic reporting parameters** dialog box, enter the following information.

| **Field**                                                        | **Description**                                                                                                            |
|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| **Signatory type**                                                   | Specify who signs the profit tax declaration. Select either **Taxpayer** or **Representative**.                            |
| **Signatory first name**, **Signatory middle name**, **Signatory last name** | Enter the full name of the signatory.                                                                                      |
| **Representative document**                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |
| **Correction number**                                                | Enter the number of the correction, if you didn't specify it in step 5.                                                    |
| **Reporting date**                                                   | Enter the reporting date, if you didn't specify it in step 5.                                                              |

10. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs while the report is generated, the status of the message is changed to **Technical error**.
11. On the **Action log** FastTab, review all of the user actions for the current message.
12. To review the report that is generated, select **Attachments** (the paper clip icon) in the upper-right corner of the page. Then select **Open** to open the file.

You must also manually upload the generated file to the special third-party software for data preview and data updates, and to transfer the profit tax declaration files to the tax authorities through the communication channels.
