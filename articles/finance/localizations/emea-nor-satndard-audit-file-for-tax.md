---
# required metadata

title: Standard Audit File for Tax (SAF-T) for Norway
description: This topic explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities that have their primary address in Norway. 
author: LizaGolub
ms.author: v-elgolu
ms.date: 12/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

manager: 
# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Standard Audit File for Tax (SAF-T) for Norway

[!include [banner](../includes/banner.md)]

This topic includes country-specific information about how to set up the Standard Audit File for Tax (SAF-T) for legal entities that have their primary address in Norway.

## Introduction

Beginning January 2020, all companies in Norway are required by the Norwegian Tax Administration to provide SAF-T Financial data. This requirement is in accordance with version 1.4 of the documentation, which was published on July 8, 2019, and version 1.3 of the technical documentation, which was published on March 23, 2018, in the form of an XML report. The publication of these pieces of documentation coincided with version 1.1 of the "Norwegian SAF-T Financial data" XML Schema Definition (XSD) schema that was developed by the SAF-T Working group, Skatteetaten, and based on "OECD Standard Audit File - Taxation 2.00," which was modified on February 2, 2018.

## Overview

To support the **Norwegian SAF-T Financial data** report, your Microsoft Dynamics 365 Finance application must be one of the following versions or later.

| Version of Finance | Build number       |
|--------------------|--------------------|
| 10.0.6             | 10.0.234.**20020** |
| 10.0.7             | 10.0.283.**10012** |
| 10.0.8             | 10.0.319.**12**    |
| 10.0.9             | 10.0.328.**20020** |

When your Finance application version is suitable, import the following versions or later of these Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS).

| ER configuration name              | Configuration type | Version |
|------------------------------------|--------------------|---------|
| Standard Audit File (SAF-T)        | Model              | 32      |
| SAF-T Financial data model mapping | Model mapping      | 32.30   |
| SAF-T Format (NO)                  | Format (exporting) | 32.41   |

Import the latest versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that the configuration version introduced.

> [!NOTE]
> After you've finished importing all the ER configurations from the preceding table, set the **Default for model mapping** option to **Yes** for the **SAF-T Financial data model mapping** configuration.
>
> ![Default for model mapping option set to Yes](media/nor-saf-default-model-mapping.jpg)

For more information about how to download ER configurations from LCS, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

## Setup

To start to use the **Norwegian SAF-T Financial data** report in Finance, you must complete the following setup:

- **General ledger parameters:** Set up the ER format on the **General ledgers parameters** page.
- **Sales tax codes:** Associate sales tax codes with Norwegian standard value-added tax (VAT) tax codes.
- **Main accounts:** Associate main accounts with Norwegian standard accounts.

The following sections explain how to do each part of this setup.

### General ledger parameters

1. In Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **General ledger parameters** page, on the **Standard Audit File for Tax (SAF-T)** tab, in the **Standard Audit File for Tax (SAF-T)** field, select **SAF-T Format (NO)**.

![Standard Audit File for Tax (SAF-T) field on the General ledger parameters page](media/nor-saf-gl-parameters.jpg)

### Sales tax codes

As the documentation explains, in Norwegian SAF-T Financial data, sales tax codes that are used in Finance must be associated with Norwegian standard VAT tax codes (\<StandardTaxCode\>) for the purpose of SAF-T reporting. The Norwegian standard VAT tax codes are available at <https://github.com/Skatteetaten/saf-t>.

To associate sales tax codes that are used in Finance with Norwegian standard VAT tax codes, follow these steps.

1. In Finance, go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
2. On the **Sales tax code** page, select the **Sales tax code** record, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.

    ![External codes button on the Action Pane of the Sales tax code page](media/nor-saf-standard-tax-codes.jpg)

3. On the **External codes** page, specify the Norwegian standard VAT tax codes that should be used for the selected sales tax code record for the purpose of SAF-T reporting.

### Main accounts

As the documentation explains, in Norwegian SAF-T Financial data, main accounts that are used in Finance must be associated with Norwegian standard accounts for the purpose of SAF-T reporting. The Norwegian standard accounts are available at <https://github.com/Skatteetaten/saf-t>.

