---
# required metadata

title: Set up a retail  channel
description: This topic presents the steps needed to create a new retail channel within Microsoft Dynamics 365 Commerce.
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
# Set up an online channel

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents the steps needed to create a new retail channel within Microsoft Dynamics 365 Commerce.

## Overview
TBD

## Create a new retail channel
Before a retail channel is created ensure you follow the channel prerequisite steps. (LINK TBD)

* Go to **Navigation pane** > **Modules** > **Channels** > **Retail stores** > **All retail stores**.
* On the **Action pane** click **New**.

![New online channel](media/channel-setup-retail-1.png)

## Configure the new retail channel
* In the **Name** field, provide a name for the new channel.
* Select the appropriate **Legal entity** from the drop down.
* Select the appropriate **Warehouse** location from the drop down.
* Set the appropriate time zone in the **Store time zone** field.
* Set the appropriate currency in the **Currency** field.
* In the **Default customer** field, provide a valid default customer.
* In the **Customer address book** field, provide a valid address book.
* In the **Functionality profile** field, select one if applicable.
* In the **Email notification profile** field, provide a valid email notification profile.
* Select **Save**

## Set up languages
If your e-Commerce site will support multiple languages, expand the **Languages** section and add additional languages as needed.

## Set up payment account
From within the **Payment account** section you can add a 3rd party payment provider.  Please see the following to setup Adyen payment connect (TBD)

Below is an example retail channel.

![Example retail channel](media/channel-setup-retail-2.png)




