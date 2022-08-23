---
title: The production delays scenario
description: The production delays scenario generates a notification if production throughput falls below a certain threshold value. 
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

# The production delays scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The *production delays* scenario generates a notification if production throughput falls below a certain threshold value. In this scenario, a *part-out* signal is sent to Azure IoT Hub for each item that is produced. In Supply Chain Management, the order delay is calculated based on the amount of time that the production order is scheduled to run, the number of items that should be produced, the amount of time that the job has been running, and the number of *part-out* signals received. A delay notification is generated if the number of *part-out* signals for the job falls below the threshold value.

## Scenario dependencies

The *production delays* scenario has the following dependencies:

- An alert can be triggered only if a production order is running on a mapped machine.
- A signal that represents a mapped machine's *part-out* signal must be sent to the Azure IoT Hub, and a unique property name must be included.
- A UNIX timestamp property, where the value is expressed in milliseconds (ms), must be present in the Azure IoT Hub message.

## Prepare demo data for the product delays scenario

If you'd like to use a demo system to test the *production delays* scenario, then use a system that has the [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) installed, select the *USMF* legal entity (company) and prepare the additional demo data as described in this section. If you are using your own sensors and data, then you can skip this section.

### Set up sensor simulator

If you'd like to try this scenario without using a physical sensor, then you can set up a simulator to generate the required signals as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md).

### Verify that resource 3118 is used for product P0111

A production order will be scheduled and released, so a production job is released to *Resource 3118* *– Foam cutting machine*. Follow these steps to verify that *Resource 3118 – Foam cutting machine* is used for product *P0111* in your demo data:

1. Go to **Product information management \> Products \> Released products**.
1. Find and select the product with **Item number** *P0111*.
1. On the Action Pane, select the **Engineer** tab and, in the **View** group, select **Route**.
1. On the **Route** page, open the **Overview** tab at the bottom of the page and select the line with **Oper. No.** *30*.
1. At the bottom of the page, open the **Resource requirements** tab and make sure that the resource *3118 – Foam cutting machine* is associated with the operation.

### Create and release a production order for product P0111

Follow these steps to create and release a production order for product *P0111*:

1. Go to **Production control \> Production orders \> All production orders**.
1. The **All production orders** page opens. On the Action Pane, select **New batch order**.
1. The **Create batch** dialog opens. Set the following values:
    - **Item number:** *P0111*
    - **Quantity:** *10*

1. Select **Create** in the dialog to create the order and return to the **All production orders** page.
1. Use the **Filter** field to find production orders for **Item number** *P0111*. Then identify and select the production order that you just created.
1. On the Action Pane, select the **Production order** tab and, in the **Process** group, select **Estimate**.
1. The **Estimate** dialog opens. Select **OK** to run the estimate.
1. On the Action Pane, select the **Production order** tab and, in the **Process** group, select **Release**.
1. The **Release** dialog opens.
1. Write down the number for the batch order you just created.
1. Select **OK** to release the order.

### Configure the production floor execution interface

If you haven't already done so, configure the production floor execution interface to show jobs assigned to the *3118 – Foam cutting machine* resource. See the following sections for instructions:

- [Configure the production floor execution interface](sdi-scenario-equipment-downtime.md#config-pfe)
- [Enable search option on the production floor execution interface](sdi-scenario-equipment-downtime.md#enable-pfe-search)

### Start the first job in the batch order

Follow these steps to start the first job in the batch order:

1. Go to **Production control \> Manufacturing execution \> Production floor execution**.
1. In the **Badge ID** field, type *123* and select **Sign in**.
1. If prompted for an absence reason, select one of the cards for absence and select **OK**.
1. In the **Search** field, enter the batch order number that you wrote down previously and then press return.
1. Select the order and then select **Start job**.
1. The **Start job** dialog opens. Select **Start**.

## Set up the production delays scenario

Follow these steps to set up the *production delays* scenario in Supply Chain Management:

1. Go to **Production control \> Setup \> Sensor Data Intelligence \> Scenarios** to open the **Scenarios** page.
1. In the **Production delays** scenario box, select **Configure** to launch the setup wizard for this scenario.
1. The wizard starts with the **Sensors** page. Select **New** to add a new sensor to the grid and set the following values for it:
    - **Sensor ID** - Enter the ID of the sensor you are using. (If you are using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md), then enter *ProductionDelay*.)
    - **Sensor description** - Enter a description of the sensor.

1. Repeat the previous step for each sensor you want to add for now. You can come back and add more sensors at any time.
1. Select **Next**.
1. The **Business record mapping** page opens. In the **Sensors** section, select the record for the sensor you defined in the previous step.
1. In the **Business record mapping** section, select **New** to add a row to the grid.
1. On the new row, set **Business record** to the resource you are monitoring with the selected sensor. (If you are using the demo data created earlier in this article, set it to *3118, Foam cutting machine*.)
1. Select **Next**.
1. The **Production delay deviation threshold** page opens. If you are using the demo data created earlier in this article, make the following settings:
    - Select the **Item relation** column heading to open a drop-down dialog with search filters for the column. Enter *P0111* into the search box and select**Apply**.
    - Select the line where **Operation** is *Trim/Cut*. For this line, set **Notification threshold for delay (%)** to the threshold (as a percentage) at which a notification should be sent.

1. Select **Next**.
1. The **Activate sensors** page opens. In the grid, select the sensor you just added and then select **Activate**. Each activated sensor in the grid shows a check in its **Active** column.
1. Select **Finish**.

## Work with the production delays scenario

### View production delay data on the Resource status page

On the **Resource status** page, supervisors can monitor a timeline of signals received from the sensors mapped to each machine resource. Follow these steps to configure the timeline:

1. Go to **Production control \> Manufacturing execution \> Resource status**.
1. The **Configure** dialog opens. Set the following values:
    - **Resource** – Select the resources you want to monitor. (If you're working with the demo data, select *3118*.)
    - **Time series 1** - Select the record (metric key) with the following name format: *ProductionJobDelayed:ActualQuantity:&lt;JobId&gt;*
    - **Display name** – Enter *Parts out signal*.
