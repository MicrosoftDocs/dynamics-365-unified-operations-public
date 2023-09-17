---
title: Asset downtime scenario
description: This article describes the asset downtime scenario, which lets you use sensor data to monitor the availability of your assets.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreScenarioConfigurationWizardV2, EntAssetObjectProductionStop
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Asset downtime scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The asset downtime scenario generates a maintenance downtime record if no signal is received from a machine within a defined time threshold since the last signal was received. The scenario requires that you fit your machine with a sensor that periodically sends a signal to your Azure IoT Hub while the machine is operating, but doesn't send a signal when the machine isn't operating.

## Set up the asset downtime scenario

Follow these steps to set up the *asset downtime* scenario in Supply Chain Management.

1. Go to **Asset Management \> Setup \> Sensor Data Intelligence \> Scenarios** to open the **Scenarios** page.
2. In the **Asset downtime** scenario box, select **Configure** to open the setup wizard for this scenario.
3. On the **Sensors** page, select **New** to add a sensor to the grid. Then set the following fields for it:

    - **Sensor ID** – Enter the ID of the sensor that you're using. (If you're using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md), enter *AssetDownTime*.)
    - **Sensor description** – Enter a description of the sensor.

4. Repeat the previous step for each additional sensor that you want to add now. You can come back and add more sensors at any time.
5. Select **Next**.
6. On the **Business record mapping** page, in the **Sensors** section, select the record for one of the sensors that you just added.
7. In the **Business record mapping** section, select **New** to add a row to the grid.
8. On the new row, set the **Business record** field to the resource that you're using the selected sensor to monitor. (If you're using the demo data, select *AK-101, Air Knife for Line 1*.)
9. Select **Next**.
10. On the **asset downtime threshold** page, define how long after the last signal the system should wait before send a asset downtime notification. There are two ways to define the threshold:

    - **Default threshold (minutes)** – Set this field to define the default threshold. This value applies to all resources where the **Notification threshold (minutes)** field is set to two minutes or less. The minimum value is *2* (minutes).
    - **Threshold to determine machine not responding (minutes)** – For each resource in the grid where don't want to use the default threshold, enter an override value in this field. Resources that are set to use a threshold of two minutes or less will use the **Default threshold (minutes)** setting instead.
11. Select **Next**.
12. On the **Activate sensors** page, in the grid, select the sensor that you set up, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.
13. Select **Finish**.

## Work with the asset downtime scenario

If no sensor signal is received from an asset within the threshold defined in the scenario configuration, the system will create a maintenance downtime record for that asset. Managers should periodically review the downtime records (for example, once during each working shift) and apply appropriate reason codes and end times for each downtime registration. Follow these steps to view the maintenance downtime records for an asset:

1. Go to **Asset management > Assets > All assets**.
2. Find and select the asset you want to inspect. (If you're using the demo data, select *AK-101*.)
3. On the Action Pane, open the **Asset** tab and, from the **Work order** group, select **Maintenance downtime** to open the page for maintenance downtime records for the selected asset.
