---
title: Run on-hand consistency checks while Inventory Visibility is enabled
description: Learn about the steps that you should complete before you run an on-hand consistency check while the Inventory Visibility integration batch job is enabled.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/01/2026
ms.custom: 
  - bap-template
---

# Run on-hand consistency checks while Inventory Visibility is enabled

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides an on-hand consistency check tool that you can use to recalculate inventory on-hand list data based on inventory transactions for selected items or all items. The tool analyzes the inventory transactions (`InventTrans`) table and then reconstructs the `InventSum` and `WHSInventReserve` tables.

> [!NOTE]
> This article describes only the additional preparation that's required when the *Inventory Visibility integration* batch job is enabled. For general guidance about when and how to run an on-hand consistency check, see [Run an on-hand consistency check](on-hand-consistency-check.md).

If you run an on-hand consistency check on *all items* while the *Inventory Visibility integration* batch job is enabled, the following conditions apply:

- The tool usually takes longer to finish running than it does when the *Inventory Visibility integration* batch job isn't enabled.
- The tool uses API calls to sync the changes in the `InventSum` and `WHSInventReserve` tables to the Inventory Visibility service. Therefore, if the *Inventory Visibility integration* batch job is enabled, the consistency check might fail if the external calls result in unexpected errors.

For these reasons, disable the *Inventory Visibility integration* batch job before you run an on-hand consistency check on all items.

## Prepare for and run an on-hand consistency check on all items

Before you run an on-hand consistency check on all items, follow these steps:

1. Go to **Inventory Management > Periodic Tasks > Inventory Visibility integration**.
1. Check the **Status** value to determine whether the job is enabled.

    - If the **Status** value is *Disabled*, you can skip the rest of this procedure and just run the on-hand consistency check.
    - If the **Status** value is *Enabled*, disable the job by selecting **Disable** on the Action Pane.

1. Run the on-hand consistency check.
1. When the check is completed, go to **Inventory Management > Setup > Inventory Visibility integration parameters**.
1. On the **General** tab, set the **Resync before initial push** option to *Yes*.
1. On the Action Pane, select **Save**.
1. Go to **Inventory Management > Periodic Tasks > Inventory Visibility integration**.
1. On the Action Pane, select **Enable** to reenable the batch job.

The initial push with the `Resync` action first cleans up legacy Supply Chain Management data in Inventory Visibility service. It then resyncs the `InventSum` and `WHSInventReserve` tables to the Inventory Visibility Service.

> [!IMPORTANT]
> The Inventory Visibility service resumes delivering correct query results after the reenabled *Inventory Visibility integration* batch job completes its initial push work.

## Prepare for and run an on-hand consistency check on selected items

If you want to run an on-hand consistency check on only a few selected items, you don't need to complete the extra steps that are described in the previous section. Instead, just run the check.
