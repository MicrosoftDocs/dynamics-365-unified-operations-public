---
title: Print a Ledger Posting report for LATAM
description: Learn how to print a Ledger Posting report for Latin America, including prerequisites and a process for printing a ledger posting report.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/06/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Print a Ledger Posting report for LATAM

[!include [banner](../../includes/banner.md)]

This article explains how to print a **Ledger Posting** report for Latin America.

## Prerequisites

Before you can print a **Ledger Posting** report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- You must enable the country/region-specific LATAM feature and the general feature.
- The following Electronic reporting (ER) configurations must be imported:

    - Ledger accounting reports
    - Ledger Accounting LATAM
    - Ledger posting

    For more information about ER configurations, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- You must create a new SSRS Reports/Services reference and configure it in the following way:

    - In the **Report/Service Id** field, enter **LedgerPosting**.
    - In the **Report/Service name** field, enter **LedgerPost**.
    - In the **Report/Service type** field, select an ER configuration.
    - In the **Model mapping name** field, select **Ledger accounting LTM**.
    - In the **Data model definition** field, select **LedgerPosting**.
    - In the **Format mapping** field, select **Ledger Posting LATAM**.
    - In the list of report/service types, enable **Ledger Posting**.

## Print the Ledger Posting report for Latin America

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **Ledger Posting Report**.
2. In the **Ledger posting report** dialog box, configure the filters for the report.
3. In the **Report ID** field, select the corresponding report/service ID.
4. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
5. In the **Account number** field, select the account number if you want to print the transactions for a specific account.
6. Select the posting layers to include on the report.
7. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
