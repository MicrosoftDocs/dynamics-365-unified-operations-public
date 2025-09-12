---
title: Format 1012 file for Colombia configuration
description: Learn how to set up and issue a format 1012 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 02/26/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1012 file for Colombia configuration

This article explains how to set up and issue a format 1012 file. The format 1012 file includes information about company investments that must be provided to the tax authority. It includes two format outputs, an XML file that meets the official tax requirements and an Excel file for internal control purposes.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in Colombia.
- Enable the country-specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import the following configurations from the Dataverse:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   |:::no-loc text="LTM Tax Report":::                 |
| Mapping | :::no-loc text="LTM Tax Report mapping":::|
| Format  | :::no-loc text="File format 1012:::      |
| Format  | :::no-loc text="File format 1012 Excel":::  |

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax application codes

To execute the Form 1012 report in Dynamics 365 Finance and Operations, you need to set up a **Tax Application Id**.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **1012** (For format 1012). 
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.

It is also necessary to configure the codes for **Tax ID types**:

1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Colombian format 1012.
1. In the **Tax application code** field, enter the code for tax IDs according to the Colombian regulatory.

It is also necessary to configure the codes for countries:

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (Country/Region) go to **LATAM** \> **Tax application** to assign the tax application codes for according to the Colombian regulatory.

Proper setting up of these Tax Application codes is essential for the report to correctly reflect taxable operations and comply with DIAN requirements.

For more information, see [Tax application for Latin America](../ltm-core-tax-application.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and ledger account numbers that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1012**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup that refers to the main account group, **MainAccountGroup**.
5. In the **Conditions** section, add a line. In the **Lookup result** field, select a value.
6. In the **Main account** field, select the ledger account that represents the concept.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are included in the report.

8. In the **Lookups** section, select the second lookup, **PaymentMethodId**. This lookup refers to the payment method document class that's used to post transactions for each concept in the **MainAccountGroup** lookup.
9. In the **Conditions** section, add a line. In the **Lookup result** field, select **PaymentMethodClass**.
10. In the **Document classification Id** field select the document class used in the transactions that are included in the report.

    > [!NOTE]
    > For each **Lookup**, add two conditions where the **Lookup result** is **N/A** for both. The **Main account ID** for the first condition should be **"Blank"** and the Main account ID** for the second condition should be **"Not blank"**. 

    > [!NOTE]
    > The lookup settings must be applied to both formats to be used.

## Issue format 1012 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1012**.
3. Select **OK**.
4. Specify the Tax Application ID applicable to this format.
5. Select a date range.
6. Select **OK**.

## Issue a format 1012 file in excel format
1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1012 Excel**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.
6. Complete the **Tax application Id** field with the code created for this report.
7. Select the date range. 
8. Select **OK**.

> [!NOTE]
> When executing the Format 1012 report in Excel, it is not necessary to populate the Tax Application ID field in the report launcher."

