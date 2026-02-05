---
title: Production auto report scenario (preview)
Learn about the Production auto report scenario, which uses sensor signals to measure finished goods output and automatically post the corresponding finished quantities in Supply Chain Management.

author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 09/02/2022
ms.reviewer: kamaybac
ms.search.form: IoTIntCoreScenarioManagement, IoTIntCoreNotification, IoTIntMfgResourceStatusConfiguration, IoTIntMfgResourceStatus
---

# Production auto report scenario (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The **Production auto report** scenario automatically reports finished quantities when a machine generates enough sensor signals to reach a defined output threshold. The scenario requires fitting the machine with a sensor that emits a signal for each production cycle, and mapping that sensor to the corresponding resource and operation. By defining how many signals correspond to one finished unit, the system can determine when progress should be reported and update the production order and inventory accordingly.

## Setup the Production auto report scenario

1. Go to **Production control > Setup > Sensor Data Intelligence > Scenarios** to open the **Scenarios** page.
1. In the **Production auto report scenario** box, select **Configure** to open the setup wizard for this scenario.
1. On the **Sensors** page, select **New** to add a sensor to the grid. Then set the following fields for it:
    - **Sensor ID** – Enter the ID of the sensor that you're using. (If you're using the Raspberry PI Azure IoT Online Simulator and have set it up as described in Set up a simulated sensor for testing, enter AssetDownTime.)
    - **Sensor description** – Enter a description of the sensor.
1. Repeat the previous step for each additional sensor that you want to add now. You can come back and add more sensors at any time.
1. Select **Next**.
1. On the **Business record mapping** page, in the **Sensors** section, select the record for one of the sensors that you just added.
1. In the **Business record mapping** section, select **New** to add a row to the grid.
1. On the new row, set the **Business record** field to the resource that you're using the selected sensor to monitor.
1. On the **Set auto-reporting threshold** page, select the operation relation you want you configuration to be applicable for. You can find a specific operation relation by following these steps:
    - Select the **Item relation** column heading to open a drop-down dialog box that includes search filters for the column. Enter the product that the operation relation is created for.
    - Select the **Route relation** column heading to open a drop-down dialog box that includes search filters for the column. Enter the route number that the operation relation is created for.

> [!NOTE]
An operation relation in Dynamics 365 SCM defines the detailed properties of an operation—such as setup time, run time, cost categories, and resource requirements—for a specific route or product. It lets the same operation have different properties depending on where it's used.

1. When you have found the applicable operation relation, you need to define measures for:
    - **Pulses per cycle** – Number of pulses the sensor emits in a production cycle.  
    - **Units per cycle** – Number of parts produced by the operation in a production cycle.

> [!NOTE]
A production cycle is the smallest repeatable unit of work performed by a machine that produces a measurable output.

1. Select **Next**.
1. On the **Activate sensors** page, in the grid, select the sensor that you set up, and then select **Activate**. For each activated sensor in the grid, a check mark appears in the **Active** column.
1. Select **Finish**.

## Setup the production floor execution interface

Add a button to the toolbar on the **Production Floor Execution interface** that lets workers access the counter view. Use the procedure provided in [Set up a device to run the production floor execution interface](../production-control/production-floor-execution-setup.md) , and insert the control labeled **View counter**.

## View sensor counters in the production floor execution interface

Jobs that are configured for auto reporting through a sensor signal appear in the job list on the **Production Floor Execution interface** with a dedicated icon, as indicated in the below image.

:::image type="content" source="media/sdi-sensor-icon.png" alt-text="Job list with sensor jobs":::

When a sensor controlled job is started, workers can open the **View counter** dialog by selecting **View counter** from the toolbar in the job list. As shown in the image below, the counter dialog displays the current progress counters for the job.

:::image type="content" source="media/sdi-view-counter.png" alt-text="View counter dialog":::

Counters are shown in one or two levels. The number of levels depends on the **Unit Sequence group ID** defined on the finished product. Learn more about configuring **Unit Sequence group ID** in: [Unit of measure and stocking policies](../warehousing/unit-measure-stocking-policies.md).

### Example of counters in a two level setup

In the example shown in the previous image, the first‑level counter indicates how many pieces have been added to the box currently being filled. Each time a sensor signal is received, the Level 1 counter increases. When the threshold of 12 pieces per box is reached, the Level 1 counter resets to zero and the Level 2 counter (which counts how many boxes are placed on a pallet) increases by one. When the Level 2 threshold of 100 boxes per pallet is reached, the Level 2 counter also resets to zero, indicating that a new pallet is ready to be filled. At this point, the system automatically reports a pallet as finished. The report as finished posting is processed through the message queue as an asynchronous (deferred) operation. Learn more about deferred posting here: [Make finished goods physically available before posting to journals](../production-control/deferred-posting.md).

### Pausing signals and adjusting counters

Workers can adjust counter values at each level using the + / – buttons. To adjust a counter, the worker must first pause the sensor signal. Sensor input can be started or stopped by selecting button (1) in the previous image. Counter adjustments are useful when part of the produced quantity must be scrapped. In this case, the worker pauses the signal, adjusts the counter to reflect the scrapped quantity, and then resumes the signal by selecting button (1) again. While the signal is paused, workers can manually report progress and scrap using buttons (2) and (3).

### Navigating between multiple sensor enabled jobs

If multiple jobs in the job list are enabled for sensor controlled reporting, the worker can use the **Previous** and **Next** buttons to switch between jobs without closing the dialog.