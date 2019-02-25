---
# required metadata
title: Accounting reporting in electronic format (Russia)
description: This topic explains how to set up accounting reporting for Russia.
author: Anasyash
manager: AnnBe
ms.date: 03/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
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


1.  In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2), in the Shared asset library, download the latest versions of the Electronic reporting (ER) configurations for the Accounting reporting.

    >   For example, to generate the Accounting reporting in xml format for the year after 2016 reporting period, download the latest versions of the following configurations:
    > -   Financial reports model
    > -   Financial reports model mapping (RU)
    > -   Accounting reporting format 5.07 (RU)
    >   For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

2.  Upload Data management package settings. 

    >   Data package contains:
    > -   Financial reports and Financial reports cells for Balance sheet, Income statement, Equity statement, Cash flow, Funds usage
    > -   Electronic messages settings for generating accounting reporting in electronic format.
    >  Follow these steps:

    1. In the LCS Shared asset library, select **Data package** as the asset type. 
    2. Download the **RU Accounting reporting 5.07 (2016)** package. The file that is downloaded is named **RU Accounting reporting 5.07
    (2016).zip**
    3. In Microsoft Dynamics 365 for Finance and Operations, in the **Data management** workspace, select **Import**.
    4. In the **Job details** section, enter any name for the job.
    5. In the **Data source format** field, select **Package**.
    6. In the **Upload data file** field, select **Upload**, and then select the **RU Accounting reporting 5.07 (2016).zip** file that you downloaded earlier.
    7. After the data entities are uploaded, select **Import**.

3.  Go to **General ledger \> Financial reports setup \> Financial reports**, and validate the financial reports that are imported (all data which is imported, are presented only in Russian language):

    | **Report**       | **Report code** | **Description**                                         |
    |------------------|-----------------|---------------------------------------------------------|
    | Balance sheet    | Баланс          | Бухгалтерский баланс (2016)                             |
    | Income statement | ПрибУб          | Отчет о прибылях и убытках (2016)                       |
    | Equity statement | ОтчетИзмКап     | Отчет об изменении капитала (2016)                      |
    | Cash flow        | ДвижениеДен     | Отчет о движении денежных средств (2016)                |
    | Funds usage      | ЦелИсп          | Отчет о целевом использовании полученных средств (2016) |

2.  Set up financial reports cells operations for financial reports that are imported. You should set up all required cells including totals.

    >   For more information about how to set up financial reports for Russia, see [Financial reporting (Russia)](rus-financial-reports.md).

3.  Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**, and validate the electronic message processing that is imported (most of the data which is imported, are presented in Russian language)

    | **Processing**       | **Processing code** | **Description**                 |
    |----------------------|---------------------|---------------------------------|
    | Accounting reporting | БухОтч 5.07 (2016)  | Бухгалтерская отчетность (2016) |

4.  Set up the organization codes that are used in accounting reporting.

    1.  **Go to Tax \> Setup \> Electronic messages \> Additional fields**.
    2.  Select line with field name «EconomicActivityTypeCode (ОКВЭД)». On the FastTab **Value** click **Add.** Enter legal entity’s economic activity type code in the field **Field value**.
    3.  Select the line with field name «OrganizationalFormCode (ОКОПФ)». On the FastTab **Value** click **Add.** Enter legal entity’s organizational form code in the field **Field value**.
    4.  Select the line with field name OwneshipFormCode (ОКФС). On the FastTab **Value** click **Add.** Enter legal entity’s ownership form code in the field **Field value.**
    5.  Go to **Tax \> Setup \> Electronic messages \> Electronic message processing.**
    6.  On FastTab **Message additional fields**, enter the following settings:

    | **Field name**           | **Default value**                   |
    |--------------------------|-------------------------------------|
    | EconomicActivityTypeCode | Choose the value created on step 2) |
    | OwneshipFormCode         | Choose the value created on step 3) |
    | OrganizationalFormCode   | Choose the value created on step 4) |

3.  Set up Electronic reporting format which is run when generating accounting reporting in electronic format.

    1.  **Go to Tax \> Setup \> Electronic messages \> Message processing actions**. Choose action **Generate BUHOTCH 5.07**.
    2.  Click **Edit**. In the field **Show dialog** select **Yes**.
    3.  In the field **Format mapping** select **Accounting reporting format 5.07 (RU)** downloaded in step 1.

## Generate accounting reporting in electronic format

1. To generate accounting reporting file, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages.** Select the report format to be generated (for example, select **БухОтч 5.07 (2016)**)

2. On Fast tab **Messages** click **New**. In the **Run processing** dialog box click **OK**.

3. Click on the message line which has been created. Enter **Description**. Fill **Start date** and **End date** for the report. **End date** is considered as **Base date** for Financial reports.

4. Optionally, on fast tab **Message additional fields** enter the following data:

  | **Field name**   | **Description**             | **Field value**        |
  |------------------|-----------------------------|------------------------|
  | CorrectionNumber | Номер коррекции             | Enter the number of correction for corrective accounting reporting |
  | ReportingDate    | Отчетная дата для коррекции | Enter the Reporting date for corrective accounting reporting (the calculation of cells on financial reports considers transactions of the base period and all later transactions, up to the reporting date, that correct the base period) |
  | ApprovalDate     | Дата утверждения отчетности | Enter the date when the accounting reporting was approved. |

5. On Fast tab **Messages** click **Update status**. In the **Run processing** dialog box click **OK**. Validate that the message status has been changed to **Ready to generate**.

6. On Fast tab **Messages** click **Generate report.**
7. On the **Electronic reporting parameters** dialog box, enter the following data:

| **Field**                             | **Description**   |
|-----------------------------------|-------------------------|
| Signatory type                        | Choose either Taxpayer or Representative – the one who is signing the accounting reporting |
| Signatory first, middle and last name | Enter full name of Signatory. In case if the values are blank, the name of Official of type “Director” (which is set up in **Organization administration \> Setup \> Contacts \> Officials**) will be taken as signatory. |
| Representative document               | In case of “Representative” signatory type, enter the document confirming the representative authority    |
| Correction number                     | Enter the number of correction if you didn’t specify it on step 4.  |
| Reporting date                        | Enter the reporting date if you didn’t specify it on step 4.        |
| Approval date                         | Enter the approval date if you didn’t specify it on step 4.         |

8.  Click **OK**. When the report is generated, the status of the message is changed to “Generated”. If an error occurred during generation, the status of the message is changed to “Technical error”.

9.  Review all user actions with the current message, on the FastTab **Action log**

10. Review the generated report in the **Attachments**. Click **Open** to view the file.

You further need to manually upload the generated file to the special third-party software for data preview, data updates and transferring the accounting reporting files to Tax authorities through the communication channels.
