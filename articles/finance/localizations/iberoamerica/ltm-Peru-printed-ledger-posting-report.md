---
title: Set up and generate a printed ledger posting report for Peru
description: Learn how to set up and generate a printed ledger posting report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate a printed ledger posting report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate a printed ledger posting report for Peru in Microsoft Dynamics 365 Finance.

The printed ledger posting report provides balance information for all ledger accounts, together with the transaction date, voucher, and journal description. It shows the information in a format that is suitable for printing.

## Prerequisites

Before you can generate and print the report, you must complete the following prerequisites:

- The country/region of the legal entity's address must be in Peru.
- You must enable both the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository.
- You must import the following Electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    - Ledger accounting reports
    - Ledger accounting LATAM
    - Libro Mayor PE

- You must configure the ER parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a new SQL Server Reporting Services (SSRS) Reports/Services reference and configure it in the following way:

    1. In the **Report/Service ID** field, enter **PrintLPost**.
    1. In the **Report/Service name** field, enter **PrintLPost**.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger accounting LTM**.
    1. In the **Data model definition** field, select **LedgerPosting**.
    1. In the **Format mapping** field, select **Libro Mayor PE**.
    1. In the list of report/service types, enable **Ledger Posting report**.

## Print the ledger posting report for Peru

To print the ledger posting report for Peru, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquiries and reports** \> **LATAM** \> **Ledger Posting Report**.
1. In the **Ledger posting report** dialog, configure the filters for the report.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** field, enter the beginning of the date range for the transactions that you want to print.
1. In the **To date** field, enter the end of the date range for the transactions that you want to print.
1. If you want to print the transactions for a specific account, select the account number in the **Account number** field.
1. Select the posting layers that you want.
1. Select **Print**.
