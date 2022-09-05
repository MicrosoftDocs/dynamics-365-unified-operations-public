---
title: The asset downtime scenario
description: This article describes the asset downtime scenario, which lets you use sensor data to monitor the availability of your assets.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreNotification, IoTIntMfgResourceStatusConfiguration, IoTIntMfgResourceStatus
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# The asset downtime scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Important: The asset downtime scenario requires Supply Chain Management version 10.0.29

The asset downtime scenario generates a maintenance downtime record on an asset in Supply Chain Management if no signal is received from the machine within a certain threshold value. In this scenario, a sensor signal is sent from the machine to Azure IoT Hub if the machine is operating. If the machine is not operating, no sensor signal is sent to the Azure IoT Hub.


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
8. On the new row, set the **Business record** field to the resource that you're using the selected sensor to monitor. (If you're using the demo data that you created earlier in this article, set the field to *AK-101, Air Knife for Line1*.)
9. Select **Next**.
10. On the **asset downtime threshold** page, define how long after the last *part-out* signal the system should send a asset downtime notification. There are two ways to define the threshold:

    - **Default threshold (minutes)** – Set this field to define the default threshold. The value will then apply to all resources where the **Threshold to determine machine not responding (minutes)** field is set to two minutes or less. The minimum value is *2* (minutes).
    - **Threshold to determine machine not responding (minutes)** – For each resource in the grid that you don't want to use the default threshold for, enter an override value in this field. Resources that are set to use a threshold of two minutes or less will use the **Default threshold (minutes)** setting instead.
11. Select **Next**.
12. On the **Activate sensors** page, in the grid, select the sensor that you added, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.
13. Select **Finish**.

## Work with the asset downtime scenario

If no sensor signal is received from the machine within the threshold defined in the scenario configuration, the machine is considered as being down and a maintenance downtime record is created on the asset that represents the machine in Supply Chain Management. Organizations can review the downtime record created in a specific time interval such as a working shift and apply appropriate reason codes and end time for the downtime registrations. Folow these steps to view the mainteance downtime record on an asset:

1. Go to **Asset management > Assets > All assets
2. Find and select the asset you want to inspect. (if you are using the sample data, look for *AK-101*.)
3. In the Action Pane, open the **Asset** tab and, in the **Work order** group, select **Maintenance downtime** to open the page for maintenance downtime records for asset *AK-101*

