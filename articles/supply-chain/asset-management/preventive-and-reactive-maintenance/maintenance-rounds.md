---
title: Maintenance rounds
description: Learn about maintenance rounds in Asset Management, including outlines and step-by-step processes for setting up and scheduling maintenance rounds.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: EntAssetRoundTable 
ms.topic: how-to
ms.date: 08/28/2024
ms.custom: 
  - bap-template
---

# Maintenance rounds

[!include [banner](../../includes/banner.md)]

In Asset Management, you can create maintenance rounds for various assets, on which you need to carry out a similar task at regular intervals. For example, lubrication jobs or safety inspection jobs that need to be carried out on several machines within the same intervals. First step is to create a maintenance round, including assets that require the same form of maintenance job. Next, you schedule the maintenance rounds. When you have completed the maintenance rounds schedule, you can see all the job records relating to the round in the **All maintenance schedule** and **Open maintenance schedule lines**.

> [!NOTE]
> Maintenance rounds can also be set up on functional locations to be completed on the assets installed on the functional location at the time of creation of the round-based work order. For more information on the setup of maintenance rounds on functional locations, see [Create functional locations](../functional-locations/create-functional-locations.md).

## Set up a maintenance round

1. Go to **Asset management** \> **Setup** \> **Preventive maintenance** \> **Maintenance rounds**.
1. Select **New** to create a new maintenance round.
1. Make the following settings in the heading of the new record:
    - **Maintenance round** – Enter a unique ID for the new record.
    - **Name** – Enter a name for the maintenance round.

1. Make the following settings on the **Header** FastTab:
    - **Start date** – Select a start date for the round.
    - **Finish within days** – Enter the number of days the job should take to complete. The expected end date is calculated relative to the start date, which is calculated when maintenance schedule lines are created. For example, you can enter *7* in this field to indicate that the related job should be completed within a week of the start date.
    - **Finish within hours** – Enter the number of hours the job should take to complete.
    - **Auto create** – Set to *Yes* if work orders should automatically be created from maintenance schedule lines that are created from this maintenance round.
    - **Work order type** – Select the work order type to be used on work orders created from this maintenance round.
    - **Service level** – Select the work order service level to be used on work orders created from this maintenance round.
    - **Active** – Set to *Yes* to activate the maintenance round.
    - **Assets** – This read-only value shows the number of assets related to the maintenance round.
    - **Lines** – This read-only value shows the number of lines related to the maintenance round.

    > [!IMPORTANT]
    > If you set **Active** to *No*, the system won't add any lines for this round to the maintenance schedule when the *Schedule maintenance rounds* job runs.

1. On the **Asset lines** FastTab, select **Add** to add an asset to the maintenance round. Make the following settings for the new line:
    - **Line number** – A line number is automatically inserted in this field to indicate the sequence of the assets in the maintenance round.
    - **Asset** – Select the asset to be included in the maintenance round.
    - **Maintenance job type** – Select the maintenance job type for the asset.
    - **Maintenance job type variant** – If necessary, select a maintenance job type variant related to the maintenance job type.
    - **Trade** – If necessary, select a trade related to the maintenance job type.
    - **Period type** – Select the recurrence (such as *Day*, *Week*, or *Month*) for the maintenance round.
    - **Period frequency** – Enter the number of recurrences for the maintenance round. For example, if you have selected *Day* in the **Period type** field, and you enter the number *7* in this field, new maintenance round lines are created during preventive maintenance scheduling once a week.
    - **Start date** – Select a start date for the asset to be included in the maintenance round. This date might differ from the start date set on the maintenance round.

