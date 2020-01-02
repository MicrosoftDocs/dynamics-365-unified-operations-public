---
# required metadata

title: Set up a call center channel
description: This topic presents the steps needed to create a new call center channel within Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---
# Set up a call center channel

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents the steps needed to create a new call center channel within Microsoft Dynamics 365 Commerce.

## Overview
TBD

## Create a new call center channel
Before a call center channel is created ensure you follow the [channel prerequisites](channels-prerequisites.md).

* Go to **Navigation pane** > **Modules** > **Channels** > **Call centers** > **All call centers**.
* On the **Action pane** click **New**.

![New call center channel](media/channel-setup-callcenter-1.png)

## Configure the new call center channel
* In the **Name** field, provide a name for the new channel.
* Select the appropriate **Legal entity** from the drop down.
* Select the appropriate **Warehouse** location from the drop down.
* In the **Default customer** field, provide a valid default customer.
* In the **Email notification profile** field, provide a valid email notification profile.
* Provide a **Price override** info code.  Note you may need to create an info code for this first.
* Provide a **Hold code** info code.  Note you may need to create an info code for this first.
* Provide a **Credit** info code.  Note you may need to create an info code for this first.
* Select **Save**

Below is an example call center channel.

![Example call center channel](media/channel-setup-callcenter-2.png)
