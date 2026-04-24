--- 
title: Configure credit card processing
description: Learn how to view the list of payment providers and how to configure a payment account for accounts receivable in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 02/06/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Configure credit card processing

[!include [banner](../includes/banner.md)]

This article describes how to view the list of payment providers and how to configure a payment account for accounts receivable in Microsoft Dynamics 365 Commerce.

The following procedures explain how to view the list of payment providers and how to configure a payment account for accounts receivable. The procedure uses the USRT company in demo data and is intended for administrators and IT professionals.

To configure a payment account, follow these steps:

1. In Commerce headquarters, go to **Accounts receivable** > **Payments setup** > **Payment services**.
1. Select **View available providers**.
1. Select **New**.
1. In the **Payment service** field, enter a value.
1. In the **Payment connector** field, select an option.
1. Expand the **Payment service account** section.
1. In the **Environment:** field, enter `PROD`.
1. Select **Credit card types**.
1. In the **Payment journal** field, select the drop-down button to open the lookup.
1. In the list, select the link in the chosen row.
1. Select **Add**.
1. In the **Currency** field, enter a value.
1. In the list, find and select the desired record.
1. In the **Payment journal** field, select the drop-down button to open the lookup.
1. In the list, select the link in the chosen row.
1. Select **Add**.
1. In the **Currency** field, enter a value.
1. In the list, find and select the desired record. Repeat the following steps for as many card types as you need.  
1. In the **Payment journal** field, select the drop-down button to open the lookup.
1. In the list, select the link in the chosen row.
1. Select **Add**.
1. In the **Currency** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Select **Validate**.
1. Select the **Default processor for new credit cards** checkbox.
1. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