1. Repeat the previous step to add more assets to the maintenance round.
1. On the **Functional location lines** FastTab, select **Add** to add a functional location to the maintenance round. Refer to the descriptions of the related fields provided previously. The same fields are available as for creating an asset line, but you can also select **Manufacturer** and **Model** for a functional location, if necessary. If you only select a functional location on a line, but make no selections in **Asset type**, **Manufacturer**, **Model**, **Maintenance job type**, **Maintenance job type variant**, and **Trade**, all assets related to that functional location at the time of maintenance scheduling will be included in the maintenance round.
1. On the **Pools** FastTab, select **Add** to select a work order pool to be included in the maintenance round. Several work order pools can be connected to one maintenance round.
1. On the Action Pane, select **Save**.


The following illustration shows an example of a maintenance round containing three assets.

:::image type="content" source="media/13-preventive-maintenance.png" alt-text="Example of a maintenance round containing three assets" lightbox="media/13-preventive-maintenance.png":::

## Schedule maintenance rounds

When you've set up a maintenance round, you run a schedule job to schedule all the jobs related to the maintenance round.

1. Do one of the following steps:
    - Go to **Asset management** \> **Periodic** \> **Preventive maintenance** \> **Schedule maintenance rounds**.

    - Go to **Asset management** \> **Maintenance schedule** \> **All maintenance schedule**. Select a maintenance schedule line in the grid. On the Action Pane, open the **Maintenance schedule** tab and, from the **Schedule** group, select **Maintenance rounds**.

    - Go to **Asset management** \> **Maintenance schedule** \> **Open maintenance schedule lines**. Select a maintenance schedule line in the grid. On the Action Pane, open the **Maintenance schedule** tab and, from the **Schedule** group, select **Maintenance rounds**.

    - Go to **Asset management** \> **Maintenance schedule** \> **Open maintenance schedule pools**. Select a maintenance schedule line in the grid. On the Action Pane, open the **Maintenance schedule** tab and, from the **Schedule** group, select **Maintenance rounds**.

1. The **Schedule maintenance rounds** dialog opens.
    :::image type="content" source="media/14-preventive-maintenance.png" alt-text="Set up for a schedule job in the Schedule maintenance rounds dialog." lightbox="media/14-preventive-maintenance.png":::

    Make the following settings:
    - **Period** – Select the period type to use for the scheduling job.
    - **Period frequency** – Enter the number of periods to be included in the scheduling job. The start of the scheduling is the current date.
    - **Auto create** – Set to *Yes* if a work order should automatically be created based on a maintenance round.

    > [!NOTE]
    > If **Auto create** is set to *Yes* on the **Schedule maintenance rounds** dialog, and **Auto create** is also set to *Yes* on the **Maintenance rounds** page, the system creates work orders based on the maintenance round lines and also creates maintenance schedule lines with status *Work order created*. If only one of the **Auto create** toggle buttons is set to *Yes*, the system only creates maintenance schedule lines with status *Created*. In that case, no work orders are created.

1. If necessary, you can select specific rounds or another start date for the schedule job. To do so, select **Filter** and add the rounds to be included.

1. Select **OK**.

1. You're now able to see the maintenance rounds jobs in **Asset management** \> **Maintenance schedule** \> **All maintenance schedule** or **Open maintenance schedule lines**. If the scheduled rounds are connected to a work order pool, you also see maintenance schedule lines in **Open maintenance schedule pools**. Maintenance schedule lines created from a round have the reference type *Maintenance rounds*.

The following  illustration shows the maintenance schedule lines listed on the **All maintenance schedule** page.

:::image type="content" source="media/15-preventive-maintenance.png" alt-text="Maintenance schedule lines on the All maintenance schedule page." lightbox="media/15-preventive-maintenance.png":::

- When work orders are manually created on assets that are covered by a vendor warranty, a dialog box is shown to make the user aware of the warranty. The creation of the work order can then be canceled. The check for a warranty relation is omitted for work orders that are automatically created.  
- You can set up a batch job on the **Run in the background** FastTab to schedule rounds at regular intervals.  
- If a round is included in several work order pools (refer to [Work order pools](../work-orders/work-order-pools.md)), one record is shown for each pool in **Open maintenance schedule pools**. This is done to optimize the filtering options for work order pools.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
