---
title: The asset maintenance scenario
description: The asset maintenance scenario lets you use sensor data to create counter records that track the usage of a machine asset.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# The asset maintenance scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The *asset maintenance* scenario lets you use sensor data to create counter records. Counter records track the usage of a machine asset and are used as input for generating the maintenance schedule for machine assets.

## Prepare sample data for the product quality scenario

If you would like to use a demo system to test the *asset maintenance* scenario, then use a system that has the demo data installed and select the *USMF* legal entity (company). If you are using your own data, then you can skip this section.

In this section, you will set up the *AK-101, Air knife* asset in demo data as an example of how upcoming maintenance work can be predicted based on sensor signals that measure the number of hours the air knife has been running. You will also set up a maintenance plan in which the air knife must be maintained every 10,000 hours.

### Create a new asset counter for tracking production hours

Follow these steps to create a new asset counter for tracking production hours:

1. Go to **Asset management \> Setup \> Asset types \> Counters**.
1. On the Action Pane, select **New** to create a new counter and then make the following settings in the header:
    - **Counter:** *ProductionHr*
    - **Name:** *Production hours*

1. Expand the **General** FastTab and make the following settings:
    - **Unit:** *hr*
    - **Update:** *Manual*
    - **Total aggregate:** *Sum*

1. Expand the **Asset types** FastTab and select **Add line** from the toolbar.
1. For the new line, set **Asset type** to *Air knife*.

### Create a maintenance plan for the asset

Follow these steps to create a maintenance plan for the asset:

1. Go to **Asset management \> Setup \> Preventive maintenance \> Maintenance plan**.
1. On the Action Pane, select **New** to create a new maintenance plan and then make the following settings in the header:
    - **Maintenance plan:** *AirKnife*
    - **Name:** *Plan for air knives*

1. Expand the **Details** FastTab and make the following settings:
    - **Plan date:** Enter today's date
    - **Active:** *Yes*

1. Expand the **Lines** FastTab. Select **Add asset counter** line from the toolbar to add a new line to the grid and then make the following settings for the new line:
    - **Work order description:** Maintenance for air knife
    - **Maintenance job type:** *Preventive*
    - **Interval type:** *Repeated from last work order*
    - **Period frequency:** *10000*
    - **Counter:** *ProductionHr*

## Set up the asset maintenance scenario

Follow these steps to set up the *asset maintenance* scenario in Supply Chain Management:

1. Go to **Asset management \> Setup \> Sensor Data Intelligence \> Scenarios** to open the **Scenarios** page.
1. In the **Asset maintenance** scenario box, select **Configure** to launch the setup wizard for this scenario.
1. The wizard starts with the **Sensors** page. Select **New** to add a new sensor to the grid and set the following values for it:
    - **Sensor ID** - Enter the ID of the sensor you are using. (If you are using the Raspberry PI Azure IoT Online Simulator and have set it up as described previously in this article, then enter *AssetMaintenance*.)
    - **Sensor description** - Enter a description of the sensor.

1. Repeat the previous step for each sensor you want to add for now. You can come back and add more sensors at any time.
1. Select **Next**.
1. The **Business record mapping** page opens. In the **Sensors** section, select the record for the sensor you defined in the previous step.
1. In the **Business record mapping** section, select **New** to add a new row to the grid.
1. The new row should automatically show a **Business record type** of *Assets(EntAssetObjectTable)*. For this row, set **Business record** to the resource you are monitoring with the selected sensor. (If you are using the sample data created earlier in this article, set it to *AK-101, AK-101 Air Knife for Line 1*.)
1. Right after you select a business record type for the previous row, a second row is automatically added to the grid, this time with a **Business record type** of *Counters(EntAssetCounterType)*. For this row, set **Business record** to asset counter you are updating based on signals from the selected sensor. (If you are using the sample data created earlier in this article, set it to *ProductionHr, Production hours*.)
1. Select **Next**.
1. The **Activate sensors** page opens. In the grid, select the sensor you just added and then select **Activate**. Each activated sensor in the grid shows a check in its **Active** column.
1. Select **Finish**.

## Work with the asset maintenance scenario

### View counter values

Once the data is prepared and the *asset maintenance* scenario is configured and activated, you can see how records for an asset counter are inserted based on sensor data by using the following steps:

1. Go to **Asset management \> Assets \> All assets**.
1. Find and select the asset you want to inspect. (If you are using the sample data created earlier in this article, look for *AK-101*.)
1. In the Action Pane, open the **Asset** tab and, in the **Preventive** group, select **Counters** to open the page for counter records for asset *AK-101*.

### Generate maintenance work orders

When you have enabled the *asset maintenance* scenario and set up the maintenance plan, you can run the maintenance schedule to generate maintenance work order. You can read more about working with preventive maintenance in the official Microsoft documentation here:

[Preventive maintenance overview - Supply Chain Management \| Dynamics 365 \| Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management/preventive-and-reactive-maintenance/preventive-maintenance-overview)
