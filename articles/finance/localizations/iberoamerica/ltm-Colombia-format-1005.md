---
title: Format 1005 file for Colombia configuration
description: Learn about the configuration that's required to issue the format 1005 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/20/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1005 file for Colombia configuration

This article explains the configuration that's required to issue a format 1005 file. This report provides information about the value-added tax (VAT) that's generated in purchase and sales transactions.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The legal entity must have an address in a country/region within the Latin American (LATAM) localization.
- The country-specific or region-specific LATAM feature and the general feature must be activated.
- The following configurations must be imported from the Global repository:

    - LTM Tax Report
    - Format 1005 file

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- The Electronic reporting (ER) parameters must be configured. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1005

Lookups and conditions are designed so that you can select the combination of document classification IDs and tax codes that's used in the transactions that are shown on the report.

After the previously listed prerequisites are met, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
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

    > [!NOTE]
    > The document classes that are selected in this configuration must be used in the company transactions that are included on the report.

12. In the **Lookups** section, select **TaxType**.
13. In the **Conditions** section, select **Add**, and then follow these steps:

    1. In the **Lookup result** field, select **Tax credit**.
    2. In the **Tax code** field, select an option that represents the VAT.

14. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **Vat Return**.
    2. In the **Tax code** field, select an option that represents the VAT returns in sales returns.

15. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

16. Select **Add** again, and then follow these steps:

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes that are selected in this configuration must be used in the company transactions that are included on the report.

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

## Issue a format 1005 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1009**.
3. Select **OK**.
4. Select a date range.
5. Select **OK**.
