---
title: Audit file (XML Auditfile Financieel, XAF)
description: Learn how to set up and generate the Audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/05/2025
ms.reviewer: johnmichalak
ms.search.region: Netherlands
ms.search.validFrom: 2016-06-30
ms.search.form: TaxEvatParameters_NL
---

# Audit file (XML Auditfile Financieel, XAF)

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the Audit file for legal entities in the Netherlands in Microsoft Dynamics 365 Finance.

This functionality is available for legal entities whose primary address is in the Netherlands.

## Import and set up electronic reporting configurations

To prepare Microsoft Dynamics 365 Finance to generate the Audit file, you must first import the following electronic reporting (ER) configurations.

| Number | ER configuration name         | Type                                 | Description |
|--------|-------------------------------|--------------------------------------|-------------|
| 1      | Audit file model              | Model                                | A model for the Audit file for Netherlands. |
| 2      | Audit file (NL)               | Format (exporting)                   | ER format for XML Auditfile Financieel, XAF. |

## Generate the Audit file

To generate the Audit file, follow these steps:

1. In Dynamics 365 Finance, go to **General ledger** \> **Periodic tasks** \> **Audit file**.
1. In the **From date** field, enter a date. 
1. In the **To date** field, enter a date. 
1. In the **Format mapping** field, enter "Audit file (NL)".
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
