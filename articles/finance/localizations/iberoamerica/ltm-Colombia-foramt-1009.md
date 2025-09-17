---
title: Format 1009 file for Colombia configuration
description: Learn how to set up and issue a format 1009 file for Colombia, including prerequisites and an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 09/17/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up format 1009 file for Colombia

[!INCLUDE[banner](../../includes/banner.md)]

Set up and issue the format 1009 file. The format 1009 file shows the company's liabilities for a reporting period.

The output includes two files: an XML file that meets official tax requirements and an Excel file for internal control.

## Prerequisites

Before you print the report, make sure these prerequisites are met:

- Set the legal entity address to a country/region in the Latin American (LATAM) localization.
- Enable the country/region-specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import the following configurations from Dataverse:

| Element | Format name |
|---------|-------------|
| Model | :::no-loc text="LTM Tax Report"::: |
| Mapping | :::no-loc text="LTM Tax Report mapping"::: |
| Format | :::no-loc text="File format 1009"::: |
| Format | :::no-loc text="File format 1009 Excel"::: |

    For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application codes

To run the Form 1009 report in Dynamics 365 Finance and Operations by setting up a tax application, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record with code **1009** for format 1009.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. For each record, select it, then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code for Colombian format 1009.
1. In the **Tax application code** field, enter the tax ID code according to Colombian regulation.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (Country/Region, State, and County), go to **LATAM** \> **Tax application** to assign the tax application codes according to Colombian regulation.

Set up these tax application codes correctly so the report reflects taxable operations and complies with DIAN requirements.

Learn more in [Tax application for Latin America](../ltm-core-tax-application.md).

## Configure application-specific parameters

Use lookups and conditions to select the combination of document classification IDs and ledger account numbers used in the transactions shown on the report.

> [!NOTE]
> Apply the lookup settings to both formats before you use them.

To set up the report parameters, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
1. In the left pane, select **LTM Tax Report deployment** \> **File format 1009** or **File format 1009 Excel**.
1. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select the first lookup, **IsApplicable**. Use this lookup to select the document classes used for vendor invoices, credit notes, debit notes, and payment transactions.
1. In the **Conditions** section, select **Add**, and then do the following:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification ID** field, select the appropriate document class.

1. Select **Add** again, and then do the following:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Not Blank**.

    > [!NOTE]
    > Use the document classes you select here in the company transactions listed on the report.

1. In the **Lookups** section, select **MainAccountGroups**.
1. In the **Conditions** section, select **Add**, and then select a concept code for the **Lookup result field**.
1. In the **Main Account** field, select a ledger account.
1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account** field, select **Not Blank**.

    > [!NOTE]
    > Use the ledger accounts you select here in the company transactions listed on the report.

## Issue format 1009 file

To issue format 1009 file, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **File format 1009**.
1. Select **OK**.
1. Specify the Tax Application ID applicable to this format.
1. Select a date range.
1. Select **OK**.

## Issue format 1009 file in Excel

To issue format 1009 file in Excel, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **File format 1009 Excel**.
1. Select **OK**.
1. Select a date range.
1. Select **OK**.

> [!NOTE]
> When you run the Format 1009 report in Excel, you don't need to enter a value in the **Tax Application ID** field in the report launcher.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
