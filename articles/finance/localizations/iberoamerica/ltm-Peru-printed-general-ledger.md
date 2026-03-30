---
title: Set up and generate a printed general ledger report for Peru
description: Learn how to set up and generate a printed general ledger report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate a printed general ledger report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate a printed general ledger report for Peru in Microsoft Dynamics 365 Finance.

The printed general ledger report provides detailed information about all transactions that are recorded in the journal, together with the transaction date, journal number, main account, and description. It shows the information in an Excel printout format.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The country/region of the legal entity's address must be in Peru.
- You must enable both the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository.
- You must import the following Electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    - Ledger accounting reports
    - Ledger accounting LATAM
    - General ledger PE

- You must configure the ER parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a new SQL Server Reporting Services (SSRS) Reports/Services reference and configure it in the following way:

    1. In the **Report/Service ID** field, enter **PrintGL**.
    1. In the **Report/Service name** field, enter **PrintGLedger**.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger accounting LTM**.
    1. In the **Data model definition** field, select **GeneralLedger**.
    1. In the **Format mapping** field, select **General ledger PE**.
    1. In the list of report/service types, enable **General Ledger**.

## Print the general ledger report for Peru

To print the general ledger report for Peru, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquiries and reports** \> **LATAM** \> **General Ledger**.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. Select the posting layers that you want.
1. Select **Print**.
