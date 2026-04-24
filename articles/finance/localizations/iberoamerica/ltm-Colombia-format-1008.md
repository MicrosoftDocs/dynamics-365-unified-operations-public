---
title: Format 1008 file for Colombia configuration
description: Learn how to set up and issue a format 1008 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 04/13/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1008 file for Colombia configuration

This article explains how to set up and issue a format 1008 file. The format 1008 file provides information about the company's credit assets.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in a country within the Latin American (LATAM) localization.
- Enable the country-specific LATAM globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository:

  - LTM Tax Report
  - Format 1008 file

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and ledger account numbers that's used in the transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
1. On the left, select **LTM Tax Report deployment** \> **Format 1008**.
1. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
1. In the **Lookups** section, select the first lookup, **IsApplicable**. Use this lookup to select the document classes that are used for customer invoices, credit notes, debit notes, and customer payment transactions.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    1. In the **Document classification id.** field, select the appropriate document class.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification id.** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    1. In the **Document classification id.** field, select **Not Blank**.

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are listed on the report.

1. In the **Lookups** section, select **MainAccountGroups**.
1. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select one of the following options:

        - **1315** – Accounts receivable from customers.
        - **1316** – Accounts receivable from shareholders, partners, community members, cooperative members, and related companies.
        - **1317** – Other accounts receivable.
        - **1318** – The tax value of the portfolio impairment.

    1. In the **Main Account** field, select a ledger account that's used for the concept that you selected in the **Lookup result** field.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account** field, select **Blank**.

1. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    1. In the **Main account** field, select **Not Blank**.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are listed on this report.

## Issue a format 1008 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **Format 1008**.
1. Select **OK**.
1. Select a date range.
1. Select **OK**.
