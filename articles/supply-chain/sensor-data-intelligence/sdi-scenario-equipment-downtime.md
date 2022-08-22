---
title: The equipment downtime scenario
description: The equipment downtime scenario lets you use sensor data to monitor the availability of your equipment.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreScenarioManagement
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# The equipment downtime scenario

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The *equipment downtime* scenario lets you use sensor data to monitor the availability of your equipment. If you have set up a sensor that sends a signal when a production job on a machine resource produces an output, and no sensor signal is received within a specified time interval, then a notification is shown on the supervisor's dashboard.

## Scenario dependencies

The *equipment downtime* scenario has the following dependencies:

- For a notification to be triggered, a production job must be in progress on a mapped machine.
- A signal that represents a part-out signal must be sent to the IoT hub.

## Prepare demo data for the equipment downtime scenario

If you would like to use a demo system to test the *equipment downtime* scenario, then use a system that has the [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) installed, select the *USMF* legal entity (company) and prepare the additional demo data as described in this section. If you are using your own sensors and data, then you can skip this section.

### Set up sensor simulator

If you'd like to try this scenario without using a physical sensor, then you can set up a simulator to generate the required signals as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md).

### Verify that resource 3118 is used for product P0111

A production order will be scheduled and released, so a production job is released to *Resource 3118 – Foam cutting machine*. Follow these steps to verify that *Resource 3118 – Foam cutting machine* is used for product *P0111* in your demo data:

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

### <a name="config-pfe"></a>Configure the production floor execution interface

You will use the production floor execution interface to start the job that was scheduled and released for **Item number** *P001* in the previous section. Follow these steps to configure the production floor execution interface:

1. Go to **Production control \> Manufacturing execution \> Production floor execution**.
1. Either a welcome page or sign-in page opens (depending on whether you have set up the interface before). Select **Configure** to launch the **Configure device** wizard.
1. On the **Configure device - Step 1 - Select configuration** page, select the *Default* configuration.
1. Select **Next**.
1. On the **Configure device - Step 2 - Define the production floor area** page, set **Resource** to *3118*.
1. Select **OK**.

### <a name="enable-pfe-search"></a>Enable the search option on the production floor execution interface

To make it easy to find the production job for the production order that was released in previous section, follow these steps to enable the search option on the production floor execution interface:

1. Go to **Production control \> Setup \> Manufacturing execution \> Configure production floor execution**.
1. Select the *Default* configuration.
1. On the Action Pane, select **Edit**.
1. Expand the **General** FastTab and set **Enable search** to *Yes*.
1. Close the page.

### Start the first job in the batch order

Start the job scheduled on *Resource 3118* by following these steps:

1. Go to **Production control \> Manufacturing execution \> Production floor execution**.
1. In the **Badge ID** field, type *123* and select**Sign in**.
1. If prompted for an absence reason, select one of the cards for absence and select **OK**.
1. In the **Search** field, enter the batch order number that you wrote down previously and then press return.
1. Select the order and then select **Start job**.
1. The **Start job** dialog opens. Select **Start**.

## Set up the Equipment downtime scenario

Follow these steps to set up the *equipment downtime* scenario in Supply Chain Management:

1. Go to **Production control \> Setup \> Sensor Data Intelligence \> Scenarios** to open the **Scenarios** page.
1. In the **Equipment downtime** scenario box, select **Configure** to launch the setup wizard for this scenario.
1. The wizard starts with the **Sensors** page. Select **New** to add a new sensor to the grid and set the following values for it:
    - **Sensor ID** - Enter the ID of the sensor you are using. (If you are using the Raspberry PI Azure IoT Online Simulator and have set it up as described in [Set up a simulated sensor for testing](sdi-set-up-simulated-sensor.md), then enter *EquipmentDowntime*.)
    - **Sensor description** - Enter a description of the sensor.

1. Repeat the previous step for each sensor you want to add for now. You can come back and add more sensors at any time.
1. Select **Next**.
1. The **Business record mapping** page opens. In the **Sensors** section, select the record for the sensor you defined in the previous step.
1. In the **Business record mapping** section, select **New** to add a row to the grid.
1. On the new row, set **Business record** to the resource you are monitoring with the selected sensor. (If you are using the demo data created earlier in this article, set it to *3118, Foam cutting machine*.)
1. Select **Next**.
1. The **Equipment downtime threshold** page opens. Use this page to establish how much time may pass after the last *part-out* signal before the system should send an equipment-down notification. There are two ways to define the threshold:
    - **Default threshold (minutes)** – Set this value to establish the default time interval. This value will apply to all resources that have **Threshold to determine machine not responding (minutes)** set to 2 minutes or less. The minimum value is 2 minutes.
    - **Threshold to determine machine not responding (minutes)** – For each resource in the grid where you don't want to use the default threshold, enter an override value here. Resources set to use 2 minutes or less will use the **Default threshold (minutes)** setting instead.

    > [!NOTE]
    > Usually, you'll use a *part-out* signal to monitor equipment downtime. Therefore, you should verify that the threshold for each machine resource is greater than the time is takes that machine to produce each part.

1. Select **Next**.
1. The **Activate sensors** page opens. In the grid, select the sensor you just added and then select **Activate**. Each activated sensor in the grid shows a check in its **Active** column.
1. Select **Finish**.

## Work with the Equipment downtime scenario

After you have installed your sensors and configured the scenario, you will be able to view equipment downtime events in Supply Chain Management. This section describes where and how to view this information.

### View equipment downtime data on the Resource status page

On the **Resource status** page, supervisors can monitor a timeline of the parts-out signal received from the sensors mapped to each machine resource. Follow these steps to configure the timeline:

1. Go to **Production control \> Manufacturing execution \> Resource status**.
1. The **Configure** dialog opens. Set the following values:
    - **Resource** – Select the resources you want to monitor. (If you're working with the demo data, select *3118*.)
    - **Time series 1** - Select the record (metric key) with the following name format: *MachineReportingStatus:&lt;Sensor&gt;*
    - **Display name** – Enter *Parts out signal*.

The following screenshots provide some examples of how equipment downtime data looks on the **Resource status** page.

![Equipment downtime data on the Resource status page, standard operation.](media/sdi-resource-status-downtime-up.png "Equipment downtime data on the Resource status page, standard operation")

![Equipment downtime data on the Resource status page, downtime detected.](media/sdi-resource-status-downtime-down.png "Equipment downtime data on the Resource status page, downtime detected")

### View equipment downtime on the Notifications page

On the **Notifications** page, supervisors can see the notifications generated when too much time has passed since the sensor last delivered a parts-out signal. Each notification provides an overview of which production job is impacted by the outage and provides the option to reassign the affected job to another resource.

To open the **Notification** page, go to **Production control \> Inquiries and reports \> Sensor Data Intelligence \> Notifications**.

The following screenshot shows an example of an equipment downtime notification.

![Example of an equipment downtime notification.](media/sdi-resource-status-downtime-notification.png "Example of an equipment downtime notification")
