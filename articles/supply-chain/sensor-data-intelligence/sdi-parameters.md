---
title: Sensor Data Intelligence parameters
description: This article provides information about configuration settings that are available on the Sensor Data Intelligence parameters page.
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
<!-- KFM: Preview until further notice -->

The **Sensor Data Intelligence parameters** page provides a few settings that you can use to configure the feature. These settings include Azure connection parameters and a parameter for the lifetime of alert messages that are sent to users in response to sensor measurements.

## Read and change connection details for your Azure IoT solution

Typically, you will set up your Azure IoT solution and connect it to Microsoft Dynamics 365 Supply Chain Management from the **Deploy and connect Azure resources** page, which will guide you through both procedures. (For more information, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).) You can also view and edit the connection details at any time in Supply Chain Management by following these steps.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. On the **Time series** tab, in the **Redis metric store connection string** field, enter the **Primary connection string (StackExchange.Redis)** value for the Azure IoT solution that you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).
1. On the **Integrations** tab, in the **Azure AD application client ID** field, enter the **Client ID** value for the Azure IoT solution you want to connect to. For more information about how to find this value, see [Deploy an IoT solution on Azure](sdi-deploy-iot-solution-on-azure.md).

## Set the lifetime of alert messages

Each time that Sensor Data Intelligence detects a situation that requires user attention, it sends a notification to the relevant user. To prevent these notifications from piling up in the system, you should set them to expire after a few days.

1. Go to **System administration \> Setup \> Sensor Data Intelligence \> Sensor Data Intelligence parameters**.
1. On the **Notifications** tab, in the **Notification days to live** field, enter the number of days to keep a notification. After the specified amount of time passes, the notification will be deleted.
