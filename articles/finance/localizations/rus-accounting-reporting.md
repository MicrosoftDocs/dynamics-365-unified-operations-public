---
# required metadata
title: Accounting reporting in electronic format (Russia)
description: This topic explains how to set up accounting reporting for Russia.
author: Anasyash
ms.date: 09/03/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2019-4-30
ms.dyn365.ops.version: 10.0.1

---

# Accounting reporting in electronic format (Russia)

[!include [banner](../includes/banner.md)]

## Set up accounting reporting

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for accounting reporting.

    For example, to generate accounting reporting in XML format for the year after the 2019 reporting period, download the latest versions of the following configurations:

    - Financial reports model
    - Financial reports model mapping (RU)
    - Accounting reporting format 5.08 (RU)

    For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2. Upload the Data management package settings.

    The data package contains the following items:

    - Financial reports and financial report cells for the balance sheet, the income statement, the equity statement, cash flow, and funds usage.
    - Electronic message settings for generating accounting reporting in electronic format.

    Follow these steps:

    1. In the LCS Shared asset library, select **Data package** as the asset type.
    2. Download the package, **RU Accounting reporting 5.08 (2019).zip**. 
    3. In Dynamics 365 Finance, in the **Data management** workspace, select **Import**.
    4. In the **Job details** section, enter any name for the job.
    5. In the **Data source format** field, select **Package**.
    6. In the **Upload data file** field, select **Upload**, and then select the **RU Accounting reporting 5.08 (2019).zip** file that you downloaded earlier.
    7. After the data entities are uploaded, select **Import**.

