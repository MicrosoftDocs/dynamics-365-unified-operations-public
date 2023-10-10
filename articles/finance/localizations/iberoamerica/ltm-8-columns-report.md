---
title: Chile 8 columns report printing configuration
description: The article describes how to set up and use 8 columns report
author: Cpicon85 
ms.date: 29/09/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Printing Configuration for Chile 8 Columns report

[!include[banner](../../includes/banner.md)]

The "Chile 8-Column Report" is a financial reporting format used in Chile for accounting purposes. 
The "8 columns" in the report's name refer to the eight columns or sections typically included in this format.


To print the report, it is necessary to meet the following prerequisites:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- The SSRS Reports/Services references must be configured in the following way.
  
  | Field  | Description |
  |--------|---------------|
  | Report/Service Id | 8 Columns report |
  | Report/Service name | 8 Columns report |
  | Report/Service type | select ER Configuration |
  | Model mapping name | Ledger Accounting CHI |
  | Data model definition | LedgerTrialBalance |
  | Format mapping | T8 Columns Balance |
  | Ledger Tributary report | On the **Chile** FastTab, select this checkbox. |


Complete the following steps to generate and run the report. 

1. Go to **General Ledger** > **Inquiries and Reports** > **LATAM** > **8 Columns report**.
2. In the **8 columns report** slider, in the **Report ID** field, select the corresponding ID for the **8 Columns** report.
3. In the **From date** and **To date** fields, select the date range of the transactions you want to include in the report.
4. Select **Print**.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
