---
# required metadata

title: Refundable charges are not calculated based on the quantity returned
description: This topic provides troubleshooting guidance that can help when cashiers are shown incorrect refundable charges in point of sale (POS) based on the quantity of items returned.
author: gvrmohanreddy
ms.date: 03/18/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Refundable charges are not calculated based on the quantity returned

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when cashiers are shown incorrect refundable charges in point of sale (POS) based on the quantity of items returned.

## Description

A customer returns a partial quantity of items that were purchased for a sales order that has line-level refundable charges, but instead of a partial refund all charges are shown as refundable in POS.

For example, a customer purchases a quantity of 5 items at $5 per item for total charges of $25 and returns 3 of out the 5 items. The cashier is then shown a $25 refundable charge in POS instead of the expected $15 based on the 3 quantity returned.

## Resolution

### Turn on the Enable refunding charges based on the refunded quantity feature

Starting with Commerce version 10.0.26, turning on the **Enable refunding charges based on the refunded quantity** feature allows the calculation of line-level refundable charges that are based on the quantity of items returned.

To enable the **Enable refunding charges based on the refunded quantity** feature in Commerce headquarters, follow these steps.

1. Go to the **Feature management** workspace at **System administrator \> Workspaces\> Feature management**.
1. In the list of available features, search for and select the **Enable refunding charges based on the refunded quantity** feature. 
1. In the right pane, select **Enable now**. 


