---
title: Run on-hand consistency checks while Inventory Visibility is enabled
description: This article describes the steps that you should complete before you run an on-hand consistency check while the Inventory Visibility integration batch job is enabled.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Run on-hand consistency checks while Inventory Visibility is enabled

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides an on-hand consistency check tool that lets you recalculate inventory on-hand list data based on inventory transactions on selected items or all items. The tool analyzes the inventory transactions (`InventTrans`) table and then reconstructs the `InventSum` and `WHSInventReserve` tables.

If you run an on-hand consistency check on *all items* while the *Inventory Visibility integration* batch job is enabled, the following conditions apply:

- The tool usually takes longer to finish running than it does when the *Inventory Visibility integration* batch job isn't enabled.
- The tool uses API calls to sync the changes in the `InventSum` and `WHSInventReserve` tables to the Inventory Visibility service. Therefore, if the *Inventory Visibility integration* batch job is enabled, the consistency check might fail if the external calls result in unexpected errors.

For these reasons, we recommend that you disable the *Inventory Visibility integration* batch job before you run a on-hand consistency check on all items.

## Prepare for and run an on-hand consistency check on all items

Before you run an on-hand consistency check on all items, we recommend that you follow these steps.

1. Go to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. Check the **Status** value to determine whether the job is enabled.

    - If the **Status** value is *Disabled*, you can skip the rest of this procedure and just run the on-hand consistency check.
    - If the **Status** value is *Enabled*, disable the job by selecting **Disable** on the Action Pane.

1. Run the on-hand consistency check.
1. When the check is completed, go to **Inventory Management \> Setup \> Inventory Visibility integration parameters**.
1. On the **General** tab, set the **Resync before initial push** option to *Yes*.
1. On the Action Pane, select **Save**.
1. Go to **Inventory Management \> Periodic Tasks \> Inventory Visibility integration**.
1. On the Action Pane, select **Enable** to reenable the batch job.

The initial push with the `Resync` action will first clean up legacy Supply Chain Management data in Inventory Visibility service. It will then resync the `InventSum` and `WHSInventReserve` tables to the Inventory Visibility Service.

> [!IMPORTANT]
> The Inventory Visibility service will resume delivering correct query results after the reenabled *Inventory Visibility integration* batch job has completed its initial push work.

## Prepare for and run an on-hand consistency check on selected items

If you want to run an on-hand consistency check on only a few selected items, you don't have to complete the extra steps that are described in the previous section. Instead, you can just run the check.
