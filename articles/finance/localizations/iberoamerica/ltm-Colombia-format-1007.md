---
title: Format 1007 file for Colombia configuration
description: Learn how to set up and issue a format 1007 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 11/21/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1007 file for Colombia configuration

This article explains how to configure and issue a file in 1007 format. This format records for each third party the income received by a natural or legal person during the taxable year including both operating and non-operating income.

> [!NOTE]
> The XML output format covers the fiscal requirements. The Excel output format is for management purposes.

## Prerequisites

Before generating and printing the report, you must first complete the following prerequisites:

- The country/region of the legal entity's address must be in Colombia. 
- Enable the country/region-specific Latin American (LATAM) feature for Colombia and the general LATAM feature.
- Download the specific report configurations from the Dataverse configuration repository:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   |:::no-loc text="LTM Tax Report":::                 |
| Mapping | :::no-loc text="LTM Tax Report mapping":::|
| Format  | :::no-loc text="File format 1007:::      |
| Format  | :::no-loc text="File format 1007 (Excel)":::  |

- Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the **Electronic Reporting (ER)** parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax applications

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and create a new record.
1. On the **Tax application Id** field complete with **1007**.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup** \> **Country/region**.
1. Select **Colombia** and go to **LATAM** \> **Tax application**.
1. Create a new record.
1. In the **Tax application Id** field, select **1007**.
1. In the **Tax application code** field, enter the country code according to the Colombian normative.
1. Go to **Organization Administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. On the top menu, go to **Tax application** and create a new record.
1. In the **Tax application Id** field, select **1007**.
1. In the **Tax application code** field, enter the tax ID code according to the Colombian normative.

For more information, see [Tax application for Latin America](ltm-core-tax-application.md).

## Configure application-specific parameters for format 1007

Lookups and conditions are designed so you can select the combination of document classifications and tax codes used in transactions.

After you meet the prerequisites and configure the tax application codes, follow these steps for both formats:
1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting** and select **Reporting configuration**.
1. On the left, select **LTM Tax Report** \> **File format 1007**.
1. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select **InvoiceAndCreditNoteIsApplicable** and follow this steps:
   1. In the **Conditions** section, select **Add**.
   1. In the **Lookup result** field, select **Yes**.
   1. In the **Document classification id.** field, select a document class used for purchase invoices that contain VAT.
1. In the **Lookups** section, select **MainAccountGroups** and follow this steps: 
   1. In the **Conditions** section, select **Add**.
   1. In the **Lookup result** field, select **Yes**.
   1. In the **Document classification id.** field, select a document class used in company transactions.
1. In the **Lookups** section, select **TaxType** and then follow these steps:
   1. In the **Conditions** section, select **Add**.
    1. In the **Lookup result** field, select **Generated tax**.
    1. In the **Tax code** field, select a value that represents the VAT generated in sales.
   1. Select **Add**.
    1. In the **Lookup result** field, select **Tax refund**.
    1. In the **Tax code** field, select an option that represents the VAT returns in purchase returns.
1. In the **Lookups** section, select **ApplicableInvoice** and then follow these steps:
   1. In the **Conditions** section, select **Add**.
   1. In the **Lookup result** field, select **Yes**.
   1. In the **Document classification id.** field, select a document class used for purchase invoices.

> [!NOTE]
> To ensure the report shows transactions that meet the configured conditions, complete the **Lookup result** field as **N/A** with **Blank** and **Not blank** conditions for all **Lookup** records.

> [!NOTE]
>The tax codes and document classes you select in this configuration must be used in the company transactions. Otherwise, they will not appear in the report.

## Issue a format 1007 file for XML and Excel output

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **File format 1007** for the XML output or **File format 1007 (Excel)** for the excel output.
1. For the XML output only, enter **1007** in the **Tax application ID** field.
1. Select a date range.
1. Select **OK**.
