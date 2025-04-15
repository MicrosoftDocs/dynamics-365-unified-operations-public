---
title: Printing configuration for Electronic Ledger posting report Perú
description: This topic provides information about the required configuration for printing a Ledger posting report for Perú. 
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Printing configuration for Electronic Ledger posting report Perú
This article describes how to set up and generate an **Electronic Ledger posting report** for Perú.
The electronic ledger posting report is a digital accounting record that compiles and classifies all the economic transactions of a company in a chronological and detailed manner.
## Prerequisites
Before you can print an **Electronic Ledger posting report**, the following prerequisites must be met:  

- The legal entity's address must be in country/region Perú.
- The country/region-specific LATAM feature for Perú and the general LATAM feature must be enabled.
-You must download the specific report configurations from the Dataverse configuration repository. 

* The following Electronic reporting (ER) configurations must be imported:
  * Ledger accounting reports
  * Ledger Accounting LATAM
  * Magnetic General Ledger Perú
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
* You must create a **Tax application code** to use in this report. Learn more in [Tax application for Latin America]( https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-tax-application)
* You must configure the application code associated with the transaction currency according to the fiscal regulation.
* You must configure the tax application code associated with the type of country document ID according to the fiscal regulation.
* You must configure the tax application code for the different document classes used in transactions (payment methods, invoices, credit notes, debit notes, etc.) according to the fiscal regulation. 
* You must create a new **SSRS Reports/Services reference** and configure it as follows:
  * In the Report/Service Id field, enter LedgerPosting.
  * In the Report/Service name field, enter LedgerPost.
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger accounting LTM.
  * In the Data model definition field, select MagneticGeneralLedger.
  * In the Format mapping field, select Magnetic General Ledger Perú.
  * In the list of report/service types, enable Ledger Posting report.
  * In the list of Parameters add **TaxApplicationId** to the **Name** column, and the tax application code created in the **Value** column.


## Print the Ledger Posting report for Perú

1. Go to **General Ledger > Inquiries and Reports > LATAM > Ledger Posting Report**.
2. In the Ledger posting report dialog box, configure the filters for the report.
3. In the Report ID field, select the corresponding report/service ID.
4. In the **From date** and **To date** fields, select the date range of the transactions that you want.
5. In the Account number field, select the account number if you want to print the transactions for a specific account.
6. Select the posting layers you prefer.
7. Select print.
