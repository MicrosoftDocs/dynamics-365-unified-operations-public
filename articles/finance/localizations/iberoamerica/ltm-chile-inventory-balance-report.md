---
title: Print the Inventory and balance report for Chile
description: The article describes how to set up and print the Inventory and balance report for Chile.
author: Cpicon85 
ms.date: 10/06/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: Cpicon85 
ms.custom: bap-template
---

# Printing Configuration for Chile Inventory and balance report

[!include [banner](../includes/banner.md)]

The article describes how to set up and print the Inventory and balance report for Chile.

Before you can print the Inventory and balance report, the following prerequisites must be met.

- The legal entity must have an address in a country that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- The SSRS Reports/Services references must be configured in the following way:

  | Field  | Description |
  | -------| ----------- |
  | Report/Service Id | IB report|
  | Report/Service name| InventBal report|
  | Report/Service type| select ER Configuration|
  | Model mapping name| Ledger Accounting CHI|
  | Data model definition | InventoryBalance|
  | Format mapping | Inventory Balance CL|
  | Inventory balance Chile | On the **Chile** FastTab, select this check box.  |

Complete the following steps to print the report.
1. Go to **General Ledger** > **Inquiries and Reports** > **LATAM** > **General ledger**.
2. On the **General ledger** slider, in the **Report ID** field, select the corresponding ID for the Inventory balance report.
3. In the **From date** and **To date** fields, select the date range of transactions that you want to print.
4. Select **Print**.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
