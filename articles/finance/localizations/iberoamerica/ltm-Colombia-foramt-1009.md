---
title: Format 1009 file for Colombia configuration
description: Learn how to set up and issue a format 1009 file for Colombia, including prerequisites and an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 12/01/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1009 file for Colombia configuration

This article explains how to set up and issue a format 1009 file. The format 1009 file provides information about the company's liabilities during a specified period.

It includes two format outputs, an XML file that meets the official tax requirements and an Excel file for internal control purposes.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in a country/region within the Latin American (LATAM) localization.
- Enable the country/region specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import the following configurations from the Dataverse:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   |:::no-loc text="LTM Tax Report":::                 |
| Mapping | :::no-loc text="LTM Tax Report mapping":::|
| Format  | :::no-loc text="File format 1009:::      |
| Format  | :::no-loc text="File format 1009 Excel":::  |

    For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application codes

To execute the Form 1009 report in Dynamics 365 Finance and Operations, you need to set up a Tax Application.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **1009** (For format 1009). 
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Colombian format 1009.
1. In the **Tax application code** field, enter the code for tax IDs according to the Colombian regulatory.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (Country/Region, State and County) go to **LATAM** \> **Tax application** to assign the tax application codes for according to the Colombian regulatory.

Proper setup of this Tax Application codes is essential for the report to correctly reflect taxable operations and comply with DIAN requirements.

For more information, see [Tax application for Latin America](../ltm-core-tax-application.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and ledger account numbers that's used in transactions that are shown on the report.

> [!NOTE]
> The lookup settings must be applied to both formats to be used.

Follow these steps to set up the parameters for the reports.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **File format 1009** or **File format 1009 Excel**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **IsApplicable**. Use this lookup to select the document classes that are used for vendor invoices, credit notes, debit notes, and payment transactions.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class.

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are listed on the report.

8. In the **Lookups** section, select **MainAccountGroups**.
9. In the **Conditions** section, select **Add** and select a concept code for the **Lookup result field**.
10. In the **Main Account** field, select a ledger account.
11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Main account** field, select **Blank**.

12. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Main account** field, select **Not Blank**.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are listed on the report.

## Issue format 1009 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1009**.
3. Select **OK**.
4. Specify the Tax Application ID applicable to this format
4. Select a date range.
5. Select **OK**.

## Issue a format 1009 file in excel format
1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1009 Excel**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.

> [!NOTE]
> When executing the Format 1009 report in Excel, it is not necessary to populate the Tax Application ID field in the report launcher."
