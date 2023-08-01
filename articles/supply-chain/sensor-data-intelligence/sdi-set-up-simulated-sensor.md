---
title: Set up a simulated sensor for testing
description: This article describes how to set up a simulator that you can use to test Sensor Data Intelligence without installing any physical sensors.
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
<!-- KFM: Preview until further notice -->

If you want to test Sensor Data Intelligence without installing any physical sensors, you can use the *Raspberry PI Azure IoT Online Simulator* service to emulate sensor signals and send them to your Internet of Things (IoT) solution on Microsoft Azure. For more information about the simulator, see [Connect Raspberry Pi online simulator to Azure IoT Hub (Node.js)](/azure/iot-hub/iot-hub-raspberry-pi-web-simulator-get-started).

## Video instructions

The following video shows how to set up a simulated sensor for testing. The remaining sections in this article provide the same instructions in a text-based format.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE588g6]

## Create a device in Azure IoT Hub

You must first set up a device to authenticate the sensor signals to the Azure IoT Hub.

1. In Azure, go to the list of resources for the resource group that you created for use with Sensor Data Intelligence. (For more information, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).)
1. In the resource list, find the record where the **Type** field is set to *IoT Hub*. In the **Name** column, select the name to open the details page for the resource.
1. In the left navigation pane, select **Devices**.
1. On the **Devices** page, select **Add device**.
1. On the **Create a device** page, set the following fields:

    - **Device ID** – Enter a name for the new device (for example, *My-IoT-Device*).
    - **Authentication type** – Select *Symmetric keys*.
    - **Auto-generate keys** – Select this checkbox.
    - **Connect this device to an IoT hub** – Select *Enable*.

1. Select **Save** to return to the **Devices** page.
1. Find the new device in the list. In the **Device ID** column, select the name to open the details page for the device. If you don't see the new device in the list, refresh the page.
1. Copy the **Primary connection string** value (for example, by selecting the **Copy to clipboard** button). You will need this value later when you set up the Raspberry Pi IoT simulator to emulate sensor signals. Therefore, consider pasting it into a text file for now.

## Add the Azure connection string to the Raspberry Pi IoT simulator

Follow these steps to add the connection string from the device in Azure IoT Hub to the script in the Raspberry service.

1. Open the [Raspberry Pi IoT simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/).
1. In the code editor pane, find the line that contains the following command.

    `const connectionString = '[Your IoT hub device connection string]';`

1. Replace the help text, including the brackets, with the **Primary connection string** value that you copied in the previous section. The result should resemble the following example.

    `const connectionString = 'HostName=XXX;DeviceId=YYY;SharedAccessKey=ZZZ';`

## Add sensor IDs and values to the payload in the Raspberry Pi IoT simulator

You must now set up the Raspberry Pi IoT simulator with simulated sensors and the values that they will send as payloads.

- In the code editor of the Raspberry Pi IoT simulator, find the `getMessage` function, and edit it so that it matches the following code. (The sensors are set up in the `cb()` lines.)

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
            cb(JSON.stringify({ value: 5, sensorId: 'AnomalyDetector' }), false);
        })
        .catch(function (err) {
            console.error('Failed to read out sensor data: ' + err);
        });
    }
    ```

    > [!IMPORTANT]
    > The sensors IDs that are defined in the code editor for the Raspberry Pi IoT simulator must be identical to the sensor IDs that you will specify later for the scenarios in Supply Chain Management. The preceding example code uses human-readable sensor IDs. However, in an actual scenario, the sensor IDs will be globally unique identifier (GUID) values that are provided by the sensor manufacturer. The human-readable sensor IDs that are used in this example code are also used in the examples for the [product quality scenario](sdi-scenario-product-quality.md), [asset maintenance scenario](sdi-scenario-asset-maintenance.md), [production delays scenario](sdi-scenario-production-delays.md), [anomaly detection scenario](sdi-scenario-anomaly.md), [asset downtime scenario](sdi-scenario-asset-downtime.md), and [machine status scenario](sdi-scenario-equipment-downtime.md)). Therefore, use this code if you will work through those scenarios.

## Edit the interval for sending sensor signals

You must now set the interval at which the Raspberry Pi IoT simulator should send the emulated sensor signals.

1. In the code editor of the Raspberry Pi IoT simulator, find the following function invocation.

    `setInterval(sendMessage, 2000);`

2. By default, the Raspberry Pi IoT simulator sends a sensor signal every 2,000 milliseconds (two seconds). You can adjust the value as you require.

## Run the Raspberry Pi IoT simulator

- Select **Run** to start the simulator and begin to send simulated sensor data.
