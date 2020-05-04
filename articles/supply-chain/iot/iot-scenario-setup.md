---
# required metadata

title: Scenario setup for IoT Intelligence
description: This topic describes how to configure a scenario in Supply Chain Management for IoT Intelligence.
author: robinarh
manager: AnnBe
ms.date: 08/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Scenario setup for IoT Intelligence

[!include [banner](../../includes/banner.md)]

This topic describes how to configure a scenario in Supply Chain Management for IoT Intelligence. Before you can setup the scenarios, you must [setup LCS](iot-lcs-setup.md).

In this topic, you will configure the **Equipment downtime** scenario to generate a notification in Supply Chain Management when a machine goes down.

## Configure the **Equipment downtime** scenario in Supply Chain Management

The **Equipment downtime** scenario maps a part out signal to a machine alert threshold. The machine is monitored only when the machine is selected for the scenario and is set to running in Supply Chain Management. If the time since the machine’s last received Part Out signal is greater than the alert threshold, then a **Machine down** notification is triggered. If the machine is still running, when the next **PartOut** signal is received a **Machine up** notification is triggered. If a machine stays down for 30 mins a new **Machine down** notification is triggered.

The **Equipment downtime** scenario has these dependencies:

+ A production order must be running on a mapped machine for an alert to be triggered.
+ A signal representing a mapped machine's part out signal must be sent to the IoT Hub with a unique property name.
+ A Unix milliseconds timestamp property must be present in the IoT hub message.

To configure the scenario, follow these steps:

1. Log into Supply Chain Management.
2. Enable the IoT Intelligence feature flag. For more information, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
3. Configure the metrics. For more information, see [How to configure metrics](iot-metrics-setup.md#how-to-configure-metrics).
4. Navigate to **Production control**.
5. Navigate to **Setup \> IoT Intelligence \> Scenario management**.
6. Click **Configure** on the **Equipment downtime** tile. The configuration wizard starts with the **Equipment sensor schema definition** page. The goal here is to setup the schema in Supply Chain Management to match the JSON format of the IoT messages. Multiple message schemas can be defined. For more information, see [Message schema formats for IoT Hub](iot-json-setup.md). In this example, the message payload contains a batch of messages with this format:

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

7. Add a row to the table.

    1. Set the **Schema name** to **ID**.
    2. Set the **Schema path** to **/payload[\*]/id**.
    3. Set the **Description** to **Message ID**.

8. Add a row to the table.

    1. Set the **Schema name** to **Timestamp**.
    2. Set the **Schema path** to **/payload[\*]/timestamp**.
    3. Set the **Description** to **Message timestamp**.

9. Add a row to the table.

    1. Set the **Schema name** to **Value**.
    2. Set the **Schema path** to **/payload[\*]/value**.
    3. Set the **Description** to **Message value**.

    You don't need to define all the properties in the message, only the ones that you need. In this example, you did not create a row for **Root timestamp**. The path for **Root timestamp** would be **/timestamp**.
  
10. Click **Next** to go to the **Equipment sensor schema map** page.
11. In the row for **Equipment resource ID** set the **Schema name** to **ID**. The valid values are displayed in a dropdown table.
12. In the row for **UTC time** set the **Schema name** to **Timestamp**. The valid values are displayed in a dropdown table.
13. In the row for **Part produced signal** set the **Schema name** to **Value**. The valid values are displayed in a dropdown table.
14. Click **Next** for the **Equipment resource ID configuration** page.
15. In this step, you map the IoT Hub message values to the Supply Chain Management resources.

    1. In the **Signal Data Values** table, add a new row, and enter **IoTInt.Machine1225.PartOut** in the **Value** column. The value **IoTInt.Machine1225.PartOut** comes from the JSON **id** property in the IoT hub message.
    2. Click **Save**.
    3. In the **Business Record Mapping** table, click **New**. The default value for the **Business record type** is autopopulated, and you don't need to change it.
    4. In the **Business record** column, select the Supple Chain Management machine resource this signal value is being sent from.
    5. Click **Save**.
    6. Repeat these steps, adding a new business record mapping for **Machine1226**. You can map multiple signal data values to a single record in Supply Chain Management.

16. Use the **Selected** column to choose which machines you want to process. You do not have to define all signal values and you do not have to select all machines.
17. Click **Next** to go to the **Part produced signal configuration** page.
18. In the **Signal Data Values** table, add a row, and set **Value** to **True**. The value **True** comes from the JSON **value** property in the IoT hub message. You can add as many values as you need for your scenario.
19. Click **Save**.
20. Click **Next** to go to the **Equipment downtime threshold** page. The machines listed are the machines previously mapped to signal values. In this step, you define a threshold to determine if a machine is down. For example, if you set the threshold to 10, Supply Chain Management generates a notification if there is no part out message from a machine for 10 minutes.
21. Click **Next** to go to the **Enable scenario** page. Toggle the slider to enable the scenario.
22. Click **Finish**.

The scenario setup is complete. IoT Intelligence will automatically start processing the IoT Hub messages.

## Configure the **Product quality** scenario in Supply Chain Management

The **Product quality** scenario generates a notification if an attribute of an item is outside a specified range. For example, a sensor could send the weight of each item to IoT Hub. In Supply Chain Management, a notification would be generated if the item was too heavy or too light.

The scenario has these dependencies:

+ A Production Order must be running on a mapped machine and producing a product with a mapped batch attribute for an alert to be triggered.
+ A signal representing the batch attribute must be sent to the IoT Hub with a unique property name.
+ A Unix milliseconds timestamp property must be present in the IoT Hub message.

## Configure the **Production delays** scenario in Supply Chain Management

The **Production delays** scenario generates a notification if the production throughput falls below a threshold value. In this scenario, a **PartOut** signal is sent to IoT Hub for each item produced. In Supply Chain Management, the order delay is calculated based on how long the production order is scheduled to run, how many items should be produced, how long the job has been running, and how many **PartOut** signals are received. A delay notification would be generated if the number of the **PartOut** signals for the job falls below the threshold value of the expected value.

The scenario has these dependencies:

+ A Production Order must be running on a mapped machine for an alert to be triggered.
+ A signal representing a mapped machine's part out signal must be sent to the IoT Hub with a unique property name.
+ A Unix milliseconds timestamp property must be present in the IoT Hub message.

## How to disable a scenario

To disable a scenario, follow these steps:

1. In Supply Chain Management, navigate to **Production control \> Setup \> IoT Intelligence \> Scenario management**.
2. Click **Configure** on the scenario.
3. Click **Next** to get to the last wizard tab.
4. Toggle the slider to disable the scenario.