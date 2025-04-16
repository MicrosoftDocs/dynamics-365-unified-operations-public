---
title: Printing configuration for Electronic Accounting Plan for Peru
description: This topic provides information about the required configuration for printing an Electronic Accounting Plan for Peru.
author: Fhernandez0088
ms.date: 04/16/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Printing configuration for Electronic Accounting Plan for Peru
This article describes how to set up and generate an **Electronic Accounting Plan** for Peru.
The electronic chart of accounts book is a digital record that details all the accounting accounts used by a company, according to the Peruvian General Corporate Accounting Plan (PCGE). This book is used together with the printed journal for validation in SUNAT's Electronic Ledger Program (PLE). Its purpose is to ensure that accounting transactions are recorded in an accurate and orderly manner, facilitating auditing and compliance with tax and accounting regulations.

## Prerequisites
Before you can print an **Electronic Accounting Plan Peru**, the following prerequisites must be met:  

- The legal entity's address must be in country/region Peru.
- The country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
-You must download the specific report configurations from the Dataverse configuration repository. 

* The following Electronic reporting (ER) configurations must be imported:
  * Ledger accounting reports
  * Ledger Accounting LATAM
  * Electronic Accounting plan

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
* You must create a **Tax application code** to use in this report. Learn more in [Tax application for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application)
* You must configure the application code associated with the transaction currency according to the fiscal regulation.
* You must configure the tax application code associated with the type of country document ID according to the fiscal regulation.
* You must configure the tax application code for the different document classes used in transactions (payment methods, invoices, credit notes, debit notes, etc.) according to the fiscal regulation. 
* You must create a new **SSRS Reports/Services reference** and configure it as follows:
  * In the Report/Service Id field, enter AccountingPlan.
  * In the Report/Service name field, enter Account.P
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger Accounting LTM.
  * In the Data model definition field, select MagneticGeneralLedger.
  * In the Format mapping field, select Electronic Accounting plan.
  * In the list of report/service types, enable General Ledger.
  * In the list of Parameters add **TaxApplicationId** to the **Name** column, and the tax application code created in the **Value** column.

## Print the Accounting PLan report for Peru

1. Go to **General Ledger > Inquiries and Reports > LATAM > General Ledger**.
2. In the Report ID field, select the corresponding report/service ID.
3. In the **From date** and **To date** fields, select the date range of the transactions that you want.
4. Select the posting layers you prefer.
5. Select print.



