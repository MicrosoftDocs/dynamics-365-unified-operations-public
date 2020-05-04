---
# required metadata

title: Schema formats for IoT Hub messages
description: This topic describes how you should design your message schema for use in IoT Intelligence.
author: robinarh
manager: AnnBe
ms.date: 04/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-04-25
ms.dyn365.ops.version: AX 7.0.0
---

# Message schema formats for IoT Hub

[!include [banner](../../includes/banner.md)]

This topic describes how you should design your message schema for use in IoT Intelligence.

## Message requirements

There are a few rules that apply to monitoring messages in IoT Intelligence.

+ A message is tracked only if it contains all the properties defined in the scenario setup. For example, if you define **id**, **timestamp**, and **value** properties then this message is monitored:

    ```json
        {
            "id": "IoTInt.Machine1225.PartOut",
            "timestamp": 1576016821614,
            "value": True
        }
    ```

    This message is not monitored, because the **value** property is missing:

    ```json
        {
            "id": "IoTInt.Machine1225.PartOut",
            "timestamp": 1576016821614,
        }
    ```

+ A Unix milliseconds timestamp property must be present in the IoT hub message.

+ IoT Intelligence ignores properties in the message that are not defined in the scenario configuration. For example, if you define **id**, **timestamp**, and **value** properties, then IoT Intelligence will monitor all of these messages:

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

+ IoT Intelligence silently ignores messages is does not monitor.

+ You can define different schemas for different IoT Intelligence scenarios, or different schemas for different IoT Hub tasks unrelated to IoT Intelligence.

## Id-value pair schema

Using an id-value pair is a common pattern for IoT Intelligence message schemas. By using an id-value pair, your message schema is the same across all the scenarios. For example, a message for the **Equipment downtime** or **Production delays** scenario might look like this:

```json
{
    "id": "IoTInt.Machine1225.PartOut",
    "timestamp": 1576016821614,
    "value": True
}
```

A message for the **Product quality** scenario might look like this:
```json
{
    "id": "IoTInt.Machine1225.Temperature",
    "timestamp": 1576016821614,
    "value": 105
}
```

Both contain **id** and **value** properties. The **id** values can be mapped in the **Signal Data Values** table during scenario setup. For the **Equipment downtime** scenario, you would map the **IoTInt.Machine1225.PartOut** value. For the **Product quality** scenario, you would map the **IoTInt.Machine1225.Temperature** value.

For more information, see [Azure IoT Hub Documentation](https://docs.microsoft.com/azure/iot-hub/).
