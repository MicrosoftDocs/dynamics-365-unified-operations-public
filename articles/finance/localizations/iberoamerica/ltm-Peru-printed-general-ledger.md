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

The printed general ledger report provides detailed information on all transactions recorded in the journal, along with the transaction date, journal number, main account and description, and displays the information in an Excel printout format.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:  
- The legal entity's address must be in country/region Peru.
- You must enable the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository. 
- You must import the following electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
    - Ledger accounting reports
    - Ledger accounting LATAM
    - General ledger PE
* You must configure the electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
* You must create a new SSRS Reports/Services reference and configure it in the following way:
    1. In the **Report/Service ID** field, enter "PrintGL".
    1. In the **Report/Service name** field, enter "PrintGLedger".
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger accounting LTM**.
    1. In the **Data model definition** field, select **GeneralLedger**.
    1. In the **Format mapping** field, select **General ledger PE**.
    1. In the list of report/service types, enable **General Ledger**.

## Print the general ledger report for Peru

To print the general ledger report for Peru, follow these steps.

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **General Ledger**.
1. In the **Report ID field**, select the corresponding report/service ID.
1. In the **From date** and **To date fields**, select the date range of the transactions that you want to print.
1. Select the posting layers you want.
1. Select **Print**.


