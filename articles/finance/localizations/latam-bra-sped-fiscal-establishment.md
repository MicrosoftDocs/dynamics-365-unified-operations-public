---
title: Enable the Fiscal establishment dimension
description: This article explains how to set up the Fiscal establishment dimension for the SPED-Reinf.
author: AdamTrukawka
ms.date: 08/07/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1
ms.search.form: 
---

# Enable the Fiscal establishment dimension

[!include [banner](../includes/banner.md)]
  
It's necessary to have the dimension "Fiscal establishment", for non-fiscal operations when generated General Journal to meet the events: R-4010, R-4020 and R-4040.

1. Go to **General Ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimensions** then configure it as following.  
    ![Fiscal Dimenssions.](media/bra-fiscal-dimenssions.png)

2. General Ledger \> Chart of accounts \> Dimensions \> Financial dimension sets then configure it as following.  
    ![Fiscal Establishment.](media/bra-fiscal-establishment.png)

3. General Ledger \> Chart of accounts \> Structures \> Configure account structures \> select "Brasil" \> click "Edit" button.  
    ![Preparation items parameters.](media/bra-acc-structure.png)

4. Add segment button \> Add "FiscalEstablishment" \> click "Activate" then configure it a following.  
    ![Preparation items parameters.](media/bra-add-segment.png)

5. Accounts payable \> Invoices \> Invoice journal \> click "Lines" button.  
    ![Preparation items parameters.](media/bra-inv-journal.png)

6. On the Journal Lines Pane \> List tab \> click= "New" then configure it as following.

7. Financial dimensions option \> Accounts \> then configure it as following \> click "OK" button.  
    ![Preparation items parameters.](media/bra-sel-dim.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
