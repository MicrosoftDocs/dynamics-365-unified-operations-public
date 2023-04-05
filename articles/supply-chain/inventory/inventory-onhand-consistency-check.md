---
title: Running on-hand consistency checks while Inventory Visibility is enabled
description: This article describes the steps you should take before running an on-hand consistency check while the Inventory Visibility integration batch job is enabled.
author: yuhuiyou
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yuhuiyou
ms.search.validFrom: 2022-01-17
ms.dyn365.ops.version: 10.0.21
---

# Running on-hand consistency checks while Inventory Visibility is enabled

[!include [banner](../includes/banner.md)]

Dynamics 365 Supply Chain Management provides an on-hand consistency check tool that allows you to recalculate inventory on-hand list data based on inventory transactions on selected items or all items. The tool analyzes the inventory transactions (`InventTrans`) table and then reconstructs the `InventSum` and `WHSInventReserve` tables.

If you run an on-hand consistency check on *all items* while the *Inventory Visibility integration* batch job is enabled, the following conditions apply:

- The tool will usually take longer to complete than it would when the *Inventory Visibility integration* batch job isn't enabled.
- The tool uses API calls to sync the changes in the `InventSum` and `WHSInventReserve` tables to Inventory Visibility service. Therefore, if the *Inventory Visibility integration* batch job is enabled, the consistency check may fail if the external calls result in unexpected errors.  

For these reasons, we recommend that you disable the *Inventory Visibility integration* batch job before you run a on-hand consistency check on all items.

## Prepare for and run an on-hand consistency check on all items

Before you run an on-hand consistency check on all items, we recommend that you follow these steps:

1. Go to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. Check the **Status** value to see if the job is enabled.
    - If **Status** is *Disabled*, then you can skip the rest of this procedure and just run the on-hand consistency check.
    - If **Status** is *Enabled*, then disable the job by selecting **Disable** on the Action Pane.
1. Run the on-hand consistency check.
1. When the check is complete, go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**.
1. On the **General** tab, set **Resync before initial push** to *Yes*.
1. Select **Save** on the Action Pane.
1. Return to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. Select **Enable** on the Action Pane to reenable the batch job.

The initial push with the `Resync` action will clean up legacy Supply Chain Management data in Inventory Visibility service and then resync the `InventSum` and `WHSInventReserve` tables to the Inventory Visibility Service.

> [!IMPORTANT]
> The Inventory Visibility service will return correct results after the reenabled *Inventory Visibility integration* batch job has completed.

## Prepare for and run an on-hand consistency check on selected items

If you only want to run an on-hand consistency check on a few selected items, then you don't have to take the extra steps listed in the previous section. Instead, you can just run the check.
