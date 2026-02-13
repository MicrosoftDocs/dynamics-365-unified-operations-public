---
title: Format 1001 file for Colombia issue configuration
description: Learn about the required configuration for issuing the format 1001 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 10/07/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1001 file for Colombia issue configuration

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up and configure information so that you issue a format 1001 file. The **Format 1001 file** report provides a list of expenses that you paid to third parties, and the taxes and withholding taxes that those transactions generated.
This article provides the configuration requirements for issuing the XML format and Excel format versions of the File format 1001.

> [!NOTE]
> The XML output format covers the fiscal requirements. The Excel output format is for management purposes.

## Prerequisites

Before you print this report, meet the following prerequisites:

- The legal entity has an address in a country/region within the Latin American (LATAM) localization.
- Both the country/region-specific LATAM feature and the general feature are enabled.
- Import the required configurations from the Global repository:

    - :::no-loc text="LTM Tax Report":::
    - :::no-loc text="LTM Tax Report mapping":::
    - :::no-loc text="File Format 1001":::
    - :::no-loc text="File format 1001 Excel":::

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Set up the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
## Configure tax application codes

These reports use tax application codes. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).

Go to **Organization administration > Setup > LATAM > Tax ID type**, and for each record, follow these steps:
1. Go to **Tax application** in the top menu.
1. Create a new record.
1. In the **Tax application Id** field, select the tax application created for these formats. 
1. In the **Tax application code** field, enter the document type code according to the Colombian normative.
Go to **Organization administration > Global address book > Addresses > Address setup** and for Countries/Regions, States, and Counties records follow these steps:
1. Go to **LATAM > Tax application** on the top menu.
1. Create a new record.
1. In the **Tax application Id** field, select the tax application created for these formats. 
1. In the **Tax application code** field, enter the code according to the Colombian normative.

## Configure application-specific parameters for format 1001

Lookups and conditions are designed so that you can select the combination of document classification IDs, tax codes, and ledger accounts that are used in the transactions that appear on the report.

After you meet the prerequisites and configure the tax application codes, follow these steps for both formats:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On the left, select **LTM Tax Report** \> **File Format 1001** for the XML output or **File format 1001 Excel** for the Excel output.
1. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. Use this lookup to select the document classes that are used to post third-party expenses.
1. In the **Conditions** section, select **Add**, and then follow these steps for every document class that you use in transactions that should appear in the 1001 format:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification id.** field, select the appropriate document class (usually vendor invoices or debit notes). 

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification id.** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification id.** field, select **Not Blank**.

1. In the **Lookups** section, select **MainAccountGroup\_NoDeduc**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup Result** field, select the desired concept code.
    1. In the **Main account id** field, select a ledger account that represents the code you selected. 

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account id** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account id** field, select **Not Blank**.

1. In the **Lookups** section, select **TaxType**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select the following values:

        - **COMUN** – VAT withholding practiced common regime.
        - **IDED** – VAT higher value of the deductible cost or expense.
        - **INDED** – VAT higher value of the non-deductible cost or expense.
        - **NO DOM** – VAT withholding practiced to foreign 3rd parties.
        - **RETA** – Income withholding tax suffered.
        - **RTPE** – Income withholding tax assumed.

    1. In the **Tax code** field, select the appropriate tax code for each concept lookup result that you added.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Tax code** field, select **Blank**.

1. Select **Add** again, then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Tax code** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes, ledger accounts, and document classes you select in this configuration must be used in the company transactions. Otherwise, they don't appear on the report.

## Issue a format 1001 file for XML and Excel output

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **File Format 1001** or **File format 1001 Excel**.
1. Select **OK**.
1. For the XML output format, enter the tax application ID used for the format in the **Tax application Id** field.
1. Select a date range, then select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
