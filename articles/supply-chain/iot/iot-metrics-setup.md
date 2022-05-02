---
# required metadata

title: Set up metrics for IoT Intelligence
description: This topic explains how to set up metrics for IoT Intelligence.
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

# Set up metrics for IoT Intelligence

[!include [banner](../../includes/banner.md)]

## Configure metrics

If you want to view the time series charts of your messages in Microsoft Dynamics 365 Supply Chain Management, you must set up the metrics by following these steps.

1. Copy the connection string for the Redis cache:

    1. In the Azure portal, go to the Redis cache.
    2. Go to **Settings** \> **Access keys**.
    3. Copy the value in the **Primary connection string** field.

2. In Supply Chain Management, go to **Production control \> Setup \> IoT Intelligence \> Scenario parameters**.
3. On the **Scenario parameters** page, on the **Time series** tab, in the **Redis metric store connection string** field, paste the connection string that you copied earlier. This step enables the metrics from Azure IoT Hub to be visualized in Supply Chain Management. When you paste the value into the field, it's shown as **\*\*\*\*\*\***.

    > [!NOTE]
    > Whenever you update the Redis cache connection string, you must also update this field.

4. Go to **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**.
5. On the **Metric keys** page, select **Update**.
6. In the **Update metric keys** dialog box, notice that **Run in the background** is selected in the field. Select **OK**.

All the metric keys in the Redis cache are retrieved and added to the **Metric keys** list. Metric values won't appear until you [enable the scenarios](iot-scenario-setup.md).

## Configure the Resource Status time series

To configure the **Resource Status** time series, follow these steps.

1. In Supply Chain Management, go to **Production control \> Manufacturing execution \> Resource Status**.
2. On the **Resource status** page, select **Configure**.
2. In the **Configure** dialog box, in the **Resource** list, select an item to monitor.
3. Select the **Edit** button for **Time series 1**.
4. In the **Select time series** dialog box, select a metric in the grid. (You can also use the **Update metric keys** link to update the metric keys from this dialog box.)
5. Select **OK** to return to the **Configure** dialog box.
6. Enter a display name.
7. In the **Show data from** field, select a time frame.
8. Select **OK**.

The chart is shown.

## Delete a metric key

1. In Supply Chain Management, go to **Production control \> Inquiries and reports \> IoT Intelligence \> Metric keys**.
2. On the **Metric keys** page, select the metric key to delete.
3. Select **Delete**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]