---
title: Enable lookup based Product Search using External Item Identifier
description: Learn how to search a Product using External Item Identifier. This feature will help find items using External item numbers tied to a product under a customer account set-up.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableDetails, SalesLine
ms.topic: how-to
ms.date: 07/18/2025
ms.custom: 
  - bap-template
---

# Enable lookup based Product Search using External Item Identifier

[!include [banner](../../includes/banner.md)]

This feature currently supports lookup based search using External Item Identifier on a Sales order line when you try to add an item. The functionality is visible behind a feature named **SalesExternalItemLookupSearchFeature** with label visible in the UI as "**Enable lookup based search for Sales External Item Identifier field**".

1. Enable the feature **Enable lookup based search for Sales External Item Identifier field** via Feature Management workspace.
1. Go to **Account Receivable** \> **All customers**.
1. Click on any one customer say US-001 in this case where you would like to do the set up for External Item Identifiers.
1. Click **Setup** from the top pane and click **External item description** from the dropdown.
1. You will be able to add a product and its corresponding External item details such as External item number, External item text and Description etc.
1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Either [create a new sales order](tasks/create-sales-orders.md) or open an existing sales order that you want to add lines to.
1. Click on **Add line** to add SO line and add the additional available column on the line named "External" via Insert Column option. 
1. You will be able to see a lookup denoting the presence of lookup based search support.
1. The lookup brings up the list of products for the respective Customer account on the SO line.
1. The feature supports *Search as you type in* on the basis of keywords matching either the **External item number** or **Description**.
1. Once you select a value, respective values under Item number and other related fields such as Product name gets populated too.

    The selected External item number and its respective Item number hence gets entered in the current sales line.
