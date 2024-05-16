---
title: Format 1006 file for Colombia configuration
description: Learn about the configuration that's required to issue the format 1006 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/21/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1006 file for Colombia configuration

This article explains how to set up and issue a format 1006 file. This report includes value-added tax (VAT) that's generated in sales and purchase transactions, and consumption taxes.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The legal entity must have an address in a country within the Latin American (LATAM) localization.
- Activate the country-specific LATAM feature and the general feature.
- Import the following configurations from the Global repository:

    - LTM Tax Report
    - Format 1006 file

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1006

Lookups and conditions are designed so that you can select the combination of document classification IDs and tax codes that's used in the transactions that are shown on the report.

After the prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1006**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableCreditNote**. Use this lookup to select the document classes that are used for purchases that contain VAT.
5. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select a value.

6. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

7. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not blank**.

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are listed on the report.

8. In the **Lookups** section, select **TaxType**.
9. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup Result** field, select **Consumption tax**.
    2. In the **Tax code** field, select an option that represents consumption taxes.

10. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Generated tax**.
    2. In the **Tax code** field, select a value that represents the VAT that's generated in sales.

11. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Tax refund**.
    2. In the **Tax code** field, select an option that represents the VAT returns in purchase returns.

12. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

13. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes that are selected in this configuration must be used in the company transactions that are listed on the report.

14. In the **Lookups** section, select **ApplicableInvoice**.
15. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Yes**.
    2. In the **Document classification id.** field, select the appropriate document class (purchase invoices).

16. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Blank**.

17. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **No**.
    2. In the **Document classification id.** field, select **Not Blank**.

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are listed on the report.

## Issue format 1006 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1006**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.
