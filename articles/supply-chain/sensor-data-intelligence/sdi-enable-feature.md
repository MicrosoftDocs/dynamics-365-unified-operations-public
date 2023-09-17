---
title: Turn on Sensor Data Intelligence for your system
description: This article explains how to turn on Sensor Data Intelligence for your system.
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

# Turn on Sensor Data Intelligence for your system

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

## Video instructions

The following video shows how to turn on the Sensor Data Intelligence feature and [deploy the required Azure resources](sdi-deploy-iot-solution-on-azure.md). The other section in this article provides the same instructions in a text-based format.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE58g3I]

## Procedure

Before you can use Sensor Data Intelligence, it must be turned on for your system.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. On the **All** tab, use the **Filter** field to search for the feature that is named *Sensor Data Intelligence*.
1. If the *Sensor Data Intelligence* feature is enabled on your system, select it in the list, and then select **Disable** to disable it. You can't use this older version of the feature together with the new preview version that you will enable in the next step.
1. Use the **Filter** field to search for the feature that is named *(Preview) Sensor Data Intelligence*.
1. Select the feature in the list, and then select **Enable now** to enable it.
