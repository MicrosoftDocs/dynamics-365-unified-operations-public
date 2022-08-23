---
title: Set up a simulated sensor for testing
description: This article describes how to set up a simulator that you can use to test Sensor Data Intelligence without installing any actual physical sensors.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Set up a simulated sensor for testing

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

If you want to test Sensor Data Intelligence without installing any actual physical sensors, you can use the *Raspberry PI Azure IoT Online Simulator* service to emulate sensor signals and send them to your IoT solution on Azure. For more information about the simulator, see [Connect Raspberry Pi online simulator to Azure IoT Hub (Node.js)](/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started).

## Create a device in Azure IoT Hub

You must start by setting up a device to authenticate the sensor signals to the Azure IoT Hub. To create the device, use the following steps:

1. In Azure, go to the resource list for the resource group you created for use with Sensor Data Intelligence (see also [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md)).
1. In the list of resources, find the record with **Type** *IoT Hub* and select its name in the **Name** column to open the details page for that resource.
1. On the left navigation pane, select **Devices** to open the **Devices** page.
1. Select **Add device** to open the **Create a device** page.
1. Make the following settings:
    - **Device ID** – Enter a name for the new device (for example, *My-IoT-Device*).
    - **Authentication type** – Select *Symmetric keys*.
    - **Auto-generate keys** – Select the check box.
    - **Connect this device to an IoT hub** – Select *Enable*.

1. Select **Save** to return to the **Devices** page. If you don't see your new device in the list, reload the page.
1. Find your new device in the list and select its name in the **Device ID** column to go to the detailed page for the device.
1. Copy the value provided for **Primary connection string** (for example, by selecting the **Copy to clipboard** button). You will need this value later when you set up the Raspberry Pi IoT simulator for emulating sensor signals, so consider pasting it in a temporary text file for now.

## Add the Azure connection string to the Raspberry Pi IoT simulator

Follow these steps to add the connection string from the device in Azure IoT Hub to the script in the Raspberry service.

1. Open the [Raspberry Pi IoT simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/).
1. In the code editor pane find the line with the following command:

    `const connectionString = '[Your IoT hub device connection string]';`

1. Remove the help text from the line (including the square brackets) and replace it with the **Primary connection string** you copied in the previous section. The result should resemble the following example:

    `const connectionString = 'HostName=XXX;DeviceId=YYY;SharedAccessKey=ZZZ';`

## Add sensor IDs and values to the payload in the Raspberry Pi IoT simulator

Now you must set up the Raspberry Pi IoT simulator with simulated sensors and the values they will send as payloads.

In the code editor of the Raspberry Pi IoT simulator, find the `getMessage` function and edit it to match the following code (the sensors are set up in the `cb()` lines):

```cpp
function getMessage(cb) {
    messageId++;
    sensor.readSensorData()
    .then(function (data) {
        cb(JSON.stringify({ value: 1, sensorId: 'MachineStatus' }), false);
        cb(JSON.stringify({ value: 70, sensorId: 'Quality' }), false);
        cb(JSON.stringify({ value: 1, sensorId: 'AssetMaintenance' }), false);
        cb(JSON.stringify({ value: 1, sensorId: 'ProductionDelay' }), false);
        cb(JSON.stringify({ value: 20, sensorId: 'AssetDowntime' }), false);
    })
    .catch(function (err) {
        console.error('Failed to read out sensor data: ' + err);
    });
}
```

> [!IMPORTANT]
> The sensors IDs defined here in the code editor for the Raspberry Pi IoT simulator must be identical to the sensor IDs you will specify later for the scenarios in Supply Chain Management. The example provided here uses human-readable IDs, but in an actual scenario, these will be GUID values provided by the sensor manufacturer. The human-readable IDs suggested in the sample code shown here are also used in the example scenarios provided in [The product quality scenario](sdi-scenario-product-quality.md), [The asset maintenance scenario](sdi-scenario-asset-maintenance.md), [The production delays scenario](sdi-scenario-production-delays.md), and [The machine status scenario](sdi-scenario-equipment-downtime.md)). If you will work through those scenarios, then use this code.

## Edit the time interval for sending sensor signals

Now you must set the time intervals at which the Raspberry Pi IoT simulator should send the emulated sensor signals.

In the code editor of the Raspberry Pi IoT simulator, find the following function invocation:

`setInterval(sendMessage, **2000**);`

This is the default setting, which sends a sensor signal every 2000 milliseconds (2 seconds). You can adjust the value if you want to use a different one.

## Run the Raspberry Pi IoT simulator

Select **Run** to start the simulator and begin sending simulated sensor data.
