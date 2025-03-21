---
title: Cancel a customer fiscal document (project) (Brazil)
description: This article describes how to cancel a customer invoice for a project or fiscal document in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
---

# Cancel a customer fiscal document (project) (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to cancel a customer invoice for a project or fiscal document in Brazil with Microsoft Dynamics 365 Finance.

You can cancel a customer invoice for a project. When you cancel a project invoice, a negative project invoice is created. When you post the negative project invoice, the original and negative project invoices are marked as canceled, and all the ledger and financial transactions are reversed. The original transaction is reported as canceled in the fiscal books, but the negative transaction isn't reported in the fiscal books. You can't cancel a project invoice that is partially or fully settled. Additionally, you can't cancel a project invoice if the posting date of the invoice is in a fiscal period that is closed. 

The following procedure uses the BRMF demo company.

To cancel a customer invoice for a project or fiscal document, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting \> Projects \> All projects**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Invoice journals**.
1. Use the Quick Filter to find records. For example, filter on the **Invoice field** with a value of "04000006".
1. Select **Invoice cancellation**.
1. Select **Yes**.
1. In the **Reason code** field, enter or select a value.
1. In the **Canceling invoice date** field, enter a date.
1. Select **Cancel project invoice**.
1. In the **Print invoice** field, select **No**.
1. Select **OK**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
