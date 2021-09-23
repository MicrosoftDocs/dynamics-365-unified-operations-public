---
# required metadata
title: Profit tax declaration 
description: This topic provides information about the profit tax declaration for Russia.
author: anasyash
ms.date: 03/17/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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

You can generate profit tax declarations in an electronic format. To generate the declaration, you must first set up the rules for collecting data from ledger accounts or profit tax registers in the appropriate financial report for the profit tax declaration.

A data package is available that contains predefined cells names for the profit tax declaration. An Electronic reporting (ER) configuration is available that considers the predefined cells names. The following sections of the profit tax declaration are available in the data package and configured in the ER configuration.

| Section                       | Element in XML   |
|-------------------------------|------------------|
| Section 1                     | НалПУ            |
| Subsection 1.1                | НалПУАв          |
| Subsection 1.2                | НалПУМес         |
| Sheet 02                      | РасчНал          |
| Appendix 1 to Sheet 02        | ДохРеалВнеРеал   |
| Appendix 2 to Sheet 02        | РасхРеалВнеРеал  |
| Appendix 3 to Sheet 02        | РасчРасхОпер     |
| Appendix 1 to tax declaration | ДохНеУч\_РасхУч  |

## Set up the profit tax declaration

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the ER configurations for the profit tax declaration. For example, to generate a profit tax declaration in XML format for the year 2019, download the latest versions of the following configurations:

    - Financial reports model
    - Financial reports model mapping (RU)
    - Profit tax declaration format 5.08 (RU)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2. Upload the Data management package settings.

    1. In the LCS Shared asset library, select **Data package** as the asset type.
    2. Download the **RU Profit Tax 5.08 2019 package** package. The file that is downloaded is named **RU Profit Tax 5.08 2019 package.zip**.
    3. In Microsoft Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
    4. In the **Job details** section, enter a name for the job.
    5. In the **Data source format** field, select **Package**.
    6. In the **Upload data file** field, select **Upload**, and then select the **RU Profit Tax 5.08 2019 package.zip** file that you downloaded earlier.
    7. After the data entities are uploaded, select **Import**.

    The data package contains the following items:

    - Financial report and financial report cells for the profit tax declaration
    - Electronic message settings that are used to generate a profit tax declaration in electronic format

3. Go to **General ledger** \> **Financial reports setup** \> **Financial reports**, and validate the financial report that is imported. All the data that is imported is presented only in the Russian language.

    | Report                 | Report code    | Description                            |
    |------------------------|----------------|----------------------------------------|
    | Profit tax declaration | Прибыль (2019) | Декларация по налогу на прибыль (2019) |

4. Set up financial report cell operations for the financial reports that are imported.

    > [!NOTE]
    > Sort the financial report cells that are loaded from the package by the **Description** column. In this way, cells on the page appear in the same order in which they appear in the paper version of the declaration.

    For more information about how to set up financial reports for Russia, see [Financial reporting (Russia)](./rus-financial-reports.md).

5. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that is imported. Most of the data that is imported is presented in the Russian language.

    | Processing             | Processing code     | Description                            |
    |------------------------|---------------------|----------------------------------------|
    | Profit tax declaration | НалПриб 5.08 (2019) | Декларация по налогу на прибыль (2019) |

6. Set up the reference information that is used in the profit tax declaration.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**.
    2. In the left pane, select the field. Then, on the **Value** FastTab, select **Add**.
    3. In the **Field value** field, enter the value of the field. The following values can be defined.

        | Field                            | Description |
        |----------------------------------|-------------|
        | BudgetClassificationCodeFederal  | Enter the budget classification code for the payment of profit tax to the federal budget (КБК федеральный). |
        | BudgetClassificationCodeRegional | Enter the budget classification code for the payment of profit tax to the regional budget (КБК Региональный). |
        | FinancialReport                  | Enter the code of the financial report for the profit tax declaration. For example, enter **Прибыль 2019**. |
        | TaxRateFederal                   | Enter the profit tax rate for the payment of profit tax to the federal budget (Ставка налога в федеральный бюджет). |
        | TaxRateRegional                  | Enter the profit tax rate for the payment of profit tax to the regional budget (Ставка налога в бюджет субъекта Российской Федерации). |
        | TaxRateRegionalLaw               | Enter the reference to the law number that enforces the regional tax rate that you apply. This value must be in the following format: *XXXX/YYYY/ZZZZ/NNNNNNNNNNNNNNN*, where *XXXX* is the law article number, *YYYY* is the point of the law article, *ZZZZ* is the subpoint of the law article, and *NNNNNNNNNNNNNNN* is the law number. |

    4. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
    5. On the **Message additional fields** FastTab, select default values for the fields.

7. Set up the ER format that is run when a profit tax declaration is generated in electronic format.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**.
    2. In the left pane, select the **Generate PRIB 5.08** action, and then select **Edit**.
    3. Set the **Show dialog** option to **Yes**.
    4. In the **Format mapping** field, select the **Profit tax declaration format 5.08 (RU)** configuration that you downloaded earlier.

For more information about how to set up electronic messaging functionality, see [Electronic messaging](../general-ledger/electronic-messaging.md).

### Generate a profit tax declaration in electronic format

1. To generate the profit tax declaration file, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select the report format to generate. For example, select **НалПриб 5.08 (2019)**.
3. On the **Messages** FastTab, select **New**.
4. In the **Run processing** dialog box, select **OK**.
5. Select the message line that is created, and then enter a description, and specify the start date and end date for the report. The end date is treated as the base date for financial reports.
6. Optional: On the **Message additional fields** FastTab, enter the following information.

    | Field name       | Description                 | Field value |
    |------------------|-----------------------------|-------------|
    | CorrectionNumber | Номер коррекции             | Enter the number of the correction for a corrective declaration. |
    | ReportingDate    | Отчетная дата для коррекции | Enter the reporting date for a corrective declaration. The calculation of cells on financial reports considers transactions of the base period and all later transactions, up through the reporting date, that correct the base period. |

7. On the **Messages** FastTab, select **Update status**.
8. In the **Run processing** dialog box, select **OK**.
9. Validate that the message status is changed to **Ready to generate**.
10. On the **Messages** FastTab, select **Generate report**.
11. In the **Electronic reporting parameters** dialog box, enter the following information.

    | Field                                                            | Description |
    |------------------------------------------------------------------|-------------|
    | Signatory type                                                   | Specify who signs the profit tax declaration. Select either **Taxpayer** or **Representative**. |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory. |
    | Representative document                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |
    | Correction number                                                | Enter the number of the correction, if you didn't specify it in step 6. |
    | Reporting date                                                   | Enter the reporting date, if you didn't specify it in step 6. |

12. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs while the report is generated, the status of the message is changed to **Technical error**.
13. On the **Action log** FastTab, review all the user actions for the current message.
14. To review the report that is generated, select **Attachments** (the paper clip symbol) in the upper-right corner of the page. Then select **Open** to open the file.

You must also manually upload the generated file to the special third-party software for data preview and data updates, and to transfer the profit tax declaration files to the tax authorities through the communication channels.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]