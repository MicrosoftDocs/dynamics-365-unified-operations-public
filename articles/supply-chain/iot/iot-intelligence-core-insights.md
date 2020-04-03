---
# required metadata

title: IoT intelligence core insights
description: This topic explains how to calculate item forecast in Asset Management.
author: 
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

## Azure Resource setup
    + How to add the ‘Microsoft Dynamics Microservice ERP’ First Party App Id to the customer tenant
    + How to setup an Azure Redis Cache for IoT Intelligence        
        + Show where the Redis Cache connection string is located        
        + Call out that it is recommendation that only one Redis Cache is used per environment
    + How to setup an Azure IoT Hub for IoT Intelligence        
        + Provide the steps to add the IoT Intelligence consumer groups        
        + Show where the Event Hub connection string is located        
        + Call out that it is recommendation that only one IoT Hub is used per environment
        
### How to setup an Azure Key Vault for IoT Intelligence        
+ Provide the steps on how to give the first party app-id the correct Access Policies to the key vault        
+ Show where the Key Vault Uri is located        
+ Show where the Key Vault ADD tenant id is located        
+ Provide the steps on how to add the IoT Hub connection string to the key vault        
+ Provide the steps on how to add the Redis Cache connection string to the key vault        
+ Show where the Key Vault secret names are located        
+ Call out that any time one of the connection strings is updated the secret values will need to be updated

Notes:
Need to add the Microsoft Dynamics microservice, first party app ID.
Give the LCS environment access to the key vault.



## OneBox Environment setup
    + How to whitelist a OneBox Environment for IoT Intelligence access        
        + Provide the steps on how to create the Network Security Group Inbound SQL Port rule        
        + Provide the steps on how to create the Load Balancer Inbound NAT rule        
        + Provide the steps on how to open up the VMs Firewall for the SQL port        
        + Provide the steps on how to verify the VM’s ‘PC Discoverable setting’ is turned off
    + How to add the correct SQL users to the OneBox environment for IoT Intelligence access

## LCS Environment setup 
    + How to install the IoT Intelligence add-in for an environment        
        + Provide the steps to locate the LCS environment add-in section        
        + Provide the steps to select the IoT Intelligence add-in        
        + Give the details on where each input property can be found (Tenant Id, Key Vault Uris and Secret names)
    + How to uninstall the IoT Intelligence add-in for an environment        
        + Show where in LCS the IoT Intelligence add-in can be uninstalled

1. Open LCS.
2. Navigate to the environment details.
3. Scroll down to an environment.
4. In the Add-in section, click **Install a new add-in** to populate the list of addin's that have been enabled for the environment.
5. Click on the **IoT Intelligence** add-in.
6. Enter the connection strings for your IoT hub and Redis cache. You can find the values that you need in the key vault you created in the [name of section](#link to section).
    a. In Azure, open the key vault you previously created, and copy the DNS name. The DNS name servers as the key vault identifer.
    b. In the **Setup add-in** dialog, copy the value into the fields for **IoT Hub** and **Redis cache**.
    c. In Azure, open the key vault and click the Secrets tab. Copy the secret for ?? and copy it to teh ??? field in the **Setup add-in** dialog.
    d. In Azure, copy the secret for the **Redis ???** and copy it to **Redis cache endpoint secret name** in the **Setup add-in** dialog.
7. Click **Install**. 
8. A dialog shows up that says **Add-in has been successfully triggered for installation**. Click **OK**.
That's it for the LCS portion.

## IoT Intelligence Scenario setup
    + How to enable the IoT Intelligence Feature flag
    + How to define the IoT Hub message schemas in the IoT Intelligence wizard        
        + Call out the JSON message schema dependency         
        + Provide examples on how this message schema translates into this schema path        
        + Call out that multiple messages schemas can be defined and are shared
    + How to select the message schema paths for the IoT Intelligence scenario        
        + Call out the dependency on the UNIX milliseconds timestamp        
        + Call out that the message paths need be defined on same IoT Hub message        
        + Provide examples of how one template can be filled out
    + How to map your IoT Hub signals to the Dynamics resources        
        + Describe the importance on the signal mapping and what it represents        
        + Describe the signal selection process and what it represents
    + How to enable the IoT Intelligence scenario
    + How to disable the IoT Intelligence scenario
    + How to modify a running IoT Intelligence scenario        
        + List what can and cannot be updated while the scenario is running

## IoT Intelligence Metric setup
    + How to setup Dynamics to view the IoT Hub metrics        
        + Provide the steps to add the Redis Connection string to the Scenario Parameters form        
        + Call out that any time the Redis connection string is updated the parameter form value will need to be updated
    + How to configure the Resource Status displayed metrics
    + How to update the metric keys
    + How to delete their metric keys 

## IoT Intelligence Scenario data dependencies
    + How does the Machine Status scenario determine when a machine is up or down        
        + Describe how a machine is tied to a Part Out signal and an alert threshold. The machine is only monitored when the machine is selected for the scenario and is set to running in Dynamics. If the time since the machine’s last received Part Out signal is greater than the alert threshold a Machine down notification is triggered. If the machine is still running,  when the next Part Out signal is received a Machine up notification is triggered. If a machine stays down for 30 mins a new Machine down notification is triggered.
    + How does the Quality scenario determine if a attribute is valid or not        
        + Describe how a sensor reading is tied to a machine and a batch attribute. The sensor reading is only monitored when the signal is selected for the scenario, the sensor’s machine is running and the machine is scheduled to produce a product that has the batch attribute defined. While the machine is running, every time the signal crosses the batch attribute’s min max range a quality notification will be triggered.
    + How does the Production Order Delay scenario determine if an order is delayed or not        
        + Describe how a machine is tied to a Part Out signal and a route threshold. A Production order is only monitored when the producing machine is selected for the scenario and is set to running in Dynamics. The order delay is calculated based on how long the production order is scheduled to run, how many items should be be produced, how long the job has been running and how many Part Out signals have been received. A production order delay notification is created, if the number of the Part Out signals for the job falls below the threshold value of the expected linear output rate.

## Simulation options
    + How to setup IoT solutions to simulate factory machine signals
    + How to setup a MxChip to simulate a factory machine signal



