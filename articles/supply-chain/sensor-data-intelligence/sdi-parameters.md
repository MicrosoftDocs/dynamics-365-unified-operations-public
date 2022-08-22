---
title: Sensor Data Intelligence parameters
description: The product quality scenario uses a sensor to measure the quality of a product batch and generates an alert if a measurement falls outside a defined threshold.
author: johanhoffmann
ms.date: 09/02/2022
ms.topic: article
ms.search.form: IoTIntCoreServiceParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.30
---

# Sensor Data Intelligence parameters

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
 
The **Sensor Data Intelligence parameters** page provides a few settings for configuring the feature, including the connection to Azure and the lifetime of alert messages sent to users in response to sensor measurements.

## Read and change connection details for your Azure IoT solution

Usually, you'll set up your Azure IoT solution and connect it to Supply Chain Management from the **Deploy and connect Azure resources** page, which will guide you through both procedures (see also [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md)). You can also view and edit the connection details at any time in Supply Chain Management, as described in the following procedure.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. Open the **Time series** tab and make the following setting:
    - **Redis metric store connection string** – Enter the **Primary connection string (StackExchange.Redis)** value for the Azure IoT solution you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).
1. Open the **Integrations** tab and make the following setting:
    - **Azure AD application client ID** – Enter the **Client ID** value for the Azure IoT solution you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).

## Set the lifetime of alert messages

Each time Sensor Data Intelligence detects a situation that requires user attention, it sends a notification to the relevant user. To prevent these notifications from piling up in the system, you should set them to expire after a few days, as described in the following procedure.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. Open the **Notifications** tab and make the following setting:
    - **Notification days to live** – Enter the number of days for which to keep a notification. After this amount of time has passed, the notification will be deleted.
