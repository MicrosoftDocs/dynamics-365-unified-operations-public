---
title: Format 1001 file for Colombia issue configuration
description: Learn about the required configuration for issuing the format 1001 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/10/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1001 file for Colombia issue configuration

This article explains how to set up and configure information so that you can issue a format 1001 file. The **Format 1001 file** report provides a list of expenses that were paid to third parties, and the taxes and withholding taxes that those transactions generated.

## Prerequisites

Before you print this report, the following prerequisites must be met:

- The legal entity has an address in a country within the Latin American (LATAM) localization.
- Both the country/region-specific LATAM feature and the general feature are activated.
- Import the required configurations from the Global repository:

    - LTM Tax Report
    - Format 1001 file

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1001

Lookups and conditions are designed so that you can select the combination of document classification IDs, tax codes, and ledger accounts that's used in the transactions that are shown on the report.

After the prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1001**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. Use this lookup to select the document classes that are used to post third-party expenses.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (usually vendor invoices or debit notes). 

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes that are selected in this configuration must be used in the company transactions. Otherwise, they aren't listed on the report.

8. In the **Lookups** section, select **MainAccountGroup\_NoDeduc**.
9. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup Result** field, select **5007**.
    2. In the **Tax code** field, select a ledger account that represents non-fixed assets. 

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **5008**.
    2. In the **Main account** field, select a ledger account that represents fixed assets. 

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

12. In the **Concepts** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

13. In the **Lookups** section, select **MainAccountGroup**.
14. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup Result** field, select **5007**.
    2. In the **Tax code** field, select a ledger account that represents non-fixed assets.

15. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **5008**.
    2. In the **Main account** field, select a ledger account that represents fixed assets. 

16. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

17. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions. Otherwise, they aren't listed on the report.

18. In the **Lookups** section, select **TaxType**.
19. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select the following values:

        - **COMUN** – VAT withholding practiced common regime.
        - **IDED** – VAT higher value of the deductible cost or expense.
        - **INDED** – VAT higher value of the non-deductible cost or expense.
        - **NO DOM** – VAT withholding practiced to foreign.
        - **RASUMC** – CREE withholding suffered.
        - **RECREE** – CREE withholding practiced.
        - **RETA** – Income withholding tax suffered.
        - **RTPE** – Income withholding tax practiced.
        - **SIMP** – VAT withholding suffered simplified regime.

    2. In the **Tax code** field, select the appropriate tax code for each concept lookup result that you added.

20. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Tax code** field, select **Blank**.

21. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Tax code** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes that are selected in this configuration must be used in the company transactions. Otherwise, they aren't listed on the report.

## Issue a format 1001 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1001**.
3. Select **OK**.
4. Select a date range, and then select **OK**.
