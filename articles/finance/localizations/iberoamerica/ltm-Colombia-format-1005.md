---
title: Format 1005 file for Colombia configuration
description: Learn about the configuration required to issue the format 1005 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 09/17/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure Format 1005 file for Colombia

[!INCLUDE[banner](../../includes/banner.md)]

This article describes how to configure and generate the Format 1005 file. The report shows deductible VAT for purchases and sales returns. It outputs an XML file that meets official tax requirements and an Excel file for internal control.

## Prerequisites

Before you print the report, make sure these prerequisites are met:

- Make sure the legal entity has an address in a country/region in the Latin American (LATAM) localization.
- Turn on the country/region-specific LATAM feature and the general feature.
- Import the following configurations from Dataverse:

| Element | Format name |
|---------|-------------|
| Model | :::no-loc text="LTM Tax Report"::: |
| Mapping | :::no-loc text="LTM Tax Report mapping"::: |
| Format | :::no-loc text="File format 1005"::: |
| Format | :::no-loc text="File format 1005 (Excel)"::: |

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application codes

Set up a tax application ID to run Form 1005 reports in Dynamics 365 Finance and Operations.

* Go to **Organization Administration** > **Settings** > **LATAM** > **Tax Application**. Select **New** and create a record with code **1005**. 

Configure the tax application code for each **Tax Id Type**.
* Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**. For each record, select **Tax application** on the top menu and create a new record with the appropriate tax application code based on fiscal regulations.

Correct setup of these tax application codes lets the report reflect taxable operations and comply with DIAN requirements.

Learn more in [Tax application for Latin America](ltm-core-tax-application.md).

## Configure application-specific parameters for format 1005

Lookups and conditions let you select the document classification IDs and tax codes used in transactions shown in the report.

To configure application-specific parameters for format 1005, after you meet the prerequisites, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
1. In the tree on the left, select **LTM Tax Report deployment** \> **Format 1005**.
1. On the top menu, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select **ApplicableInvoice**. This lookup lets you select the document classes for vendor invoices that contain VAT.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification ID** field, select the appropriate document class (vendor invoices).

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Not Blank**.

1. In the **Lookups** section, select **ApplicableDebitNote**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification ID** field, select the appropriate document class (vendor debit note).

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification ID** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification ID** field, select **Not Blank**.

1. In the **Lookups** section, select **TaxType**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Tax credit**.
    1. In the **Tax code** field, select an option that represents the VAT.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Vat Cost**.
    1. In the **Tax code** field, select an option that represents the VAT charged at cost.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Vat Return**.
    1. In the **Tax code** field, select an option that represents the VAT in sales returns.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Type of tax** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Type of tax** field, select **Not Blank**.

1. In the **Lookups** section, select **ApplicableCreditNote**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification ID** field, select the appropriate document class (vendor credit note).

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification ID** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification ID** field, select **Not Blank**.

> [!NOTE]
> Use the selected tax codes in the company transactions included in the report.

> [!NOTE]
> Apply the lookup settings to both formats.

## Issue file format 1005

To issue file format 1005, follow these steps.

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **File format 1005**, then select **OK**.
1. Enter the Tax Application ID and date range, then select **OK**.


## Generate Format 1005 report in Excel

To generate Format 1005 report in Excel, follow these steps.

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **File format 1005 Excel**.
1. Select **OK**.
1. Select a date range.
1. Select **OK**.

> [!NOTE]
> When you run the Format 1005 report in Excel, you don't need to enter a value in the **Tax Application ID** field in the report launcher.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
