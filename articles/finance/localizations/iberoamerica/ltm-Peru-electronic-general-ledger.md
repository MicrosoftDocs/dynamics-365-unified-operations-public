---
title: Set up and generate an electronic general ledger report for Peru
description: Learn how to set up and generate an electronic general ledger report for Peru with Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate an electronic general ledger report for Peru

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate an electronic general ledger report for Peru with Microsoft Dynamics 365 Finance.

The electronic journal is a digital version of the traditional journal, where all the accounting transactions of a company are recorded in chronological order. It includes details such as the date, the type of transaction, the ledger accounts affected, and the amounts involved.

## Prerequisites

Before you can print an electronic general ledger report for Peru, the following prerequisites must be met:  

- The legal entity's address must be in country/region Peru.
- The country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
- You must download the specific report configurations from the Dataverse configuration repository. 
- You must import the following electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse).
    - Ledger accounting reports
    - Ledger accounting LATAM
    - Electronic general ledger Peru
- You must configure the electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a **Tax application code** to use in this report. Learn more in [Tax application for Latin America]( /dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application).
- You must configure the application code associated with the transaction currency according to the fiscal regulation.
- You must configure the tax application code associated with the type of country document ID according to the fiscal regulation.
- You must configure the tax application code for the different document classes used in transactions (for example, payment methods, invoices, credit notes, and debit notes) according to the fiscal regulation. 
- You must create a new SSRS Reports/Services reference and configure it as follows:
    1. In the **Report/Service ID** field, enter GeneralLedger.
    1. In the **Report/Service name** field, enter GeneralLedg.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select Ledger Accounting LTM.
    1. In the **Data model definition** field, select MagneticGeneralLedger.
    1. In the **Format mapping** field, select Electronic General Ledger Peru.
    1. In the list of report/service types, enable **General Ledger**.
    1. In the list of parameters, in the **Name** column, add "TaxApplicationId".
    1. In the list of parameters, in the **Value** column, add the tax application code.

## Print the ledger posting report for Peru

To print the ledger posting report for Peru, follow these steps.

1. In Dynamics 365 Finance, go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **General Ledger**.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want.
1. Select the posting layers you prefer.
1. Select print.


