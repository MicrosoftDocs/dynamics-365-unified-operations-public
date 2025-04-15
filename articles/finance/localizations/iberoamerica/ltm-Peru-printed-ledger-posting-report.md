---
title: Printing configuration for Printed ledger posting report for Peru
description: This topic provides information about the required configuration for the Printed ledger journal report for Peru.
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Printing configuration for Printed ledger posting report for Peru
This article describes how to set up and generate a **Printed Ledger posting report** for Peru.
This report provides balance information for all ledger accounts, along with the transaction date, voucher and journal description, and displays the information in a printing format.

## Prerequisites
Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:  
- The legal entity's address must be in country/region Peru.
- The country/region-specific LATAM feature for Peru and the general LATAM feature must be enabled.
-You must download the specific report configurations from the Dataverse configuration repository. 
* The following Electronic reporting (ER) configurations must be imported:
  * Ledger accounting reports
  * Ledger Accounting LATAM
  * Libro Mayor PE
Learn more in [Import Electronic reporting (ER) configurations from Dataverse](https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
* You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
* You must create a new SSRS Reports/Services reference and configure it in the following way:
  * In the Report/Service Id field, enter PrintLPost.
  * In the Report/Service name field, enter PrintLPost .
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger accounting LTM.
  * In the Data model definition field, select LedgerPosting.
  * In the Format mapping field, select Libro Mayor PE.
  * In the list of report/service types, enable Ledger Posting report.

## Print the Ledger Posting report for Peru
1. Go to **General Ledger > Inquiries and Reports > LATAM > Ledger Posting Report**.
2. In the **Ledger posting report** dialog box, configure the filters for the report.
3. In the **Report ID field**, select the corresponding report/service ID.
4. In the **From date** and **To date fields**, select the date range of the transactions that you want to print.
5. In the **Account number** field, select the account number if you want to print the transactions for a specific account.
6. Select the posting layers you prefer.
7. Select print.
