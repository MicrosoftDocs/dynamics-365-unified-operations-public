---
title: Format 1003 file for Colombia configuration
description: Learn about the configuration that's required to issue the format 1003 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 11/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1003 file for Colombia configuration

This article explains the configuration that's required to issue a format 1003 file. This report provides information about withholding taxes that the company incurred during a period and the related entities.
This article provides the configuration requirements for issuing the XML format and excel format versions of the file format 1003.

> [!NOTE]
> The fiscal requirements are covered with the XML output format, the excel output format is for management purposes.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that is within the Latin American (LATAM) localization.
- The country/region specific LATAM feature and the general feature must be activated.
- The following configuration must be imported from the Dataverse Configuration Repository:

    - :::no-loc text="LTM Tax Report”:::
    - :::no-loc text="LTM Tax Report Mapping”:::
    - :::no-loc text="File format 1003”:::
    - :::no-loc text="File format 1003 Excel”::: 

For more information, see [Import Electronic reporting (ER) configurations from Dataverse](gsw-import-er-config-dataverse.md).
    
- The Electronic reporting (ER) parameters must be configured. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure Tax application

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application** and select **New** to create a tax application record that has the code **1003** (For format 1003). 
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:
1. Select the record, and then select **Tax application**.
1. On the **Tax application** page, in the **Tax application id** field, enter the code that is used for Colombian format 1003.
1. In the **Tax application code** field, enter the code for tax IDs according to the Colombian regulatory.
1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record (Country/Region, State and County) go to **LATAM** \> **Tax application** to assign the tax application codes for according to the Colombian regulatory.

## Configure application-specific parameters for format 1003

Lookups and conditions are designed so that you can select the combination of document classification IDs, tax codes, and ledger accounts that's used in the transactions that are shown on the report.

After the previously listed prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. In the tree on the left, select **LTM Tax Report** \> **File format 1003** or **LTM Tax Report** \> **File format 1003 Excel**.
3. For each format, go on the top menu, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. This lookup lets you select the document classes that are used to post third-party sales transactions.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (usually sales invoices or debit notes).

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

> [!NOTE]
> The document classes that are selected in this configuration must be used in the company transactions that will be listed on the report.

8. In the **Lookups** section, select **Concept**.
9. In the **Conditions** section, select **Add**, and select every concept that is required.

 2. For each one, in the **Tax code** field, select a tax code that represents the concept.

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

> [!NOTE]
> The tax codes that are selected in this configuration must be used in the company transactions that will be listed on the report.

## Run a format 1003 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select the format mapping **File format 1003** or **File format 1003 Excel**.
3. Select **OK**.
4. For **File format 1003**, in Tax application Id, complete with the tax application **1003** created for this report.
5. Select **OK**.
6. Select a date range.
7. Select **OK**.
