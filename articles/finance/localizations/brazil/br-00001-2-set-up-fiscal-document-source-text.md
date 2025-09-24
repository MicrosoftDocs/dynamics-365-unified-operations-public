---
title: Set up fiscal document source text (Brazil)
description: This article describes how to attach fiscal document texts to a sales order, purchase order, or free text invoice in Brazil with Microsoft Dynamics 365 Finance.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.date: 03/13/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---
# Set up fiscal document source text (Brazil)

[!include [banner](../../includes/banner.md)]

This article describes how to attach fiscal document texts to a sales order, purchase order, or free text invoice in Brazil with Microsoft Dynamics 365 Finance.

You can attach fiscal document texts to a sales order, purchase order, or free text invoice. The fiscal document texts that are attached to the sales order, purchase order, or free text invoice are printed on the fiscal document. The fiscal document texts provide additional information about the taxes and laws that are applied to the fiscal document. You can also include placeholders in the fiscal document source text. The placeholders are replaced by predefined text when you post the fiscal document that the fiscal document text is attached to. 

The following procedure uses the BRMF demo company.

To set up fiscal document source texts, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Document management \> Document types**.
1. Select **New**.
1. In the **Type** field, enter a value.
1. In the **Name** field, enter a value.
1. Select **Simple note**.
1. Select **Database**.
1. Select **Save**.
1. Close the page.
1. Go to **Organization administration \> Setup \> Brazilian parameters**.
1. Select the **Fiscal document** tab.
1. In the **Document type** field, enter or select a value.
1. Select **Save**.
1. Close the page.
1. Go to **Organization administration \> Setup \> Fiscal document source texts**.
1. Select **New**.
1. In the **Fiscal document text** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Text** field, enter a value.
1. Select **Save**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
