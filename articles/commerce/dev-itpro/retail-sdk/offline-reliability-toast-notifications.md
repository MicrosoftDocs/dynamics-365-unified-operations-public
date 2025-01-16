---
title: Offline reliability toast notifications in Store Commerce
description: This article describes the various toast notifications that will be available in Microsoft Dynamics 365 Commerce Store Commerce app.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 01/16/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
---

# Offline reliability toast notifications in Store Commerce app

The article describes the various toast notifications that will be available in the Store Commerce app to support Offline reliability scenarios starting release 10.0.43. 

## Enable toast notifications feature.

To enable toast notifications in Store commerce app, following feature management flags should be turned on.

Enable proactive notifications for offline functionalities.
Enable proactive notifications for network connectivity insights.

## Toast notification for offline logon failure

Store employees will receive a notification if the offline mode is unavailable due to offline logon authentication failure. The notification will have a link for more detailed
error information that may be copied and sent to admin for corrective action.

## Toast notification for Seamless offline switch

Store employees will receive a notification when POS switches to offline mode through the seamless switch mechanism and will also receive a notification when POS switches back to online mode.

## Toast notfication for missing or weak network connection

Store employees will receive a notification when network connectivity is missing or weak, with a prompt to switch to offline. Additionally, there will be a direct link to network connectivity 
insights from the notification to learn more. To learn more on the network connectivity insights see [Network health checks](pos-healthcheck.md) 

Please visit this page as we update with more notifications in the future releases.

