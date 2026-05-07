---
title: Print a Ledger Posting report for LATAM
description: Learn how to print a Ledger Posting report for Latin America, including prerequisites and a process for printing a ledger posting report.
author: MatiasPizmeny01
ms.author: v-mpizmeny
ms.topic: how-to
ms.date: 04/28/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Print a Ledger Posting report for LATAM

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

This article explains how to print a **Ledger Posting** report for Latin America.

## Prerequisites

Before you can print a **Ledger Posting** report, ensure the following prerequisites are met:

- The legal entity has an address in a country or region that's within the LATAM localization.
- You enable the country or region-specific LATAM feature and the general feature.
- You download the specific report configurations from the Dataverse configuration repository.

| Element |                    Format name                    | Country or Region |
|:-------:|:-------------------------------------------------:|:---------------------------------------:|
| Model   | :::no-loc text="Ledger accounting reports":::    | All LATAM countries/regions |
| Model   | :::no-loc text="Ledger Accounting LATAM":::      | All LATAM countries/regions |
| Format  | :::no-loc text="Ledger Posting LATAM":::         | All LATAM countries/regions excluding Bolivia |
| Format  | :::no-loc text="Ledger Posting Bolivia":::         | Bolivia |

Learn more in [Import electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure SSRS Reports / Services references

- Create a new SSRS Reports/Services references record and configure it as follows:

  - In the **Report/Service Id** field, enter **LedgerPosting**.
  - In the **Report/Service name** field, enter a descriptive name.
  - In the **Report/Service type** field, select an ER configuration.
  - In the **Model mapping name** field, select **:::no-loc text="Ledger accounting LTM":::**.
  - In the **Data model definition** field, select **:::no-loc text="Ledger Posting":::**.
  - In the **Format mapping** field, select **:::no-loc text="Ledger Posting LATAM":::** (**:::no-loc text="Ledger Posting Bolivia":::** for Bolivia).
  - In the list of report/service types, enable **Ledger Posting**.

## Print the Ledger Posting report for Latin America

1. Go to **General Ledger** > **Inquiries and Reports** > **LATAM** > **Ledger Posting Report**.
1. In the **Report ID** field, select the corresponding report or service ID.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. In the **Ledger account** field, select the account number if you want to print the transactions for a specific account.
1. Set the **Start page number** field.
1. Select the posting layers to include on the report.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
