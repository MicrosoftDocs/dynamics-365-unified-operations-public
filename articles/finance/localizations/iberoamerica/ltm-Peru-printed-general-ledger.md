---
title: Configuration for Printed General Ledger for Peru
description: This topic provides information about the required configuration for the Printed General Ledger for Peru.
author: Fhernandez0088
ms.date: 04/16/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configuration for Printed General Ledger for Peru
This article describes how to set up and generate a ** Printed General Ledger report** for Peru.
This report provides detailed information on all transactions recorded in the journal, along with the transaction date, journal number, main account and description, and displays the information in an Excel printout format.

## Prerequisites
Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:  
- The legal entity's address must be in country/region Peru.
- The country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
-You must download the specific report configurations from the Dataverse configuration repository. 
* The following Electronic reporting (ER) configurations must be imported:
  * Ledger accounting reports
  * Ledger Accounting LATAM
  * General Ledger PE

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
* You must create a new SSRS Reports/Services reference and configure it in the following way:
  * In the Report/Service Id field, enter PrintGL.
  * In the Report/Service name field, enter PrintGLedger.
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger accounting LTM.
  * In the Data model definition field, select GeneralLedger.
  * In the Format mapping field, select General ledger PE.
  * In the list of report/service types, enable General Ledger.

## Print the General Ledger report for Peru
1. Go to **General Ledger > Inquiries and Reports > LATAM > General Ledger**.
2. In the **Report ID field**, select the corresponding report/service ID.
3. In the **From date** and **To date fields**, select the date range of the transactions that you want to print.
4.Select the posting layers you prefer.
5. Select print.


