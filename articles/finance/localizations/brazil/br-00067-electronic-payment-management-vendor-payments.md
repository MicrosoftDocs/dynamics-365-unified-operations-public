---
title: Electronic payment management for vendor payments (Brazil)
description: This article describes how to make electronic payments by transferring files between a legal entity and a bank in Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Electronic payment management for vendor payments (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to make electronic payments by transferring files between a legal entity and a bank in Brazil with Microsoft Dynamics 365 Finance.

You can make electronic payments by transferring files between a legal entity and a bank. You can generate and send an electronic remittance file to a bank. In this case, the export file contains information about invoices that must be received or paid, requests for return invoices, or changes to customer or vendor addresses. Alternatively, you can import a return file from a bank. In this case, the return file contains either information about the acceptance of an invoice together with the payment number that is provided by the bank, or information about the payments that are received from a customer or paid to a vendor. 

The following procedure uses the BRMF demo company.

To make electronic payments by transferring files between a legal entity and a bank, follow these steps:

1. In Dynamics 365 Finance, go to **Purchase ledger \> Payments \> Payment transfers**.
1. In the list, mark the selected row.
1. Select **Return file - vendor**.
1. In the **Method of payment** field, enter or select a value.
1. Select **OK**.
1. Select **OK**. The status of the payments is updated in the **Payments status** field on the **Payment transfers** page. The new status is based on the status of the payment in the return file.  
1. Select **Post**.
1. In the **New journal name** field, enter a value.
1. Select **OK**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
