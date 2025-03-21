---
title: Set up interest and fines on customer payments (Brazil)
description: This article describes how to set up interest and fines on customer payments in Brazil with Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
---

# Set up interest and fines on customer payments (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to set up interest and fines on customer payments in Brazil with Microsoft Dynamics 365 Finance.

The following procedure uses the BRMF demo company.

To set up interest and fines on customer payments, follow these steps. 

1. In Dynamics 365 Finance, go to **Accounts receivable \> Setup \> Customer posting profiles**.
1. In the **Posting profile** field, select the link.
1. Select **Edit**.
1. In the **Financial interest** field, enter a value.
1. In the **Fine** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Go to **Accounts receivable \> Payments setup \> Payment calendar**.
1. Use the Quick Filter to find records. For example, filter on the **Payment calendar** field with a value of "Brazil".
1. Select **State/province holidays**.
1. Use the Quick Filter to find records. For example, filter on the **State/province** field with a value of "SP".
1. Select **New**.
1. In the **Date** field, enter a date.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Select **City holiday**s.
1. Use the Quick Filter to find records. For example, filter on the **City** field with a value of "São Paulo".
1. Select **Add**.
1. In the **Date** field, enter a date.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Go to **Accounts receivable \> Payments setup \> Fine codes**.
1. Select **New**.
1. In the **Fine code** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Fine %** field, enter a number.
1. Select **Save**.
1. Close the page.
1. Go to **Accounts receivable \> Payments setup \> Interest codes**.
1. Select **New**.
1. In the **Interest code** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Interest %** field, enter a number.
1. In the **Interest calculation per** field, enter a number.
1. Select **Save**.
1. Close the page.
1. Go to **Accounts receivable \> Customers \> All customers**.
1. In the list, select the link in the selected row.
1. Expand the **Payment defaults** section.
1. Select **Edit**.
1. In the **Fine code** field, enter or select a value.
1. In the **Interest code** field, enter or select a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
