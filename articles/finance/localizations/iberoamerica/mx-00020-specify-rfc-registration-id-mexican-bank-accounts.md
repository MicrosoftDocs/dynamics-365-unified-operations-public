---
title: MX-00020 - Specify the RFC registration ID for Mexican bank accounts
description: Learn about creating the Bank account for Mexico and assigning the RFC tax registration ID, including a step-by-step process.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - BankAccountTable
  - DefaultDashboard
ms.dyn365.ops.version: Version 7.0.0
---

# MX-00020 - Specify the RFC registration ID for Mexican bank accounts

[!include [banner](../../includes/banner.md)]

This task shows you how to create the bank account for Mexico and assign the RFC tax registration ID. This task uses the MXMF demo company data.

1. Go to **Cash and bank management** > **Bank accounts**.
1. Select **New**.
1. In the **Bank account** field, enter a value.
1. In the **Routing number** field, enter the routing number.
    * Use this field to identify the Mexican bank code for electronic ledger accounting statements. You can find the list of bank codes on the [government site](https://www.gob.mx/).  
1. In the **Bank account number** field, enter a value.
1. Select a main account.
1. Expand or collapse the **Additional identification** section.
1. In the **RFC number** field, enter the 12-character RFC number of the bank.
    * The Federal Registration for Taxpayers (RFC) number is the tax identification number that tax authorities assign to a person or a corporation. The system validates tax registration IDs according to the format specified by tax authorities in Mexico.  
1. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
