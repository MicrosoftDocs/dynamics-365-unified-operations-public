---
title: Register items by using an item arrival journal
description: Learn how to manually create an item arrival journal and generate its lines to register the receipt of items that don't use warehouse management processes.
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WMSJournalTable, WMSJournalCreate
ms.topic: how-to
ms.date: 10/09/2026
ms.custom:
  - bap-template
---

# Register items by using an item arrival journal

[!INCLUDE [banner](../includes/banner.md)]

When items arrive at a warehouse, you can use an item arrival journal to register them and update the on-hand quantities. A receiving clerk typically performs this task.

You can create an item arrival journal in two ways:

- Automatically, by starting an arrival from the **Arrival overview** page. Use this approach when you want to work from a list of expected receipts. Learn more in [Arrival overview](arrival-overview.md).
- Manually, by creating a journal on the **Item arrival** page and then generating the lines from the source order. This article describes this approach.

This article applies to items and warehouses that *aren't* enabled for warehouse management processes (WMS). If you use WMS, follow the procedure in [Register items enabled for warehouse management processes using an item arrival journal](../warehousing/tasks/register-items-advanced-warehousing.md) instead.

## Prerequisites

To work through this scenario by using the sample records and values that are specified in this article, you must be using a system where the standard [demo data](../../fin-ops-core/dev-itpro/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

You can instead work through this scenario by substituting values from your own data, provided that you have the following data available:

- A confirmed purchase order that has an open purchase order line.
- The item on the line must be stocked.
- The item must be associated with a storage dimension group where the site and warehouse dimensions are active.
- An item arrival journal name where **Check picking location** is set to *No* and **Quarantine management** is set to *No*.

## Create an item arrival journal header

The journal header identifies the delivery that you're receiving and links the journal to the order that the items were ordered on. The values that you enter here determine which order lines are available when you generate the journal lines in the next section. Follow these steps to create the header:

1. Go to **Inventory management** > **Journal entries** > **Item arrival** > **Item arrival**.
1. On the Action Pane, select **New**.
1. In the dialog box that appears, set the following fields:

    - **Name** – Select an item arrival journal name. If you're using *USMF* sample data, select *WHS*.
    - **Packing slip** – Enter the packing slip ID from the packing slip that the vendor issued. This value must be unique.
    - **Number** – Select the purchase order that you're receiving against.

1. Select **OK** to create the journal header.

## Generate the journal lines

You can enter journal lines manually, but it's usually faster to generate them from the source order. The **Create lines** function adds one line for each order line that still has a quantity to register. Follow these steps to generate the lines:

1. On the Action Pane, select **Functions** > **Create lines**.
1. In the dialog box that appears, set the **Initialize quantity** option:

    - Set it to *Yes* to set the quantity on each journal line to the quantity that remains to be registered on the corresponding order line. Use this setting when you receive the full outstanding quantity.
    - Set it to *No* to create the lines without quantities, so that you can enter the received quantity on each line yourself. Use this setting when you receive a partial delivery.

1. Select **OK**. The system creates one journal line for each order line that has a quantity to register.
1. Review the lines, and adjust the quantities if the delivery doesn't match what was ordered.

> [!NOTE]
> The **Create lines** function also works for item arrival journals that reference a sales return order or an inbound transfer order. The journal header determines which source order the lines are generated from.

## Post the journal and update the product receipt

When you post the journal, you register the items and update the on-hand quantities, but you don't update the order itself. To record the receipt against the purchase order and add the physical cost, you must also update the product receipt. Follow these steps to complete both tasks:

1. On the Action Pane, select **Post**.
1. In the dialog box that appears, select **OK**. The items are now registered, and the on-hand quantities are updated.
1. On the Action Pane, select **Functions** > **Product receipt** to update the purchase order and post a product receipt for the registered items.
1. In the dialog box that appears, select **OK**.

## Related information

- [Arrival overview](arrival-overview.md)
- [Inventory journals](inventory-journals.md)
- [Set up an item arrival overview profile](tasks/set-up-item-arrival-overview-profile.md)
- [Register items enabled for warehouse management processes using an item arrival journal](../warehousing/tasks/register-items-advanced-warehousing.md)
- [Inventory management overview](inventory-home-page.md)
