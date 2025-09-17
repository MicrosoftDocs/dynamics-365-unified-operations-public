---
title: Format 1012 file for Colombia configuration
description: Learn how to set up and issue a format 1012 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 09/17/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure format 1012 file for Colombia

Set up and issue a format 1012 file. The file lists company investments you provide to the tax authority. The process outputs two files: an XML file that meets official tax requirements, and an Excel file for internal control.

## Prerequisites

Before you print the report, meet these prerequisites:

- Set the legal entity address to a location in Colombia.
- Enable the country-specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import these configurations from Dataverse:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   |:::no-loc text="LTM Tax Report":::                 |
| Mapping | :::no-loc text="LTM Tax Report mapping":::|
| Format  | :::no-loc text="File format 1012":::      |
| Format  | :::no-loc text="File format 1012 Excel":::  |

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Set up Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application codes

Run the Form 1012 report in Dynamics 365 Finance and Operations by setting up a **Tax Application Id**.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record with code **1012** for format 1012.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. Select a record, and then select **Tax application**.

Configure codes for **Tax ID types**:

1. On the **Tax application** page, in the **Tax application id** field, enter the code for Colombian format 1012.
1. In the **Tax application code** field, enter the tax ID code according to Colombian regulation.

Configure codes for countries:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**, and for each country/region go to **LATAM** \> **Tax application** to assign the tax application codes according to Colombian regulation.

Proper setup of these tax application codes helps the report reflect taxable operations and comply with DIAN requirements.

For more information, see [Tax application for Latin America](../ltm-core-tax-application.md).

## Configure application specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and ledger account numbers that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
1. Select **LTM Tax Report deployment** \> **Format 1012**.
1. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select the first lookup, **MainAccountGroup**, that refers to the main account group.
1. In the **Conditions** section, add a line, then in **Lookup result**, select a value.
1. In **Main account**, select the ledger account for the concept.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are included in the report.

1. In the **Lookups** section, select the second lookup, **PaymentMethodId**. This lookup refers to the payment method document class used to post transactions for each concept in the **MainAccountGroup** lookup.
1. In the **Conditions** section, add a line, then in **Lookup result**, select **PaymentMethodClass**.
1. In the **Document classification Id** field, select the document class used in the transactions included in the report.

    > [!NOTE]
    > For each **Lookup**, add two conditions where the **Lookup result** is **N/A** for both. The **Main account ID** for the first condition should be **"Blank"** and the Main account ID** for the second condition should be **"Not blank"**. 

    > [!NOTE]
    > The lookup settings must be applied to both formats to be used.

## Generate file format 1012 file

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **File format 1012**, and then select **OK**.
1. Specify the **Tax Application ID** for this format.
1. Select a date range, and then select **OK**.

## Generate a Format 1012 Excel file
1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, select **File format 1012 Excel**, and then select **OK**.
1. Select the date range, and then select **OK**.
1. Enter the code for this report in the **Tax application Id** field (if required), and then select **OK**.

> [!NOTE]
> When executing the Format 1012 report in Excel, it is not necessary to populate the Tax Application ID field in the report launcher."

