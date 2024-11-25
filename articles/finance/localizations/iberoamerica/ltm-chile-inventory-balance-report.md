---
title: Print the Inventory and balance report for Chile
description: Learn how to set up and print the Inventory and balance report for Chile, including an outline on prerequisites and a table that defines various fields.
author: Cpicon85
ms.author: kfend
ms.topic: article
ms.date: 10/09/2023 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Print the Inventory and balance report for Chile

[!include [banner](../../includes/banner.md)]

The article describes how to set up and print the **Inventory and balance** report for Chile.

Before you can print the **Inventory and balance** report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- The SSRS Reports/Services references must be configured in the following way.

    | Field | Description |
    | ------| ----------- |
    | Report/Service Id | Enter **IB report**. |
    | Report/Service name | Enter **InventBal report**. |
    | Report/Service type | Select **ER Configuration**. |
    | Model mapping name | Select **Ledger Accounting CHI**. |
    | Data model definition | Select **InventoryBalance**. |
    | Format mapping | Select **Inventory Balance CL**. |
    | Inventory balance Chile | On the **Chile** FastTab, select this checkbox. |

Follow these steps to print the report.

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **General ledger**.
2. In the **General ledger** dialog box, in the **Report ID** field, select the ID that corresponds to the **Inventory balance** report.
3. In the **From date** and **To date** fields, select the date range of transactions that you want to print.
4. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
