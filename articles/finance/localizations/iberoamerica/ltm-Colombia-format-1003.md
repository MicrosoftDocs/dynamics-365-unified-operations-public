---
title: Format 1003 file for Colombia configuration
description: Learn about the configuration required to issue the format 1003 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 08/26/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1003 file for Colombia configuration

This article explains the configuration required to issue a format 1003 file. The report shows information about withholding taxes the company incurred during a period and the related entities.
This article provides the configuration requirements for issuing the XML and Excel format versions of the file format 1003.

> [!NOTE]
> The fiscal requirements are covered with the XML output format. The Excel output format is for management purposes.

## Prerequisites

Before printing the report, ensure the following prerequisites are met:

- The legal entity must have an address in a country/region that is within the Latin American (LATAM) localization.
- Activate the country/region-specific LATAM feature and the general feature.
- Import the following configuration from the Dataverse Configuration Repository:

    - :::no-loc text="LTM Tax Report”:::
    - :::no-loc text="LTM Tax Report Mapping”:::
    - :::no-loc text="File format 1003”:::
    - :::no-loc text="File format 1003 Excel”::: 

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).

- Configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with the code **1003** (for format 1003).
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list.
1. Select a record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code used for Colombian format 1003.
1. In the **Tax application code** field, enter the code for tax IDs according to Colombian regulations.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (Country/Region, State, and County), go to **LATAM** \> **Tax application** to assign the tax application codes according to Colombian regulations.

## Configure application-specific parameters for format 1003

Lookups and conditions are designed so that you can select the combination of document classification IDs, tax codes, and ledger accounts used in the transactions shown on the report.

After you meet the previously listed prerequisites, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
1. In the tree on the left, select **LTM Tax Report** \> **File format 1003** or **LTM Tax Report** \> **File format 1003 Excel**.
1. For each format, on the top menu, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. This lookup lets you choose the document classes used to post partner sales transactions.
1. In the **Conditions** section, select **Add**, and follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification ID** field, select the appropriate document class (usually sales invoices or debit notes).

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification ID** field, select **Not Blank**.

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions listed on the report.

1. In the **Lookups** section, select **Concept**.
1. In the **Conditions** section, select **Add**, and choose every required concept.

1. For each one, in the **Tax code** field, choose a tax code that represents the concept.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Type of tax** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Type of tax** field, select **Not Blank**.

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions listed on the report.

## Run a format 1003 file

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select the format mapping **File format 1003** or **File format 1003 Excel**.
1. Select **OK**.
1. For **File format 1003**, in **Tax application Id**, enter the tax application **1003** created for this report.
1. Select **OK**.
1. Specify a date range.
1. Select **OK**.
