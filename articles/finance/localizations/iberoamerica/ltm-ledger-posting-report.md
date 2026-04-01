---
title: Print a Ledger Posting report for LATAM
description: Learn how to print a Ledger Posting report for Latin America, including prerequisites and a process for printing a ledger posting report.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Print a Ledger Posting report for LATAM

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

This article explains how to print a **Ledger Posting** report for Latin America.

## Prerequisites

Before you can print a **Ledger Posting** report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- You must enable the country/region-specific LATAM feature and the general feature.
- Download the specific report configurations from the Dataverse configuration repository. These formats are applicable to all LATAM countries, except Bolivia.

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Ledger Accounting LATAM":::                               |
| Format  | :::no-loc text="Ledger Posting LATAM":::                         |

> [!IMPORTANT]
> For Bolivia, :::no-loc text="Ledger Posting Bolivia"::: must be imported instead.

Learn more in [Import electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

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
1. In the **Ledger posting report** dialog box, configure the filters for the report.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. In the **Account number** field, select the account number if you want to print the transactions for a specific account.
1. Select the posting layers to include on the report.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
