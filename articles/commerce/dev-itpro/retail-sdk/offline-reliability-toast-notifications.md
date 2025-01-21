---
title: Offline reliability toast notifications in Store Commerce
description: This article describes the various toast notifications available in Microsoft Dynamics 365 Commerce Store Commerce app.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 01/21/2025
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# Offline reliability toast notifications in Store Commerce app

This article describes the various toast notifications available in the Microsoft Dynamics 365 Commerce Store Commerce app to support Offline reliability scenarios starting with release 10.0.43. 

## Enable toast notifications feature.

To enable toast notifications in the Store commerce app, the following feature management flags should be turned on.

- Enable proactive notifications for offline functionalities.
- Enable proactive notifications for network connectivity insights.

## Toast notification for offline logon failure

Store employees receive a notification if the offline mode is unavailable due to offline logon authentication failure. The notification has a link for more detailed error information that can be copied and sent to an Administrator for corrective action.

![toastnotificationofflinelogon.](media/toastnotificationofflinelogon.jpg)

## Toast notification for Seamless offline switch

Store employees receive a notification when POS switches to offline mode through the seamless switch mechanism and also receive a notification when POS switches back to online mode.

![seamlessoffline.](media/seamlessoffline.jpg)

## Toast notification for missing or weak network connection

Store employees receive a notification when network connectivity is missing or weak, with a prompt to switch to offline. Additionally, there is a direct link to network connectivity 
insights from the notification to learn more. To learn more on the network connectivity insights see [Network health checks](pos-healthcheck.md) 

![network-connectivity-notification.](media/network-connectivity-notification.jpg)

Visit this page as we update with more notifications in the future releases.

