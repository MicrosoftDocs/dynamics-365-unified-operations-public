---
title: POS inventory lookup with channel-side calculation
description: Learn how the POS inventory lookup operation works with channel-side inventory calculation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-02-11
ms.custom: 
  - bap-template
---
# POS inventory lookup with channel-side calculation

[!include [banner](../includes/banner.md)]

This article explains how the point of sale (POS) inventory lookup operation works with channel-side inventory calculation in Microsoft Dynamics 365 Commerce.

In Commerce version 10.0.9 and earlier, the inventory lookup operation in POS used a real-time service call to Commerce headquarters to get inventory information for a selected product. This inventory information was for both the user's current store and any other stores that the channel configuration specified as part of the fulfillment group.

In Commerce version 10.0.10 and later, you can turn off real-time service calls to Commerce headquarters. Instead, use channel-side calculation on the Commerce server to determine the on-hand inventory that's physically available for the store and any other locations that the fulfillment group defines. This channel-calculated inventory configuration is also useful for locations where internet connectivity is unreliable, because you don't need to be online to get inventory lookups from Commerce headquarters.

When you correctly configure and manage channel-side calculation, it provides a more reliable estimate of current store inventory. It uses transactional data that's in the Commerce channel database but that Commerce headquarters might not yet have information about. For example, if you use the existing real-time service call for inventory lookups in POS, Commerce headquarters probably doesn't yet have information about a cash-and-carry sale that just occurred for a product. Therefore, the on-hand inventory value that Commerce headquarters returns for that product probably exceeds the store's actual on-hand inventory by one unit. However, if you use channel-side calculation, the cash-and-carry sale factors into the calculation and deducts from the on-hand value shown. Although the values that both the channel-side calculation and the real-time service call provide are only estimates of on-hand inventory, the value that the channel-side calculation provides is much more likely to be accurate for the current store.

## Configure POS inventory lookup to use channel-side calculation

> [!NOTE]
> To configure the POS inventory lookup operation in Commerce headquarters to use the channel-side calculation logic, and to turn off real-time service calls, first [configure channel-side calculation](channel-side-calculation.md).

To configure POS inventory lookup to use channel-side calculation, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile.
1. On the **Functions** FastTab, in the **Inventory availability calculation** section, change the value of the **Inventory availability calculation mode** field from **Real time service** to **Channel**. By default, all functionality profiles use real-time service calls. Change the value of this field if you want to use channel-side calculation logic. Every retail store linked to the selected functionality profile is affected by this change.

Sync the changes to the channels through the distribution schedule process in Commerce headquarters by following these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1070** (**Channel configuration**) job.

After you complete the configuration, the information about physically available inventory no longer uses a real-time service call when a user in the POS application uses the inventory lookup operation (standard and matrix views). Instead, data about physically available inventory for the current store and all the stores in the fulfillment group is calculated based on the last-known snapshot that was delivered to the channel database from Commerce headquarters. The snapshot value is further refined by the channel-side calculation to adjust the physically available value, based on additional sales or return transactions that exist for the selected product in the channel database but that weren't included in the last synced snapshot from the 1130 job.

> [!NOTE]
> The physically reserved value remains the same as the snapshot value, and isn't refined by the channel-side calculation.

If the channel database doesn't contain transactional data for any of the warehouses or stores in the fulfillment group, it contains no additional transactions that can be factored into a recalculation of the value. Therefore, the best estimate of on-hand inventory that you can show for those warehouses or stores is the data from the last-known Commerce headquarters snapshot.

The **Order fulfillment** pages of POS also use channel-side calculation to show on-hand inventory for items when an order fulfillment line is selected and a user views the **Details** pane for on-hand inventory for the selected item.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
