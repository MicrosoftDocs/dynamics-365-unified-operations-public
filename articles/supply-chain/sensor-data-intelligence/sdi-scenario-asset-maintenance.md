---
title: Asset maintenance scenario
description: This article describes the asset maintenance scenario, which lets you use sensor data to create counter records that track the use of a machine asset.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreScenarioConfigurationWizardV2, EntAssetCounter
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Asset maintenance scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The *asset maintenance* scenario lets you use sensor data to create counter records. Counter records track the use of a machine asset and are used as input to generate the maintenance schedule for machine assets.

## Video instructions

The following video shows how to set up and try out the asset maintenance scenario using standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md). The remaining sections in this article provide the same instructions in a text-based format.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE58aRW]

## Prepare demo data for the asset maintenance scenario

If you want to use a demo system to test the *asset maintenance* scenario, use a system where the [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, select the *USMF* legal entity (company), and prepare the additional demo data as described in this section. If you're using your own sensors and data, you can skip this section.

In this section, you will set up the *AK-101, Air knife* asset in demo data as an example. You will then see how upcoming maintenance work can be predicted based on sensor signals that measure the number of hours that the air knife has been running. You will also set up a maintenance plan where the air knife must be maintained every 10,000 hours.

### Set up a sensor simulator

If you want to try this scenario without using a physical sensor, you can set up a simulator to generate the required signals. For more information, see [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md).

### Create an asset counter to track production hours

Follow these steps to create an asset counter to track production hours.

1. Go to **Asset management \> Setup \> Asset types \> Counters**.
1. On the Action Pane, select **New** to create a counter.
1. On the header, set the following values:

    - **Counter:** *ProductionHr*
    - **Name:** *Production hours*

1. On the **General** FastTab, set the following values:

    - **Unit:** *hr*
    - **Update:** *Manual*
    - **Total aggregate:** *Sum*

1. On the **Asset types** FastTab, select **Add line**.
1. On the new line, set the **Asset type** field to *Air knife*.

### Create a maintenance plan for the asset

Follow these steps to create a maintenance plan for the asset.

1. Go to **Asset management \> Setup \> Preventive maintenance \> Maintenance plan**.
1. On the Action Pane, select **New** to create a maintenance plan.
1. On the header, set the following values:

    - **Maintenance plan:** *AirKnife*
    - **Name:** *Plan for air knives*

1. On the **Details** FastTab, set the following values:

    - **Plan date:** Enter today's date.
    - **Active:** *Yes*

1. On the **Lines** FastTab, select **Add asset counter line** to add a line to the grid. Then set the following values for it:

    - **Work order description:** *Maintenance for air knife*
    - **Maintenance job type:** *Preventive*
    - **Interval type:** *Repeated from last work order*
    - **Period frequency:** *10000*
    - **Counter:** *ProductionHr*

## Set up the asset maintenance scenario

Follow these steps to set up the *asset maintenance* scenario in Supply Chain Management.

1. Go to **Asset management \> Setup \> Sensor Data Intelligence \> Scenarios**.
1. In the **Asset maintenance** scenario box, select **Configure** to open the setup wizard for this scenario.
1. On the **Sensors** page, select **New** to add a sensor to the grid. Then set the following fields for it:

    - **Sensor ID** – Enter the ID of the sensor that you're using. (If you're using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md), enter *AssetMaintenance*.)
    - **Sensor description** – Enter a description of the sensor.

1. Repeat the previous step for each additional sensor that you want to add now. You can come back and add more sensors at any time.
1. Select **Next**.
1. On the **Business record mapping** page, in the **Sensors** section, select the record for one of the sensors that you just added.
1. In the **Business record mapping** section, select **New** to add a row to the grid.
1. On the new row, the **Business record type** field should automatically be set to *Assets(EntAssetObjectTable)*. Set the **Business record** field to the resource that you're using the selected sensor to monitor. (If you're using the demo data that you created earlier in this article, set it to *AK-101, AK-101 Air Knife for Line 1*.)
1. Immediately after you select a business record type for the row that you added in the previous step, a second row is automatically added to the grid. On this row, the **Business record type** field should be set to *Counters(EntAssetCounterType)*. Set the **Business record** field to the asset counter that you're updating based on signals from the selected sensor. (If you're using the demo data that you created earlier in this article, set it to *ProductionHr, Production hours*.)
1. Select **Next**.
1. On the **Activate sensors** page, in the grid, select the sensor that you added, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.
1. Select **Finish**.

## Work with the asset maintenance scenario

### View counter values

After the data is prepared, and the *asset maintenance* scenario is configured and activated, you can see how records for an asset counter are inserted based on sensor data.

1. Go to **Asset management \> Assets \> All assets**.
1. Find and select the asset that you want to inspect. (If you're using the demo data that you created earlier in this article, select *AK-101*.)
1. On the Action Pane, on the **Asset** tab, in the **Preventive** group, select **Counters** to open the page for counter records for asset *AK-101*.

> [!NOTE]
> The counter records are configured by default to be inserted every three hours, which means sensor data will be aggregated at that interval. You can change the interval by editing the query in the Azure Stream Analytics component.

### Generate maintenance work orders

After you enable the *asset maintenance* scenario and set up the maintenance plan, you can run the maintenance schedule to generate maintenance work orders. For more information about how to work with preventive maintenance, see [Preventive maintenance overview](../asset-management/preventive-and-reactive-maintenance/preventive-maintenance-overview.md).
