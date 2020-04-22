---
# required metadata

title: IoT Intelligence core insights
description: This topic describes IoT Intelligence core insights and describes how to setup and monitor a scenario.
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

# IoT intelligence core insights

[!include [banner](../../includes/banner.md)]


Internet of things (IoT) Intelligence supports the following core insights and action scenarios:

+ **Delayed orders** : Provides notification services and actions for managing delayed production orders. Displays impacted operations. Provides users with the ability to define order-delay metrics for combinations of resources and products, and notifies users when exceptions to these thresholds occur. Enables users to take relevant business actions for delayed orders, including the ability to view impact or create a maintenance request.
+ **Equipment down**: Provides notification services and actions for managing equipment-down scenarios. Displays impacted operations. Provides users with the ability to define metrics for machine-down thresholds and notifies users when an exception to these thresholds occurs. Enables users to take relevant business actions for delayed orders, including the ability to view impact or create a maintenance work order.
+ **Quality anomaly**: Provides notification services and actions for managing quality anomalies. Provides users with the ability to define quality attributes for products and get notified when exceptions to these attributes occur.

You can setup and configure core insights without writing any code. 

In this topic, you will configure the scenario to generate a message in Supply Chain Management when a machine goes down. This is the **Equipment down** scenario.

## Overview of setup process

