---
title: Set up and generate an electronic ledger posting report for Peru
description: Learn how to set up and generate an electronic ledger posting report for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate an electronic ledger posting report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate an electronic ledger posting report for Peru in Microsoft Dynamics 365 Finance.

The electronic ledger posting report is a digital accounting record that compiles and classifies all the economic transactions of a company in a chronological and detailed manner.

## Prerequisites

Before you can print an electronic ledger posting report, you must complete the following prerequisites:

- The country/region of the legal entity's address must be in Peru.
- You must enable both the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository.
- The following Dataverse configurations must be imported:

| Element |                    Format name                    |
|:-------:|:-------------------------------------------------:|
| Model   | :::no-loc text="Ledger accounting reports":::                      |
| Mapping | :::no-loc text="(General Ledger LATAM) Ledger Accounting LATAM"::: |
| Format  | :::no-loc text="Magnetic Ledger Posting Peru":::                   |

- You must configure the ER parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a tax application code to use in this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure the application code that is associated with the transaction currency according to the fiscal regulation.
- You must configure the tax application code that is associated with the type of country document ID according to the fiscal regulation.
- You must configure the tax application code for the different document classes that are used in transactions (for example, payment methods, invoices, credit notes, and debit notes) according to the fiscal regulation.
- You must create a new SQL Server Reporting Services (SSRS) Reports/Services reference and configure it in the following way:

    1. In the **Report/Service ID** field, enter **LedgerPosting**.
    1. In the **Report/Service name** field, enter **LedgerPost**.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger accounting LTM**.
    1. In the **Data model definition** field, select **MagneticGeneralLedger**.
    1. In the **Format mapping** field, select **Magnetic Ledger Posting Peru**.
    1. In the list of report/service types, enable **Ledger Posting report**.
    1. In the list of parameters, in the **Name** column, add **TaxApplicationId**. Then, in the **Value** column, add the tax application code that you created.

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
