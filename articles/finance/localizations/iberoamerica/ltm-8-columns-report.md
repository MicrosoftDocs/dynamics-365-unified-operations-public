---
title: Printing configuration for the Chile 8 Columns report
description: The article describes how to set up and use the Chile 8 Columns report.
author: Cpicon85 
ms.date: 9/29/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Printing configuration for the Chile 8 Columns report

[!include[banner](../../includes/banner.md)]

"Chile 8 Columns Report" is a financial reporting format that's used in Chile for accounting purposes. The phrase "8 Columns" in the report's name refers to the eight columns or sections that are typically included in this format.

Before you can print the report, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- The SSRS Reports/Services references must be configured in the following way.

    | Field | Description |
    |-------|-------------|
    | Report/Service Id | Enter **8 Columns report**. |
    | Report/Service name | Enter **8 Columns report**. |
    | Report/Service type | Select **ER Configuration**. |
    | Model mapping name | Select **Ledger Accounting CHI**. |
    | Data model definition | Select **LedgerTrialBalance**. |
    | Format mapping | Select **T8 Columns Balance**. |
    | Ledger Tributary report | On the **Chile** FastTab, select this checkbox. |

Follow these steps to generate and run the report. 

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **8 Columns report**.
2. In the **8 columns report** dialog box, in the **Report ID** field, select the corresponding ID for the **8 Columns** report.
3. In the **From date** and **To date** fields, select the date range of the transactions that you want to include on the report.
4. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
