---
# required metadata

title: Scenario setup for IoT Intelligence core insights
description: This topic describes how to configure a scenario in Supply Chain Management for IoT Intelligence core insights.
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
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Scenario setup for IoT Intelligence core insights

[!include [banner](../../includes/banner.md)]

This topic describes how to configure a scenario in Supply Chain Management for IoT Intelligence core insights.

In this topic, you will configure the **Equipment down** scenario to generate a message in Supply Chain Management when a machine goes down.

, including enabling the feature flag, configuring the schema, mapping the signals to Supply Chain Management sources, and enabling the scenario.


## Configure the **Equipment downtime** scenario in Supply Chain Management

The **Equipment downtime** scenario maps a machine to a **PartOut** signal and defines an alert threshold. The machine is monitored only when the machine is selected for the scenario and is set to running in Supply Chain Management. If the time since the machine’s last received Part Out signal is greater than the alert threshold, then a **Machine down** notification is triggered. If the machine is still running, when the next **PartOut** signal is received a **Machine up** notification is triggered. If a machine stays down for 30 mins a new **Machine down** notification is triggered.

The **Equipment downtime** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered.

1. Log into the Finance and Operations apps.
2. Enable the IoT Intelligence feature flag. For more information, see [Feature management overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
3. Navigate to **Production control**.
4. Navigate to **Setup \> IoT Intelligence \> Scenario parameters**. Enter the Redis connection string. *Insert instructions here on how to get this value. It appears not to be in the key vault.*
5. Navigate to **Setup \> IoT Intelligence \> Scenario management**.
6. Click **Configure** on the **Equipment downtime** tile. The configuration wizard starts with the **Equipment sensor schema definition** page. The goal here is to setup the schema in Supply Chain Management to match the JSON format that you created when you configured the message in Azure. In this example, the message payload contains a batch of messages with this format:

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
    2. Set the **Schema path** to **/payload[\*]/ID**.
    3. Set the **Description** to **Message ID**.

8. Add a row to the table. 

    1. Set the **Schema name** to **timestamp**.
    2. Set the **Schema path** to **/payload[\*]/timestamp**.
    3. Set the **Description** to **Message timestamp**.

9. Add a row to the table. 

    1. Set the **Schema name** to **value**.
    2. Set the **Schema path** to **/payload[\*]/value**.
    3. Set the **Description** to **Message value**.

    You don't need to define all the properties in the message, only the ones that you need. In this example, you did not create a row for **Root timestamp**. The path for **Root timestamp** would be **/timestamp**.
  
10. Click **Next** to go to the **Equipment sensor schema map** page.
11. In the row for **Equipment resource ID** set the **Schema name** to **ID**. The valid values are displayed in a dropdown table.
12. In the row for **UTC time** set the **Schema name** to **Timestamp**. The valid values are displayed in a dropdown table.
13. In the row for **Part produced signal** set the **Schema name** to **value**. The valid values are displayed in a dropdown table.
14. Click **Next** for the **Equipment resource ID configuration** page.
15. In this step, you map the machine names to ??? in the Supply Chain Management. 

    1. For the **Schema path** - **/[payload]\*/ID**, in the **Signal Data Values** table, add a new row, and enter **IoTInt.Machine1225.PartOut** in the **Value** column. The value **IoTInt.Machine1225.PartOut** comes from the **ID** property in the message JSON.
    2. In the **Business Record Mapping** table, click **New**. The default value for the **Business record type** is autopopulated, and you don't need to change it. 
    3. In the **Business record** column, select **Machine1225**. 
    4. Click **Save**. 
    5. Repeat these steps, adding a new business record mapping for **Machine1226**. You can map multiple **ID** values from the messages to a single record in Supply Chain Management, but you can't map a single **ID** value to multiple records in Supply Chain Management.

18. After you have entered all the rows you need in the **Business Record Mapping** table, use the **Selected** column to choose when machines you want to process. You do not have to process information that comes from all the machines.
19. Click **Next** to go to the **Part produced signal configuration** page.
20. In the **Signal Data Values** table, add a row, and set **Value** to **True**. The value **True** comes from the **value** property in the message JSON. You can add as many values as you need for your scenario. Click **Save**.
21. Click **Next** to go to the **Equipment downtime threshold** page. The values for downtime threshold are already mapped according to the machine id. In this step, you define a threshold to determine if a machine is down. For example, if you set the threshold to 10, Supply Chain Management generates a notification if there is no PartOut message from a machine after 10 minutes. 
22. Click **Next** to go to the **Enable scenario** page. Click the slider to enable the scenario.
23. Click **Finish**.

At this point, the pipeline is complete and the messages are processed automatically.


## Configure the **Quality** scenario in Supply Chain Management

The **Quality** scenario generates a notification if an attribute of an item is outside a specified range. For example, a sensor could send the weight of each item to IoT Hub. In Supply Chain Management, a notification would be generated if the item was too heavy or too light. 

The **Quality** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered. 

## Configure the **Production Order Delay** scenario in Supply Chain Management

The **Production Order Delay** scenario generates a notification if the production throughput falls below a threshold value. In this scenario, a **PartOut** signal is sent to IoT Hub for each item produced. In Supply Chain Management, the order delay is calculated based on how long the production order is scheduled to run, how many items should be produced, how long the job has been running, and how many **PartOut** signals are received. A delay notification would be generated if the number of the **PartOut** signals for the job falls below the threshold value of the expected value.

The **Production Order Delay** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered. 

## How to view the monitors in Supply Chain Management

There are several ways to view the messages processed in the scenario in Supply Chain Management:

+ **Production control \> Inquiries and reports \> IoT Intelligence \> Notifications**. Here you can see the list of unresolved notifications. A notification is generated when a machine is down.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Closed notifications**. Here you can see the notifications that have been resolved.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**. Here you can see a times series graph for each machine you are processing.
+ **Production control \> Manufacturing execution \> Resource status**. You can configure this page to track specific machines using the **Configure** dialog. As messages are processed a graph is produced showing the parts produced. This page displays an error message if a machine is down, and there are buttons to resolve or dismiss the error message.
+ **Production control \> Setup \> IoT Intelligence \> Scenario parameters**. Click **Equipment downtime** to see all the machines that are available.



