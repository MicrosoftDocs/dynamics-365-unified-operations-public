---
title: Profit tax declaration
description: Learn how to set up and generate the profit tax declaration for Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2020-01-29
---

# Profit tax declaration

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the profit tax declaration for Russia in Microsoft Dynamics 365 Finance.

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

To set up the profit tax declaration, follow these steps.

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the ER configurations for the profit tax declaration. For example, to generate a profit tax declaration in XML format for the year 2019, download the latest versions of the following configurations:

    - Financial reports model
    - Financial reports model mapping (RU)
    - Profit tax declaration format 5.08 (RU)

    Learn more in [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

1. Upload the Data management package settings.

    1. In the LCS Shared asset library, select **Data package** as the asset type.
    1. Download the **RU Profit Tax 5.08 2019 package** package. The file that is downloaded is named **RU Profit Tax 5.08 2019 package.zip**.
    1. In Microsoft Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
    1. In the **Job details** section, enter a name for the job.
    1. In the **Data source format** field, select **Package**.
    1. In the **Upload data file** field, select **Upload**, and then select the **RU Profit Tax 5.08 2019 package.zip** file that you downloaded earlier.
    1. After the data entities are uploaded, select **Import**.

    The data package contains the following items:

    - Financial report and financial report cells for the profit tax declaration
    - Electronic message settings that are used to generate a profit tax declaration in electronic format

1. In Dynamics 365 Finance, go to **General ledger** \> **Financial reports setup** \> **Financial reports**, and validate the financial report that is imported. All the data that is imported is presented only in the Russian language.

    | Report                 | Report code    | Description                            |
    |------------------------|----------------|----------------------------------------|
    | Profit tax declaration | Прибыль (2019) | Декларация по налогу на прибыль (2019) |

1. Set up financial report cell operations for the financial reports that are imported.

    > [!NOTE]
    > Sort the financial report cells that are loaded from the package by the **Description** column. In this way, cells on the page appear in the same order in which they appear in the paper version of the declaration.

    Learn more in [Financial reporting (Russia)](rus-financial-reports.md).

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that is imported. Most of the data that is imported is presented in the Russian language.

    | Processing             | Processing code     | Description                            |
    |------------------------|---------------------|----------------------------------------|
    | Profit tax declaration | НалПриб 5.08 (2019) | Декларация по налогу на прибыль (2019) |

1. Set up the reference information that is used in the profit tax declaration.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Additional fields**.
    1. In the left pane, select the field. Then, on the **Value** FastTab, select **Add**.
    1. In the **Field value** field, enter the value of the field. The following values can be defined.

        | Field                            | Description |
        |----------------------------------|-------------|
        | BudgetClassificationCodeFederal  | Enter the budget classification code for the payment of profit tax to the federal budget (КБК федеральный). |
        | BudgetClassificationCodeRegional | Enter the budget classification code for the payment of profit tax to the regional budget (КБК Региональный). |
        | FinancialReport                  | Enter the code of the financial report for the profit tax declaration. For example, enter **Прибыль 2019**. |
        | TaxRateFederal                   | Enter the profit tax rate for the payment of profit tax to the federal budget (Ставка налога в федеральный бюджет). |
        | TaxRateRegional                  | Enter the profit tax rate for the payment of profit tax to the regional budget (Ставка налога в бюджет субъекта Российской Федерации). |
        | TaxRateRegionalLaw               | Enter the reference to the law number that enforces the regional tax rate that you apply. This value must be in the following format: *XXXX/YYYY/ZZZZ/NNNNNNNNNNNNNNN*, where *XXXX* is the law article number, *YYYY* is the point of the law article, *ZZZZ* is the subpoint of the law article, and *NNNNNNNNNNNNNNN* is the law number. |

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**.
    1. On the **Message additional fields** FastTab, select default values for the fields.

1. Set up the ER format that is run when a profit tax declaration is generated in electronic format.

    1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Message processing actions**.
    1. In the left pane, select the **Generate PRIB 5.08** action, and then select **Edit**.
    1. Set the **Show dialog** option to **Yes**.
    1. In the **Format mapping** field, select the **Profit tax declaration format 5.08 (RU)** configuration that you downloaded earlier.

For more information about how to set up electronic messaging functionality, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

### Generate a profit tax declaration in electronic format

To generate a profit tax declaration in electronic format, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
1. In the left pane, select the report format to generate. For example, select **НалПриб 5.08 (2019)**.
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, select **OK**.
1. Select the message line that is created, and then enter a description, and specify the start date and end date for the report. The end date is treated as the base date for financial reports.
1. Optional: On the **Message additional fields** FastTab, enter the following information.

    | Field name       | Description                 | Field value |
    |------------------|-----------------------------|-------------|
    | CorrectionNumber | Номер коррекции             | Enter the number of the correction for a corrective declaration. |
    | ReportingDate    | Отчетная дата для коррекции | Enter the reporting date for a corrective declaration. The calculation of cells on financial reports considers transactions of the base period and all later transactions, up through the reporting date, that correct the base period. |

1. On the **Messages** FastTab, select **Update status**.
1. In the **Run processing** dialog, select **OK**.
1. Validate that the message status is changed to **Ready to generate**.
1. On the **Messages** FastTab, select **Generate report**.
1. In the **Electronic reporting parameters** dialog, enter the following information.

    | Field                                                            | Description |
    |------------------------------------------------------------------|-------------|
    | Signatory type                                                   | Specify who signs the profit tax declaration. Select either **Taxpayer** or **Representative**. |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory. |
    | Representative document                                          | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |
    | Correction number                                                | Enter the number of the correction, if you didn't specify it in step 1. |
    | Reporting date                                                   | Enter the reporting date, if you didn't specify it in step 1. |

1. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs while the report is generated, the status of the message is changed to **Technical error**.
1. On the **Action log** FastTab, review all the user actions for the current message.
1. To review the report that is generated, select **Attachments** (the paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.

You must also manually upload the generated file to the special third-party software for data preview and data updates, and to transfer the profit tax declaration files to the tax authorities through the communication channels.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
