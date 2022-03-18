---
# required metadata

title: Refundable charges are not calculated based on the quantity returned
description: This topic provides troubleshooting guidance that can help when customers do not see the refundable charges based on the quantity returned in Microsoft Dynamics 365 Commerce point of sale (POS).
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

This topic provides troubleshooting guidance that can help when customers do not see the refundable charges based on the quantity returned in Microsoft Dynamics 365 Commerce point of sale (POS).

## Description

A customer returns a partial quantity of items purchased for a sales order that has line-level refundable charges, but instead of a partial refund all charges are shown as refundable.

For example, a customer purchases a quantity of 5 items at $5 per item for total charges of $25, returns 3 of out the 5 items, and the cashier sees a $25 refundable charge instead of the expected $15 based on the 3 quantity returned.

## Resolution

### Enable refunding charges based on the refunded quantity

Starting with Commerce version 10.0.26, enabling the **Enable refunding charges based on the refunded quantity** feature allows the calculation of line-level refundable charges based on the quantity returned.

change is made to calculate the line-level refundable charges based on the quantity returned.  

To enable the **Enable refunding charges based on the refunded quantity** feature in Commerce headquarters, follow these steps.

1. Go to the **Feature management** workspace at **System administrator \> Workspaces\> Feature management**.
1. In the list of available features, search for and select the **Enable refunding charges based on the refunded quantity** feature. 
1. In the right pane select **Enable now**. 


