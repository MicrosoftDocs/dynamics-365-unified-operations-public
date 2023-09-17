---
title: Production delays scenario
description: This article describes the production delays scenario, which generates a notification if production throughput falls below a specific threshold value.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreScenarioConfigurationWizardV2, IoTIntMfgResourceStatusConfiguration, IoTIntMfgResourceStatus
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Production delays scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The *production delays* scenario generates a notification if production throughput falls below a specific threshold value. In this scenario, a *part-out* signal is sent to Microsoft Azure IoT Hub for each item that is produced. In Dynamics 365 Supply Chain Management, the order delay is calculated based on the amount of time that the production order is scheduled to run, the number of items that should be produced, the amount of time that the job has been running, and the number of *part-out* signals that have been received. A delay notification is generated if the number of *part-out* signals for the job falls below the threshold value.

## Scenario dependencies

The *production delays* scenario has the following dependencies:

- An alert can be triggered only if a production order is running on a mapped machine.
- A signal that represents a mapped machine's *part-out* signal must be sent to IoT Hub, and a unique property name must be included.
- A UNIX timestamp property, where the value is expressed in milliseconds (ms), must be present in the Azure IoT Hub message.

## Prepare demo data for the product delays scenario

If you want to use a demo system to test the *production delays* scenario, use a system where the [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, select the *USMF* legal entity (company), and prepare the additional demo data as described in this section. If you're using your own sensors and data, you can skip this section.

### Set up sensor simulator

If you want to try this scenario without using a physical sensor, you can set up a simulator to generate the required signals. For more information, see [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md).

### Verify that resource 3118 is used for product P0111

A production order will be scheduled and released. Therefore, a production job is released to resource *3118* (*Foam cutting machine*). Follow these steps to verify that resource *3118* is used for product *P0111* in your demo data.

1. Go to **Product information management \> Products \> Released products**.
1. Find and select the product where the **Item number** field is set to *P0111*.
1. On the Action Pane, on the **Engineer** tab, in the **View** group, select **Route**.
1. On the **Route** page, on the **Overview** tab at the bottom of the page, select the line where the **Oper. No.** field is set to *30*.
1. On the **Resource requirements** tab at the bottom of the page, make sure that resource *3118* (*Foam cutting machine*) is associated with the operation.

### Create and release a production order for product P0111

Follow these steps to create and release a production order for product *P0111*.

1. Go to **Production control \> Production orders \> All production orders**.
1. On the **All production orders** page, on the Action Pane, select **New batch order**.
1. In the **Create batch** dialog box, set the following values:

    - **Item number:** *P0111*
    - **Quantity:** *10*

1. Select **Create** to create the order and return to the **All production orders** page.
1. Use the **Filter** field to search for production orders where the **Item number** field is set to *P0111*. Then find and select the production order that you just created.
1. On the Action Pane, on the **Production order** tab, in the **Process** group, select **Estimate**.
1. In the **Estimate** dialog box, select **OK** to run the estimate.
1. On the Action Pane, on the **Production order** tab, in the **Process** group, select **Release**.
1. In the **Release** dialog box, make a note of the number of the batch order that you just created.
1. Select **OK** to release the order.

### Configure the production floor execution interface

If you haven't already done so, configure the production floor execution interface to show jobs that are assigned to resource *3118* (*Foam cutting machine*). For instructions, see the following sections:

- [Configure the production floor execution interface](sdi-scenario-equipment-downtime.md#config-pfe)
- [Enable search option on the production floor execution interface](sdi-scenario-equipment-downtime.md#enable-pfe-search)

### Start the first job in the batch order

Follow these steps to start the first job in the batch order.

1. Go to **Production control \> Manufacturing execution \> Production floor execution**.
1. In the **Badge ID** field, enter *123*. Then select **Sign in**.
1. If you're prompted for an absence reason, select one of the cards for absence, and then select **OK**.
1. In the **Search** field, enter the batch order number that you previously made a note of. Then select the **Return** key.
1. Select the order, and then select **Start job**.
1. In the **Start job** dialog box, select **Start**.

## Set up the production delays scenario

Follow these steps to set up the *production delays* scenario in Supply Chain Management.

1. Go to **Production control \> Setup \> Sensor Data Intelligence \> Scenarios**.
1. In the **Production delays** scenario box, select **Configure** to open the setup wizard for this scenario.
1. On the **Sensors** page, select **New** to add a sensor to the grid. Then set the following fields for it:

    - **Sensor ID** – Enter the ID of the sensor that you're using. (If you're using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md), enter *ProductionDelay*.)
    - **Sensor description** – Enter a description of the sensor.

1. Repeat the previous step for each additional sensor that you want to add now. You can come back and add more sensors at any time.
1. Select **Next**.
1. On the **Business record mapping** page, in the **Sensors** section, select the record for one of the sensors that you just added.
1. In the **Business record mapping** section, select **New** to add a row to the grid.
1. On the new row, set **Business record** to the resource that you're using the selected sensor to monitor. (If you're using the demo data that you created earlier in this article, set it to *3118, Foam cutting machine*.)
1. Select **Next**.
1. On the **Production delay deviation threshold** page, if you're using the demo data that you created earlier in this article, follow these steps:

    1. Select the **Item relation** column heading to open a drop-down dialog box that includes search filters for the column. Enter *P0111* in the search box, and then select **Apply**.
    2. Select the line where the **Operation** field is set to *Trim/Cut*. Set the **Notification threshold for delay (%)** field to the threshold (as a percentage) that a notification should be sent at.

1. Select **Next**.
1. On the **Activate sensors** page, in the grid, select the sensor that you added, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.
1. Select **Finish**.

## Work with the production delays scenario

### View production delay data on the Resource status page

On the **Resource status** page, supervisors can monitor a timeline of signals that are received from the sensors that are mapped to each machine resource. Follow these steps to configure the timeline.

1. Go to **Production control \> Manufacturing execution \> Resource status**.
1. In the **Configure** dialog box, set the following fields:

    - **Resource** – Select the resources that you want to monitor. (If you're working with the demo data, select *3118*.)
    - **Time series 1** – Select the record (metric key) that has the following format for its name: *ProductionJobDelayed:ActualQuantity:&lt;JobId&gt;*
    - **Display name** – Enter *Parts out signal*.
