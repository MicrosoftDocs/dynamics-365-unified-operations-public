---
title: Configure printing for the Printed General Ledger for Venezuela
description: Learn about the required configuration for the Printed General Ledger report for Venezuela.
author: Cpicon85
ms.date: 05/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the Printed General Ledger for Venezuela

[!INCLUDE[banner](../../../includes/banner.md)]

This article explains how to set up and generate the **Printed General Ledger** report for Venezuela. The **Printed General Ledger** report provides detailed information about all transactions that are recorded in the journal, together with the transaction date, journal number, main account, and description. The information is shown in an Excel printout format.

## Prerequisites

Before you can generate and print the report, the following prerequisites must be met:

- The legal entity's address must be in Venezuela.
- Both the country/region-specific LATAM feature for Venezuela and the general LATAM feature must be enabled.
- You must download the specific report configurations from the Microsoft Dataverse configuration repository.
- You must import the following Electronic reporting (ER) configurations:

    - Ledger accounting reports
    - Ledger Accounting LATAM
    - General Ledger LATAM

    Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- You must create a new SQL Server Reporting Services (SSRS) Reports/Services reference and configure it in the following way:

    - In the **Report/Service Id** field, enter **PrintGL**.
    - In the **Report/Service name** field, enter **PrintGLedger**.
    - In the **Report/Service type** field, select an ER configuration.
    - In the **Model mapping name** field, select **Ledger accounting LTM**.
    - In the **Data model definition** field, select **GeneralLedger**.
    - In the **Format mapping** field, select **General ledger LATAM**.
    - In the list of report/service types, enable **General Ledger**.

## Print the General Ledger report for Venezuela

To print the **General Ledger** report for Venezuela, follow these steps.

1. Go to **General ledger** \> **Inquiries and reports** \> **LATAM** \> **General Ledger**.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. Select the posting layers that you want.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
