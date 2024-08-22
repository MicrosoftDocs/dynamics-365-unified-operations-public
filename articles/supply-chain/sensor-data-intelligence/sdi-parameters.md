---
title: Sensor Data Intelligence parameters (preview)
description: Learn about configuration settings that are available on the Sensor Data Intelligence parameters page with an outline on setting the lifetime of alert messages.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 09/02/2022
ms.reviewer: kamaybac
ms.search.form: IoTIntCoreServiceParameters
---

# Sensor Data Intelligence parameters (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

<!-- KFM: Preview until further notice -->

The **Sensor Data Intelligence parameters** page provides a few settings that you can use to configure the feature. These settings include Azure connection parameters and a parameter for the lifetime of alert messages that are sent to users in response to sensor measurements.

## Read and change connection details for your Azure IoT solution

Typically, you will set up your Azure IoT solution and connect it to Microsoft Dynamics 365 Supply Chain Management from the **Deploy and connect Azure resources** page, which will guide you through both procedures. (Learn more in [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).) You can also view and edit the connection details at any time in Supply Chain Management by following these steps.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. On the **Time series** tab, in the **Redis metric store connection string** field, enter the **Primary connection string (StackExchange.Redis)** value for the Azure IoT solution that you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).
1. On the **Integrations** tab, in the **Microsoft Entra application client ID** field, enter the **Client ID** value for the Azure IoT solution you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).

## Set the lifetime of alert messages

Each time that Sensor Data Intelligence detects a situation that requires user attention, it sends a notification to the relevant user. To prevent these notifications from piling up in the system, you should set them to expire after a few days.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. On the **Notifications** tab, in the **Notification days to live** field, enter the number of days to keep a notification. After the specified amount of time passes, the notification will be deleted.