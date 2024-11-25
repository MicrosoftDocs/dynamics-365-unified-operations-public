---
title: Format 1003 file for Colombia configuration
description: Learn about the configuration that's required to issue the format 1003 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1003 file for Colombia configuration

This article explains the configuration that's required to issue a format 1003 file. This report provides information about withholding taxes that the company incurred during a period and the related entities.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The legal entity must have an address in a country within the Latin American (LATAM) localization.
- The country-specific LATAM feature and the general feature must be activated.
- The following configurations must be imported from the Global repository:

    - LTM Tax Report
    - Format 1003 file

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- The Electronic reporting (ER) parameters must be configured. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1003

Lookups and conditions are designed so that you can select the combination of document classification IDs, tax codes, and ledger accounts that's used in the transactions that are shown on the report.

After the previously listed prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. In the tree on the left, select **LTM Tax Report deployment** \> **Format 1003**.
3. On the top menu, select **Configurations** \> **Application specific parameters** \> **Setup**.
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
9. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup Result** field, select one or more of the following options:

        - **1301** – Withholding for salaries, benefits, and other labor payments.
        - **1302** – Sales withholdings.
        - **1303** – Withholding taxes for services.
        - **1304** – Withholding taxes for fees.
        - **1305** – Withholding taxes for commissions.
        - **1306** – Withholding taxes for interest and financial returns.
        - **1307** – Withholding taxes for leases.
        - **1308** – Withholding taxes for other concepts.
        - **1309** – Sales tax withholdings.
        - **1310** – Withholding for dividends and participations. This withholding doesn't include the value that's reported in concept 1320.
        - **1311** – Withholding taxes for the sale of fixed assets of natural persons.
        - **1312** – Withholding taxes for deposits from debit and credit cards.
        - **1313** – Withholding taxes for lotteries, raffles, bets, and similar.
        - **1314** – Withholding taxes for stamp taxes.

    2. In the **Tax code** field, select a tax code that represents the concept.

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes that are selected in this configuration must be used in the company transactions that will be listed on the report.

## Issue a format 1003 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1003**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.
