---
# required metadata

title: Scenario setup for IoT Intelligence
description: This topic explains how to configure scenarios for IoT Intelligence in Microsoft Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Scenario setup for IoT Intelligence

[!include [banner](../../includes/banner.md)]

This topic explains how to configure scenarios for IoT Intelligence in Microsoft Dynamics 365 Supply Chain Management. <!-- KFM: Hide setup info for now: Before you can set up the scenarios, you must [set up Microsoft Dynamics Lifecycle Services (LCS)](iot-lcs-setup.md). -->

In this topic, you will configure the **Equipment downtime** scenario so that a notification is generated in Supply Chain Management when a machine goes down. The topic also shows how to configure the **Product quality** scenario so that a notification is generated if an attribute of an item is outside a specified range, and how to configure the **Production delays** scenario so that a notification is generated if the production throughput falls below a threshold value.

## Configure the Equipment downtime scenario in Supply Chain Management

The **Equipment downtime** scenario maps a **PartOut** signal to a machine alert threshold. The machine is monitored only when it's selected for the scenario and when is set to **Running** in Supply Chain Management. If the time since a **PartOut** signal was last received from the machine exceeds the alert threshold, a **Machine down** notification is triggered. If the machine is still running, a **Machine up** notification is triggered when the next **PartOut** signal is received. If a machine stays down for 30 minutes, a new **Machine down** notification is triggered.

The **Equipment downtime** scenario has the following dependencies:

+ An alert can be triggered only if a production order is running on a mapped machine.
+ A signal that represents a mapped machine's **PartOut** signal must be sent to the IoT hub, and a unique property name must be included.
+ A UNIX **timestamp** property, where the value is expressed in milliseconds (ms), must be present in the Azure IoT Hub message.

To configure the scenario, follow these steps.

1. Sign in to Supply Chain Management.
2. Enable the IoT Intelligence feature flag. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
3. Configure the metrics. For more information, see [How to configure metrics](iot-metrics-setup.md#configure-metrics).
4. Go to **Production control \> Setup \> IoT Intelligence \> Scenario management**.
6. On the **Equipment downtime** tile, select **Configure** to open the configuration wizard.

   The first page in the wizard is the **Equipment sensor schema definition** page. On this page, your goal is to set up the schema in Supply Chain Management so that it matches the JavaScript Object Notation (JSON) format of the IoT Hub messages. Multiple message schemas can be defined. For more information, see [Schema formats for IoT Hub messages](iot-schema-format.md). In this example, the message payload contains a batch of messages that has the following format.

    ```json
    {
        "timestamp": 1576016821614,
        "payload": [
            {
                "id": "IoTInt.Machine1225.PartOut",
                "timestamp": 1576016821614,
                "value": True
            },
            {
                "id": "IoTInt.Machine1226.PartOut",
                "timestamp": 1576016991616,
                "value": True
            }
        ]
    }
    ```

7. Add a row to the table, and set the following values:

    1. Set the **Schema name** field to **ID**.
    2. Set the **Schema path** field to **/payload\[\*\]/id**.
    3. Set the **Description** field to **Message ID**.

8. Add another row to the table, and set the following values:

    1. Set the **Schema name** field to **Timestamp**.
    2. Set the **Schema path** field to **/payload\[\*\]/timestamp**.
    3. Set the **Description** field to **Message timestamp**.

9. Add another row to the table, and set the following values:

    1. Set the **Schema name** field to **Value**.
    2. Set the **Schema path** field to **/payload\[\*\]/value**.
    3. Set the **Description** field to **Message value**.

    > [!NOTE]
    > You don't have to define all the properties in the message. Define only the properties that you require. In the preceding steps, you didn't create a row for **Root timestamp**. The path of **Root timestamp** would be **/timestamp**.

10. Select **Next** to go to the **Equipment sensor schema map** page.
11. In the row for **Equipment resource ID**, in the **Schema name** field, select **ID**.
12. In the row for **UTC time**, in the **Schema name** field, select **Timestamp**.
13. In the row for **Part produced signal**, in the **Schema name** field, select **Value**.
14. Select **Next** to go to the **Equipment resource ID configuration** page.
15. Follow these steps to map the values in the IoT Hub message to the Supply Chain Management resources:

    1. In the **Signal Data Values** table, add a new row. In the **Value** field, enter **IoTInt.Machine1225.PartOut**. This value  comes from the JSON **id** property in the IoT Hub message.
    2. Select **Save**.
    3. In the **Business Record Mapping** table, select **New**. A default value for the **Business record type** field is automatically filled in, and you don't have to change it.
    4. In the **Business record** field, select the Supply Chain Management machine resource that the signal value is being sent from.
    5. Select **Save**.
    6. Repeat these steps to add a new business record mapping for **Machine1226**. You can map multiple signal data values to a single record in Supply Chain Management.

16. Use the **Selected** column to select the machines that you want to process. You don't have to define all signal values, and you don't have to select all machines.
17. Select **Next** to go to the **Part produced signal configuration** page.
18. In the **Signal Data Values** table, add a row, and set the **Value** field to **True**. This value comes from the JSON **value** property in the IoT Hub message. You can add as many values as you require for your scenario.
19. Select **Save**.
20. Select **Next** to go to the **Equipment downtime threshold** page. The machines that are listed are the machines that were previously mapped to signal values. On this page, you will define a threshold to determine whether a machine is down. For example, if you set the threshold to **10**, Supply Chain Management will generate a notification if no **PartOut** signal is received from a machine for 10 minutes.
21. Select **Next** to go to the **Enable scenario** page. Set the option to enable the scenario.
22. Select **Finish**.

The scenario setup is now completed. IoT Intelligence will automatically start to process the IoT Hub messages.

## Configure the Product quality scenario in Supply Chain Management

The **Product quality** scenario generates a notification if an attribute of an item is outside a specified range. For example, a sensor sends the weight of each item to IoT Hub. If an item is too heavy or too light, a notification is generated in Supply Chain Management.

The **Product quality** scenario has the following dependencies:

+ An alert can be triggered only if a production order is running on a mapped machine and producing a product that has a mapped batch attribute.
+ A signal that represents the batch attribute must be sent to the IoT hub, and a unique property name must be included.
+ A UNIX **timestamp** property, where the value is expressed in ms, must be present in the IoT Hub message.

## Configure the Production delays scenario in Supply Chain Management

The **Production delays** scenario generates a notification if the production throughput falls below a threshold value. In this scenario, a **PartOut** signal is sent to IoT Hub for each item that is produced. In Supply Chain Management, the order delay is calculated based on the amount of time that the production order is scheduled to run, the number of items that should be produced, the amount of time that the job has been running, and the number of **PartOut** signals that are received. A delay notification is generated if the number of **PartOut** signals for the job falls below the threshold value.

The **Production delays** scenario has the following dependencies:

+ An alert can be triggered only if a production order is running on a mapped machine.
+ A signal that represents a mapped machine's **PartOut** signal must be sent to the Azure IoT hub, and a unique property name must be included.
+ A UNIX **timestamp** property, where the value is expressed in ms, must be present in the IoT Hub message.

## Disable a scenario

To disable a scenario, follow these steps.

1. In Supply Chain Management, go to **Production control \> Setup \> IoT Intelligence \> Scenario management**.
2. On the tile for the scenario, select **Configure**.
3. Select **Next** to go to the last wizard page.
4. Set the option to disable the scenario.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]