+ Configure your devices to send telemetry to IoT Hub, and define the JSON message format. For more information, see [Azure IoT Hub Documentation](https://docs.microsoft.com/azure/iot-hub/).
+ Create a OneBox environment, and give the appropriate SQL users access to environment for IoT Intelligence.
+ Setup the IoT scenario in Supply Chain Management, including enabling the feature flag, configuring the schema, mapping the signals to Suppy Chain Management sources, and enabling the scenario.

## Azure Resource setup

1. Verify that **Microsoft Dynamics ERP Microservices** first-party app Id is inside your tenant.
    1. In Azure, navigate to Azure Active Directory.
    2. Navigate to **Enterprise applications**.
    3. In the **Application type** dropdown, select **All applications**.
    4. In the search box, search for **Microsoft Dynamics ERP Microservices**.
    5. Verify that **Microsoft Dynamics ERP Microservices** is in the list. There are other applications with similar names, make sure you find the right one. The application Id starts with **0cdb**.
    6. If the application is not in the list, you need to add it to your tenant. To add it:
        1. Click the tool bar icon to open the Cloud shell.
        2. You can verify that the module is not installed by running the command `Get-InstalledModule -Name "AzureAD"`. You'll get an error, because it doesn't exist.
        3. Run the command `Install-Module AzureAD`. Enter `Y` to install the module.
        4. To verify that the module is installed, run the command `Get-InstalledModule -Name "AzureAD"`.
        5. Run the command `Connect-AzureAD -Confirm` to run the authentication.
        6. Run the command `New-AzureADServicePrincipal -AppId 0cdb527f-a8d1-4bf8-9436-b352c68682b2`.
        7. Now you can rerun steps 1 through 5 to verify that the app Id is inside your tenant.
2. Create a key vault resource.
    1. In Azure, create a resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Key vault**. Click **Create**.
    4. On the **Create key vault page**, enter a name in the **Key vault name** textbox.
    5. Leave the rest of default values, and click **Review + create**.
    6. Click **Create**. The key vault is created in the background.
3. Create an IoT Hub resource.
    1. On the **Your deployment is underway** page, click the link for your resource group to navigate back to your resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Iot Hub**. Click **Create**.
    4. Enter a name in the **IoT hub name** textbox.
    5. Leave the rest of default values, and click **Review + create**.
    6. Click **Create**. The IoT hub is created in the background.
4. Create a Redis cache resource.
    1. On the **Your deployment is underway** page, click the link for your resource group to navigate back to your resource group.
    2. Click **Add**.
    3. On the **New** page, in the search box, enter **Azure Cache for Redis**. Click **Create**.
    4. Enter a name in the **DNS name** textbox.
    5. Leave the rest of default values, and click **Create**.
    6. The Redis cache is created in the background.



+ Add the **Microsoft Dynamics Microservice ERP** **First Party App Id** to the customer tenant.
+ Setup an Azure Redis Cache for IoT Intelligence.
    + Show where the Redis Cache connection string is located.        
    + Call out that it is recommendation that only one Redis Cache is used per environment.
+ Setup an Azure IoT Hub for IoT Intelligence.
    + Add the IoT Intelligence consumer groups.       
    + Show where the Event Hub connection string is located.     
    + Call out that it is recommendation that only one IoT Hub is used per environment
        
### How to setup an Azure Key Vault for IoT Intelligence

+ Give the first party app-id the correct Access Policies to the key vault.     
+ Show where the Key Vault Uri is located.
+ Show where the Key Vault ADD tenant id is located.
+ Add the IoT Hub connection string to the key vault.      
+ Add the Redis Cache connection string to the key vault.    
+ Show where the Key Vault secret names are located.  
+ Call out that any time one of the connection strings is updated the secret values will need to be updated

Notes:

+ You must add the Microsoft Dynamics microservice, first party app ID.
+ You must give the LCS environment access to the key vault.


## LCS Environment setup 

1. Open LCS.
2. Navigate to the environment details.
3. Scroll down to an environment.
4. In the Add-in section, click **Install a new add-in** to populate the list of addins that have been enabled for the environment.
5. Click on the **IoT Intelligence** add-in.
6. Provide the details of your IoT hub and Redis cache. You can find the values that you need in the key vault you created in the [name of section](#link to section).

    1. In Azure, open the key vault you previously created, and copy the DNS name. The DNS name servers as the key vault identifer.
    2. In the **Setup add-in** dialog, paste the value into the fields for **IoT Hub** and **Redis cache**.
    3. In Azure, open the key vault and click the Secrets tab. Copy the secret for ?? and copy it to the ??? field in the **Setup add-in** dialog.
    4. In Azure, copy the secret for the **Redis ???** and copy it to **Redis cache endpoint secret name** in the **Setup add-in** dialog.

7. Click **Install**. 
8. A dialog shows up that says **Add-in has been successfully triggered for installation**. Click **OK**.

## Configure the **Equipment downtime** scenario in Supply Chain Management

The **Equipment downtime** scenario maps a machine to a **PartOut** signal and defines an alert threshold. The machine is monitored only when the machine is selected for the scenario and is set to running in Supply Chain Management. If the time since the machine’s last received Part Out signal is greater than the alert threshold, then a **Machine down** notification is triggered. If the machine is still running, when the next **PartOut** signal is received a **Machine up** notification is triggered. If a machine stays down for 30 mins a new **Machine down** notification is triggered.

The **Equipment downtime** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered. 

1. Log into the Finance and Operations apps.
2. Enbale the IoT Intelligence feature flag. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
4. Navigate to **Production control**.
5. Navigate to **Setup \> IoT Intelligence \> Scenario parameters**. Enter the Redis connection string. *Insert instructions here on how to get this value. It appears not to be in the key vault.*
6. Navigate to **Setup \> IoT Intelligence \> Scenario management**.
7. Click **Configure** on the **Equipment downtime** tile. This starts the configuration wizard for the **Equipment sensor schema definition**. The goal here is to setup the schema in Supply Chain Management to match the JSON format that you created when you setup the message in Azure. In this example, the message payload contains a batch of messages with this format:

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

8. Add a row to the table. 

    1. Set the **Schema name** to **id**.
    2. Set the **Schema path** to **/payload[\*]/id**.
    3. Set the **Description** to **Message id**.

9. Add a row to the table. 

    1. Set the **Schema name** to **timestamp**.
    2. Set the **Schema path** to **/payload[\*]/timestamp**.
    3. Set the **Description** to **Message timestamp**.

10. Add a row to the table. 

    1. Set the **Schema name** to **value**.
    2. Set the **Schema path** to **/payload[\*]/value**.
    3. Set the **Description** to **Message value**.

    You don't need to define all the properties in the message, only the ones that you need. In this example, you did not create a row for **Root timestamp**. The path for **Root timestamp** would be **/timestamp**.
  
12. Click **Next** to go to the **Equipment sensor schema map** page.
13. In the row for **Equipment resource id** set the **Schema name** to **id**. The valid values are displayed in a dropdown table.
14. In the row for **UTC time** set the **Schema name** to **Timestamp**. The valid values are displayed in a dropdown table.
15. In the row for **Part produced signal** set the **Schema name** to **value**. The valid values are displayed in a dropdown table.
16. Click **Next** for the **Equipment resource id configuration** page.
17. In this step, you map the machine names to ??? in the Supply Chain Management. 

    1. For the **Schema path** - **/[payload]\*/id**, in the **Signal Data Values** table, add a new row, and enter **IoTInt.Machine1225.PartOut** in the **Value** column. The value **IoTInt.Machine1225.PartOut** comes from the **id** property in the message JSON.
    2. In the **Business Record Mapping** table, click **New**. The default value for the **Business record type** is autopopulated, and you don't need to change it. 
    3. In the **Business record** column, select **Machine1225**. 
    4. Click **Save**. 
    5. Repeat these steps, adding a new business record mapping for **Machine1226**. You can map multiple **id** values from the messages to a single record in Supply Chain Management, but you can't map a single **id** value to multiple records in Supply Chain Management.

18. After you have entered all the rows you need in the **Business Record Mapping** table, use the **Selected** column to choose when machines you want to process. You do not have to process information that comes from all the machines.
19. Click **Next** to go to the **Part produced signal configuration** page.
20. In the **Signal Data Values** table, add a row, and set **Value** to **True**. The value **True** comes from the **value** property in the message JSON. You can add as many values as you need for your scenario. Click **Save**.
21. Click **Next** to go to the **Equipment downtime threshold** page. The values for downtime threshold are already mapped according to the machine id. In this step, you define a threshold to determine if a machine is down. For example, if you set the threshold to 10, Supply Chain Management generates a notification if there is no PartOut message from a machine after 10 minutes. 
22. Click **Next** to go to the **Enable scenario** page. Click the slider to enable the scenario.
23. Click **Finish**.

At this point, the pipeline is complete and the messages are processed automatically.


## Configure the **Quality** scenario in Supply Chain Management

The **Quality** scenario generates a notification if an attribute of an item is outside a speicified range. For example, a sensor could send the weight of each item to IoT Hub. In Suppy Chain Management, a notification would be generated if the item was too heavy or too light. 

The **Quality** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered. 

## Configure the **Production Order Delay** scenario in Supply Chain Management

The **Production Order Delay** scenario generates a notification if the production throughput falls below a threshold value. In this scenario, a **PartOut** signal is sent to IoT Hub for each item produced. In Supply Chain Management, the order delay is calculated based on how long the production order is scheduled to run, how many items should be be produced, how long the job has been running, and how many **PartOut** signals are received. A delay notification would be generated if the number of the **PartOut** signals for the job falls below the threshold value of the expected value.

The **Production Order Delay** scenario has these dependencies:

+ Production Order must be scheduled and running on the machine for an alert to be triggered. 

## How to view the monitors in Supply Chain Management

There are several ways to view the messages processed in the scenario in Supply Chain Management:

+ **Production control \> Inquiries and reports \> IoT Intelligence \> Notifications**. Here you can see the list of unresolved notifications. A notification is generated when a machine is down.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Closed notifications**. Here you can see the notifications that have been resolved.
+ **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**. Here you can see a times series graph for each machine you are processing.
+ **Production control \> Manufacturing execution \> Resource status**. You can configure this page to track specific machines using the **Configure** dialog. As messages are processed a graph is produced showing the parts produced. This page displays an error message if a machine is down, and there are buttons to resolve or dismiss the error message.
+ **Production control \> Setup \> IoT Intelligence \> Scenario parameters**. Click **Equipment downtime** to see all the machines that are available.

## How to disable a scenario

In Supply Chain Management, run the **Equipment downtime** configuration wizard, and disable the scenario.

## How to uninstall the addin

1. In Supply Chain Management, run the **Equipment downtime** configuration wizard, and disable the scenario.
2. In LCS, uninstall the addin.

## Modify a running IoT Intelligence scenario        
    + List what can and cannot be updated while the scenario is running


## IoT Intelligence Metric setup

1. Copy the Redis cache connection string:
    1. In Azure, go to the Redis cache.
    2. Navigate to **Settings** \> **Access keys**.
    3. Copy the **Primary connection string** field.
2. In Supply Chain Management, navigate to **Production control \> Setup \> IoT Intelligence \> Scenario parameters.**  
    1. On the **Scenario parameters** page, in the **Time series** tab, copy the connection string into the textbox for **Redis metric store connection string**. This allows the metrics from IoT Hub to be visualized in Supply Chain Management.
3. Navigate to **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**.
    1. On the **Metric keys** page, click **Update**.
    2. In the **Update metric keys** dialog that appears, the value in the dropdown is **Run in the background**. Click **OK**.
    3. All the metric keys in the Redis cache are retrieved, and added to the **Metric keys** list.
4. Navigate to **Production control \> Manufacturing execution \> Resource Status**. On the **Resource status** page, enter the values in the **Configure** pane.
    1. Select an item to monitor from the **Resource** list.
    2. Select the edit button for **Time series 1**.
    3. Select a metric from the table on the **Select time series** dialog. (You can also use the **Update metric keys** link to update the metric keys from this dialog.)
    4. Click **OK** to return to the **Configure** dialog.
    5. Enter a display name.
    6. Select a time frame for **Show data from**.
    7. Click OK.
5. The graph is displayed.
    
To delete a metric key - ???


## Simulation options

TODO: Look for links in Azure docs.

+ Setup IoT solutions to simulate factory machine signals
+ Setup a MxChip to simulate a factory machine signal



