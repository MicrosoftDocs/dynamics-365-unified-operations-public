---
# required metadata

title: Schema formats for IoT Hub messages
description: This topic explains how you should design a message schema that you can use in IoT Intelligence.
author: johanhoffmann
ms.date: 04/25/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2020-04-25
ms.dyn365.ops.version: AX 7.0.0
---

# Schema formats for IoT Hub messages

[!include [banner](../../includes/banner.md)]

This topic explains how you should design a message schema that you can use in IoT Intelligence.

## Message requirements

The following rules apply to the monitoring of messages in IoT Intelligence:

+ Message schemas must be in JavaScript Object Notation (JSON) format.
+ A UNIX **timestamp** property, where the value is expressed in milliseconds (ms), must be present in the Microsoft Azure IoT Hub message.
+ A message is tracked only if it contains all the properties that are defined in the scenario setup. For example, if you define **id**, **timestamp**, and **value** properties, the following message is monitored.

    ```json
    {
        "id": "IoTInt.Machine1225.PartOut",
        "timestamp": 1576016821614,
        "value": True
    }
    ```

    This message isn't monitored, because the **value** property is missing.

    ```json
    {
        "id": "IoTInt.Machine1225.PartOut",
        "timestamp": 1576016821614,
    }
    ```

+ IoT Intelligence ignores properties in the message that aren't defined in the scenario configuration. For example, if you define **id**, **timestamp**, and **value** properties, IoT Intelligence will monitor all the following messages.

    ```json
    {
        "id": "IoTInt.Machine1225.PartOut",
        "timestamp": 1576016821614,
        "value": True
    },
    {
        "id": "IoTInt.Machine1225.PartOut",
        "timestamp": 1576016821614,
        "value": True,
        "machine" : "Machine1225",
    },
    {
        "id": "IoTInt.Machine1225.PartOut",
        "timestamp": 1576016821614,
        "value": True,
         "activity": "PartOut"
    },
    ```

+ IoT Intelligence silently ignores messages that don't match the scenario configuration criteria.
+ You can define and use multiple types of message schemas.
+ Not every type of message schema must be defined. Only schemas that will be used for the IoT Intelligence scenarios must be defined.

## Id-value pair schema

An id-value pair is a common pattern for IoT Intelligence message schemas. By using an id-value pair, you ensure that your message schema is the same across all the scenarios. For example, here is a message for the **Equipment downtime** or **Production delays** scenario.

```json
{
    "id": "IoTInt.Machine1225.PartOut",
    "timestamp": 1576016821614,
    "value": True
}
```

Here is a message for the **Product quality** scenario.

```json
{
    "id": "IoTInt.Machine1225.Temperature",
    "timestamp": 1576016821614,
    "value": 105
}
```

Both the preceding messages contain **id** and **value** properties. The **id** values can be mapped in the **Signal Data Values** table during scenario setup. For the **Equipment downtime** scenario, you will map the **IoTInt.Machine1225.PartOut** value. For the **Product quality** scenario, you will map the **IoTInt.Machine1225.Temperature** value.

For more information, see [Azure IoT Hub Documentation](/azure/iot-hub/).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]