---
title: Set up and generate an electronic accounting plan for Peru
description: Learn how to set up and generate an electronic accounting plan for Peru in Microsoft Dynamics 365 Finance.
author: Fhernandez0088
ms.date: 04/17/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up and generate an electronic accounting plan for Peru

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate an electronic accounting plan for Peru in Microsoft Dynamics 365 Finance.

The electronic chart of accounts book is a digital record that details all the accounting accounts that a company uses, according to the Peruvian General Corporate Accounting Plan (PCGE). This book is used together with the printed journal for validation in the National Superintendency of Customs and Tax Administration (SUNAT) Electronic Ledger Program (PLE). Its purpose is to facilitate auditing and compliance with tax and accounting regulations by ensuring that accounting transactions are recorded in an accurate and orderly manner.

## Prerequisites

Before you can print an electronic accounting plan for Peru, the following prerequisites must be met:  

- The country/region of the legal entity's address must be in Peru.
- You must enable both the country/region-specific LATAM feature for Peru and the general LATAM feature.
- You must download the specific report configurations from the Dataverse configuration repository.
- You must import the following Electronic reporting (ER) configurations. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

    - Ledger accounting LATAM
    - Electronic accounting plan

- You must configure the ER parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must create a *tax application code* to use on this report. Learn more in [Tax application for Latin America](ltm-core-tax-application.md).
- You must configure the application code that is associated with the transaction currency according to the fiscal regulation.
- You must configure the tax application code that is associated with the type of country document ID according to the fiscal regulation.
- You must configure the tax application code for the different document classes that are used in transactions (for example, payment methods, invoices, credit notes, and debit notes) according to the fiscal regulation.
- You must create a new SQL Server Reporting Services (SSRS) Reports/Services reference and configure it in the following way:

    1. In the **Report/Service ID** field, enter **AccountingPlan**.
    1. In the **Report/Service name** field, enter **Account.P**.
    1. In the **Report/Service type** field, select an ER configuration.
    1. In the **Model mapping name** field, select **Ledger Accounting LTM**.
    1. In the **Data model definition** field, select **MagneticGeneralLedger**.
    1. In the **Format mapping** field, select **Electronic Accounting plan**.
    1. In the list of report/service types, enable **General Ledger**.
    1. In the list of parameters, in the **Name** column, enter **TaxApplicationId**. Then, in the **Value** column, enter the tax application code.

## Print the accounting plan report for Peru

To print the accounting plan report for Peru, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Inquiries and reports** \> **LATAM** \> **General ledger**.
1. In the **Report ID** field, select the corresponding report/service ID.
1. In the **From date** and **To date** fields, enter the date range of the transactions that you want.
1. Select the posting layers that you want.
1. Select **Print**.
