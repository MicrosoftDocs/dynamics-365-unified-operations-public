---
title: Format 1007 file for Colombia configuration
description: Learn how to set up and issue a format 1007 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/21/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1007 file for Colombia configuration

This article explains how to set up and issue a format 1007 file. The format 1007 file provides information about the revenue that the company received during a period.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in Colombia.
- Enable the country-/region-specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository:

    - LTM Tax Report
    - Format 1007 format

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of documents classification IDs and sales tax codes that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1007**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **InvoiceAndCreditNoteIsApplicable**. Use this lookup to select the document classes that are used for invoice and credit note transactions that contain the company revenue.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select a value.

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are listed on the report.

8. In the **Lookups** section, select **MainAccountGroup**.
9. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select one of the following values:

        - 4001: Common activities revenue
        - 4002: Other activities revenue
        - 4003: Financial interest revenue
        - 4004: Mortgage interest revenue

    2. In the **Main Account** field, select a value.

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Main account** field, select **Blank**.

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Main account** field, select **Not Blank**.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are listed on the report.

## Issue a format 1007 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1007**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.