3. Go to **General ledger \> Financial reports setup \> Financial reports**, and validate the financial reports that are imported. (All the data that is imported is presented only in the Russian language.)

    | Report           | Report code | Description                                             |
    |------------------|-------------|---------------------------------------------------------|
    | Balance sheet    | Баланс      | Бухгалтерский баланс (2019)                             |
    | Income statement | ПрибУб      | Отчет о прибылях и убытках (2019)                       |
    | Equity statement | ОтчетИзмКап | Отчет об изменении капитала (2019)                      |
    | Cash flow        | ДвижениеДен | Отчет о движении денежных средств (2019)                |
    | Funds usage      | ЦелИсп      | Отчет о целевом использовании полученных средств (20169 |

4. Set up financial report cell operations for the financial reports that are imported. Set up all required cells. These required cells include cells for totals.

    For more information about how to set up financial reports for Russia, see [Financial reporting (Russia)](rus-financial-reports.md).

5. Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**, and validate the electronic message processing that is imported. (Most of the data that is imported is presented in the Russian language.)

    | Processing           | Processing code    | Description                     |
    |----------------------|--------------------|---------------------------------|
    | Accounting reporting | БухОтч 5.08 (2019) | Бухгалтерская отчетность (2019) |

6. Set up the organization codes that are used in accounting reporting and any additional information about the company.

    1. Go to **Tax \> Setup \> Electronic messages \> Additional fields**.
    2. In the left pane, select the field that is named **EconomicActivityTypeCode (ОКВЭД)**. Then, on the **Value** FastTab, select **Add**. In the **Field value** field, enter the code for legal entity's economic activity type.
    3. Select the field that is named **OrganizationalFormCode (ОКОПФ)**. Then, on the **Value** FastTab, select **Add**. In the **Field value** field, enter the code for the legal entity's organizational form.
    4. Select the field that is named **OwneshipFormCode (ОКФС)**. Then, on the **Value** FastTab, select **Add**. In **Field value**, enter the code for the legal entity's ownership form.
    5. Select the field that is named **AuditorCompanyName (Наименование аудиторской организации)**. Then, on the **Value** FastTab, select **Add**. In **Field value**, enter the name of the auditor company in case of mandatory audit of the reporting.
    6. Select that field that is named **AuditorStateRegistrationNumber (ОГРН аудиторской организации)**. Then, on the **Value** FastTab, select **Add**. In **Field value**, enter the state registration number of the auditor company.
    7. Select the field that is named **AuditorTaxRegistrationNumber (ИНН аудиторской организации)**. Then, on the **Value** FastTab, select **Add**. In **Field value**, enter tax registration number of the auditor company.
    8. Go to **Tax \> Setup \> Electronic messages \> Electronic message processing**.
    9. On the **Message additional fields** FastTab, enter the following information.

        | Field name               | Default value                                |
        |--------------------------|----------------------------------------------|
        | EconomicActivityTypeCode | Select the value that you entered in step 2. |
        | OwneshipFormCode         | Select the value that you entered in step 3. |
        | OrganizationalFormCode   | Select the value that you entered in step 4. |
        | AuditorCompanyName       | Select the value that you entered in step 5. |
        | AuditorStateRegistrationNumber | Select the value that you entered in step 6. |
        | AuditorTaxRegistrationNumber | Select the value that you entered in step 7. |

7. Set up the ER format that is run when accounting reporting is generated in electronic format.

    1. Go to **Tax \> Setup \> Electronic messages \> Message processing actions**.
    2. In the left pane, select the action that is named **Generate BUHOTCH 5.08**, and then expand the **General** FastTab.
    3. Validate that in the **Format mapping** field, the configuraiton name **Accounting reporting format 5.08 (RU)** is selected. Validate that **Show dialog** is set to **Yes**.

    For more information about how to set up electronic messaging functionality, see [Electronic messaging](../general-ledger/electronic-messaging.md).

## Generate accounting reporting in electronic format

1. To generate the accounting reporting file, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
2. In the left pane, select the report format to generate. For example, select **БухОтч 5.08 (2019)**.
3. On the **Messages** FastTab, select **New**. Then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that was created. Enter a description, and specify the start date and end date for the report. The end date is treated as the base date for financial reports.
5. Optional: On the **Message additional fields** FastTab, enter the following information.

    | Field name       | Description                 | Field value |
    |------------------|-----------------------------|-------------|
    | CorrectionNumber | Номер коррекции             | Enter the number of the correction for corrective accounting reporting. |
    | ReportingDate    | Отчетная дата для коррекции | Enter the reporting date for corrective accounting reporting. (The calculation of cells on financial reports considers transactions of the base period and all later transactions, up to the reporting date, that correct the base period.) |
    | ApprovalDate     | Дата утверждения отчетности | Enter the date when the accounting reporting was approved. |

6. On the **Messages** FastTab, select **Update status**. Then, in the **Run processing** dialog box, select **OK**.
7. Validate that the message status is changed to **Ready to generate**.
8. On the **Messages** FastTab, select **Generate report**.
9. In the **Electronic reporting parameters** dialog box, enter the following information.

    | Field                                 | Description |
    |---------------------------------------|-------------|
    | Signatory type                        | Specify who signs the accounting reporting. Select either **Taxpayer** or **Representative**. |
    | Signatory first name, Signatory middle name, Signatory last name | Enter the full name of the signatory. If you leave these fields blank, the name of the official of the **Director** type is used as the name of the signatory. (This official is set up at **Organization administration \> Setup \> Contacts \> Officials**.) |
    | Representative document               | If you selected **Representative** as the signatory type, enter the document that confirms the representative's authority. |
    | Correction number                     | Enter the number of the correction, if you didn't specify it in step 5. |
    | Reporting date                        | Enter the reporting date, if you didn't specify it in step 5. |
    | Approval date                         | Enter the approval date, if you didn't specify it in step 5. |

10. Select **OK**. When the report is generated, the status of the message is changed to **Generated**. If an error occurs while the report is generated, the status of the message is changed to **Technical error**.
11. On the **Action log** FastTab, review all user actions for the current message.
12. To review the report that is generated, select the **Attachments** button (the paper clip symbol) in the upper-right corner of the page. Then select **Open** to open the file.

You must also manually upload the generated file to the special third-party software for data preview and data updates, and to transfer the accounting reporting files to the tax authorities through the communication channels.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]