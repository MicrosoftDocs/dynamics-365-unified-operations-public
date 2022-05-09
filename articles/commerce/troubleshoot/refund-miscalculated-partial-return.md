---
# required metadata

title: Refundable charges are miscalculated based on the quantity returned
description: This topic provides troubleshooting guidance that can help when cashiers see incorrect refundable charges in point of sale (POS) for the quantity of items that is returned.
author: gvrmohanreddy
ms.date: 03/24/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Refundable charges are miscalculated based on the quantity returned

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when cashiers see incorrect refundable charges in point of sale (POS) for the quantity of items that is returned.

## Description

A customer returns a partial quantity of the items that were purchased for a sales order that has line-level refundable charges. However, instead of showing a partial refund, POS shows all charges as refundable.

For example, a customer purchases a quantity of five items at $5 per item, for total charges of $25. The customer then returns three of the five items. However, the cashier is shown a $25 refundable charge in POS, instead of the expected $15 refundable charge for the three items that were returned.

## Resolution

### Turn on the Enable refunding charges based on the refunded quantity feature

As of Microsoft Dynamics 365 Commerce version 10.0.26, the **Enable refunding charges based on the refunded quantity** feature enables line-level refundable charges to be calculated based on the quantity of items that is returned.

To enable the **Enable refunding charges based on the refunded quantity** feature in Commerce headquarters, follow these steps.

1. Open the **Feature management** workspace (**System administrator \> Workspaces\> Feature management**).
1. In the list of available features, search for and select the **Enable refunding charges based on the refunded quantity** feature.
1. In the right pane, select **Enable now**.
