---
title: POS inventory lookup with channel-side calculation
description: This article describes how the POS inventory lookup operation works with channel-side inventory calculation in Microsoft Dynamics 365 Commerce.
author: hhainesms
ms.date: 07/18/2023
ms.topic: articlex
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: hhaines
ms.search.validFrom: 2020-02-11

---
# POS inventory lookup with channel-side calculation

[!include [banner](../includes/banner.md)]

This article describes how the point of sale (POS) inventory lookup operation works with channel-side inventory calculation in Microsoft Dynamics 365 Commerce.

In Commerce version 10.0.9 and earlier, the inventory lookup operation in POS used a real-time service call to Commerce headquarters to get inventory information for a selected product, for both the user's current store and any other stores that are configured for the fulfillment group as part of the channel configuration for the store.

In Commerce version 10.0.10 and later, you can turn off real-time service calls to Commerce headquarters. Instead, you can use channel-side calculation on the Commerce server to determine the on-hand inventory that's physically available for the store and any other locations that are defined in the fulfillment group. This channel-calculated inventory configuration is also useful for locations where internet connectivity is unreliable, because you don't have to be online to get inventory lookups from Commerce headquarters.

When channel-side calculation is correctly configured and managed, it can provide a more reliable estimate of current store inventory, because it uses transactional data that's in the Commerce channel database but that Commerce headquarters might not yet have information about. For example, if you use the existing real-time service call for inventory lookups in POS, Commerce headquarters probably won't yet have information about a cash-and-carry sale that just occurred for a product. Therefore, the on-hand inventory value that Commerce headquarters returns for that product will probably exceed the store's actual on-hand inventory by one unit. However, if you use channel-side calculation, the cash-and-carry sale can be factored into the calculation and deducted from the on-hand value that's shown. Although the values that both the channel-side calculation and the real-time service call provide are only estimates of on-hand inventory, the value that the channel-side calculation provides is much more likely to be accurate for the current store.

## Configure POS inventory lookup to use channel-side calculation

> [!NOTE]
> To configure the POS inventory lookup operation in Commerce headquarters to use the channel-side calculation logic, and to turn off real-time service calls, you must first [configure channel-side calculation](channel-side-calculation.md).

To configure POS inventory lookup to use channel-side calculation, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile.
1. On the **Functions** FastTab, in the **Inventory availability calculation** section, change the value of the **Inventory availability calculation mode** field from **Real time service** to **Channel**. By default, all functionality profiles use real-time service calls. You must change the value of this field if you want to use channel-side calculation logic. Every retail store that's linked to the selected functionality profile will be affected by this change.

You must then sync the changes to the channels through the distribution schedule process in Commerce headquarters by following these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Run the **1070** (**Channel configuration**) job.

After the configuration is completed, the information that's provided about physically available inventory no longer uses a real-time service call when a user in the POS application uses the inventory lookup operation (standard and matrix views). Instead, data about physically available inventory for the current store and all the stores in the fulfillment group is calculated based on the last-known snapshot that was delivered to the channel database from Commerce headquarters. The snapshot value is further refined by the channel-side calculation to adjust the physically available value, based on additional sales or return transactions that exist for the selected product in the channel database but that weren't included in the last synced snapshot from the 1130 job.

> [!NOTE]
> The physically reserved value remains the same as the snapshot value, and won't be refined by the channel-side calculation.

If the channel database doesn't contain transactional data for any of the warehouses or stores in the fulfillment group, it contains no additional transactions that can be factored into a recalculation of the value. Therefore, the best estimate of on-hand inventory that can be shown for those warehouses or stores is the data from the last-known Commerce headquarters snapshot.

The **Order fulfillment** pages of POS also use channel-side calculation to show on-hand inventory for items when an order fulfillment line is selected and a user views the **Details** pane for on-hand inventory for the selected item.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
