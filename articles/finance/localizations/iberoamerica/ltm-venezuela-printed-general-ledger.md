---
title: Configure printing for the Printed General Ledger for Venezuela
description: Learn about the required configuration for the Printed General Ledger for Venezuela.
author: Cpicon85
ms.date: 05/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon
---

# Configure printing for the Printed General Ledger for Venezuela


[!INCLUDE[banner](../../../includes/banner.md)]

This article describes how to set up and generate **Printed General Ledger report** for Venezuela. The **Printed General Ledger report** report provides detailed information on all transactions recorded in the journal, along with the transaction date, journal number, main account and description, and displays the information in an Excel printout format.

## Prerequisites

Before you complete the steps in this article to generate and print the report, the following prerequisites must be met:  

- The legal entity's address must be in country/region Venezuela.
- The country/region-specific LATAM feature for Venezuela and the general LATAM feature must be enabled.
- You must download the specific report configurations from the Dataverse configuration repository. 
* The following Electronic reporting (ER) configurations must be imported:
  * Ledger accounting reports
  * Ledger Accounting LATAM
  * General Ledger LATAM 

Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

* You must create a new SSRS Reports/Services reference and configure it in the following way:
  * In the Report/Service Id field, enter PrintGL.
  * In the Report/Service name field, enter PrintGLedger.
  * In the Report/Service type field, select an ER configuration.
  * In the Model mapping name field, select Ledger accounting LTM.
  * In the Data model definition field, select GeneralLedger.
  * In the Format mapping field, select General ledger LATAM.
  * In the list of report/service types, enable General Ledger.

## Print the General Ledger report for Venezuela

To print the General Ledger report for Venezuela, follow these steps.

1. Go to **General Ledger > Inquiries and Reports > LATAM > General Ledger**.
1. In the **Report ID field**, select the corresponding report/service ID.
1. In the **From date** and **To date fields**, select the date range of the transactions that you want to print.
1. Select the posting layers you prefer.
1. Select print.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
