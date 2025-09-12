---
title: Format 1005 file for Colombia configuration
description: Learn about the configuration that's required to issue the format 1005 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 04/29/2025 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1005 file for Colombia configuration

This article explains the configuration required to generate the Format 1005 file. This report provides information about the deductible VAT related to purchases and sales returns. It includes two format outputs, an XML file that meets the official tax requirements and an Excel file for internal control purposes.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The legal entity must have an address in a country/region within the Latin American (LATAM) localization.
- The country/region specific LATAM feature and the general feature must be activated.
- The following configurations must be imported from the Dataverse:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   |:::no-loc text="LTM Tax Report":::                 |
| Mapping | :::no-loc text="LTM Tax Report mapping":::|
| Format  | :::no-loc text="File format 1005:::      |
| Format  | :::no-loc text="File format 1005 (Excel)":::  |

    For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- The Electronic reporting (ER) parameters must be configured. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure tax applications codes

To execute Form 1005 reports in Dynamics 365 Finance and Operations, you need to set up a Tax Application Id.

* Go to **Organization Administration** \> **Settings** \> **LATAM** \> **Tax Application** and select **New** to create a tax application record with code **1005** (for format 1005). 

You must configure the tax application code for the **Tax Id Type**:
* Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type** and for each record from the list go to **Tax application** in the top menu and create a new record to configure a tax application code in accordance with the fiscal normative.

A proper setup of these tax application codes is essential for the report to correctly reflect taxable operations and comply with DIAN requirements.

For more information, see [Tax application for Latin America]( ltm-core-tax-application.md).

## Configure application-specific parameters for format 1005

Lookups and conditions are designed so that you can select the combination of document classification IDs and tax codes that are used in transactions that are shown in the report.

After the previously listed prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting** and select **Reporting configuration**.
2. In the tree on the left, select **LTM Tax Report deployment** \> **Format 1005**.
3. On the top menu, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. This lookup lets you select the document classes that are used for vendor invoices that contain VAT.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (vendor invoices).

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

8. In the **Lookups** section, select **ApplicableDebitNote**.
9. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (vendor debit note).

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

12. In the **Lookups** section, select **TaxType**.
13. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Tax credit**.
    2. In the **Tax code** field, select an option that represents the VAT.

14. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Vat Cost**.
    2. In the **Tax code** field, select an option that represents the VAT charged at cost.

14. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Vat Return**.
    2. In the **Tax code** field, select an option that represents the VAT returns in sales returns.

15. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

16. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

17. In the **Lookups** section, select **ApplicableCreditNote**.
18. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (vendor credit note).

19. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

20. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

> [!NOTE]
> The tax codes that are selected in this configuration must be used in the company transactions that are included on the report.

> [!NOTE]
> The lookup settings must be applied to both formats to be used.

## Issue format 1005 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1005 **.
3. Select **OK**.
4. Specify the Tax Application ID applicable to this format.
4. Select a date range.
5. Select **OK**.

## Issue a format 1005 file in excel format

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **File format 1005 Excel**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.

> [!NOTE]
> When executing the Format 1005 report in Excel, it is not necessary to populate the Tax Application ID field in the report launcher.