To associate main accounts that are used in Finance with Norwegian standard accounts, follow these steps.

1. In Finance, go to **General ledger** \> **Chart of accounts** \> **Accounts** \> **Main accounts**.
2. On the **Main accounts** page, select the **Main account** record, and then, on the Action Pane, select **Edit**.
3. On the **General** FastTab, in the **Standard general ledger account** section, in the **Standard account** field, select **Standard account**.

![Standard account field on the Main accounts page](media/nor-saf-standard-main-accounts.jpg)

You must define all the standard accounts on the **Standard general ledger accounts** page before you can select them for a main account. To quickly access the **Standard general ledger accounts** page from the **Main accounts** page, right-click the **Standard account** field, and then select **View details**.

![View details command on the shortcut menu for the Standard account field](media/nor-saf-standard-main-account-setup.jpg)

## Generate the Norwegian SAF-T Financial data report

To generate the **Norwegian SAF-T Financial data** report, follow these steps.

1. In Finance, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **Standard Audit File for Tax (SAF-T)**.
2. In the dialog box for the report, in the **From date** and **To date** fields, specify the start and end dates of the period that you want to generate the report for.
3. Select the check boxes for **Customers**, **Vendors**, and **Financial dimensions** to include all the records from the related tables on the report.

    If the **Customers** and **Vendors** check boxes are cleared, the report will include only those customers and vendors of your company that there were transactions for in the reporting period, and customers and vendors that have a non-zero balance.
    
    If the **Financial dimensions** check box is cleared, only those financial dimensions that were used in transactions during the reporting period will be reported in the **\<MasterFiles\>** node of the report.

4. In the **Personnel number** field, select an employee to add the employee to the **\<UserID\>** node of the report. This node reports the ID of the user who generated the audit file.

You can also apply filters for the **Main accounts** and **General journal entry** fields by using **Records to include** FastTab in the dialog box for the report.

## Report naming and splitting

The documentation for Norwegian SAF-T Financial data requires the following naming structure for the XML reports that are generated:

\<SAF-T export type\>\_\<organization number of the vendor that the data represents\>\_\<date and time(yyyymmddhh24hmise\>\_\<file number of total files\>.xml 

Here is an example:

SAF-T Financial\_999999999\_20160401235911\_1\_12.xml

Here is an explanation of the parts of this file name:

- **SAF-T Financial** states the SAF-T type of file.
- **999999999** represents the organization number that belongs to the owner of the data.
- **20160401235911** represents the date and time when the file was created. (A 24-hour clock is used for the time.)
- **1\_12** represents file 1 out of 12 total files in the export (that is, in the same selection).

The volume of a single XML file must be less than 2 gigabytes (GB). Every individual XML file that is submitted must be validated against the schema. All \<MasterFiles\> nodes must be in the first file, and the associated transactions must be in the subsequent files (the number of these files is flexible).

The following table shows a sample selection of one accounting year that has 12 periods. For each period, there is one file that contains transactions.

| File number | Contents of the audit file                     |
|-------------|------------------------------------------------|
| 1           | \<Header\> and \<MasterFiles\> nodes           |
| 2–13        | \<Header\> and \<GeneralLedgerEntries\> nodes  |

There can be a maximum of 10 XML files in the same zip archive.

In accordance with these requirements, the **SAF-T Format (NO)** ER format is implemented to automatically split the resulting report in XML format, based on the following assumptions:

- The maximum volume of the resulting XML report is 2,000,000 kilobytes (KB) (that is, 2 GB).
- All the XML files use the following naming structure:

    \<SAF-T export type\>\_\<organization number of the vendor that the data represents\>\_\<date and time(yyyymmddhh24hmise\>

- All the XML files are included in one zip archive.
- Each individual XML file is validated against the schema.

After the report is generated, if more than one XML file is generated, the user must manually number the generated files in the zip archive by adding **\_\<file number of total files\>** to the file names. The user must also make sure that there are no more than 10 XML files in the same zip archive. If there are more than 10 XML files in an archive, the user must manually split it into several archives, each of which has a maximum of 10 XML files.
