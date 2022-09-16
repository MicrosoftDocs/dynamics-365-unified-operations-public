---
title: Use batch disposition codes to mark batches as available or unavailable
description: This article describes how to set up and use batch disposition codes to mark batches as available or unavailable* for use in master planning, reservation, picking, and/or shipping.
author: t-benebo
ms.date: 09/16/2022
ms.topic: article
ms.search.form: PdsDispositionMaster, InventBatch
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-09-16
ms.dyn365.ops.version: 10.0.29
---

# Use batch disposition codes to mark batches as available or unavailable

This article describes how to set up and use *batch disposition codes*. Each batch disposition code has a status of either *Available* or *Unavailable*, and you will assign batch disposition codes to inventory batches to indicate whether each batch is available for master planning, reservation, picking, and/or shipping.

To use batch disposition codes, you must set up the codes and assign them to the batches that you want to manage.

## Set up batch disposition codes

You must set up each code that you want to use in your system. You can create as many as you like, for example to identify various reasons a batch might be available or unavailable, but often you will have just two&mdash;one for *available* and one for *unavailable*. You can also create custom codes that allow a batch to be used for some operations but not others.

Use the following procedure to set up your batch disposition codes:

1. Go to **Inventory management > Setup > Batch > Batch disposition master**.
1. The **Batch disposition master** page opens. It lists your current batch disposition codes and lets you create, delete, and edit them. Do one of the following:
    - To edit an existing code, select it in the list pane.
    - To create a new code, select **New** on the Action Pane.
1. Make the following settings in the header of your new or selected code:
    - **Batch disposition code** – Enter the display name for the code.
    - **Description** – Describe how the code should be used.
    - **Batch disposition status** – Select the status that will apply to batches where this code is assigned. Choose one of the following values:
        - *Unavailable* – Batches with this code won't be available for use for master planning, reservation, picking, or shipping. When you select this value, all of the toggles on the **Setup** FastTab will be set with **Block** = *Yes* and **Nettable** = *No*. However, you will be able to change some of these settings to add exceptions if you need to.
        - *Available* – Batches with this code will be available for use for master planning, reservation, picking, and/or shipping. When you select this value, all of the toggles on the **Setup** FastTab will be set with **Block** = *No* and **Nettable** = *Yes*. These settings will be read-only while **Batch disposition status** is set to *Available*.
1. If you set **Batch disposition status** to *Unavailable*, you will be able to customize the block status of each operation (reserve, pick, and ship) for each type of order (sales, transfer, or production). For production orders, you can choose to block or unblock the production picking journal. You can also choose to block or unblock master planning. Use the sliders on the **Setup** FastTab to block or unblock each of these operations as needed. Set the **Nettable** slider to *Yes* to allow master planning; set it to *No* to block it.

## Assign batch disposition codes to batches

Once you have defined the batch disposition codes you need, you can assign them to your batches as needed, as described in the following procedure.

1. Go to **Warehouse management > Setup > Inventory > Batches**.
1. Select one or more batches that you want to assign a code to.
1. On the Actin Pane, open the **Reset** tab and select **Reset batch disposition code**.
1. The **Change the restrictions on the inventory batch** dialog opens.
1. Set **New batch disposition code** to the name of the code you want to assign.
1. Select **OK** to apply the settings and save the change.
1. On the **Batches** page, the values in the **Batch disposition code** and **Batch disposition status** columns update to reflect your new settings for the selected batches.

## Master planning example

This example illustrates how batch disposition codes can affect master planning.

Suppose you have batch disposition codes set up as in the following examples:

- *P-Available*:
  - **Batch disposition status:** *Available*
  - **Nettable:** *Yes*

- *P-Unavailable*:
  - **Batch disposition status:** *Unavailable*
  - **Nettable:** *No*

The is a product called *Product-1* with two batches: *Batch-A* and *Batch-B*. The batches are set up as follows:

- *Batch-A*:
  - **Batch disposition code:** *P-Available*
  - **On-hand quantity:** 1

- *Batch-B*:
  - **Batch disposition code:** *P-Unavailable*
  - **On-hand quantity:** 1

There is a sales order (*SO1*) for quantity 2 of *Product-1* with a delivery date three days from today.

Now you run master planning with the following settings that are relevant for this example:

- **Planned order:** *Purchase order*
- **Replenishment strategy:** *Requirement*
- **Lead time:** *0*

As a result of the planning run, the system will use the available batch (*Batch-A*) to cover one quantity of *Product-1* for *SO1*. But it can't use Batch-B because it's marked as unavailable for planning. Therefore, the system creates a planned purchase order (*PPO1*) for a new batch of *Product-1* to cover the remaining quantity.

The following illustration shows a timeline for the planning result.

![Example of how batch disposition codes can affect master planning.](media/batch-codes-planning-example.png "Example of how batch disposition codes can affect master planning")
