---
# required metadata

title: Set up an online channel
description: This topic presents the steps needed to create a new online channel within Microsoft Dynamics 365 Commerce.
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

This topic presents the steps needed to create a new online channel within Microsoft Dynamics 365 Commerce.

## Overview
TBD

## Create a new online channel
Before an online channel is created ensure you follow the channel [channel prerequisites](channels-prerequisites.md).

* Go to **Navigation pane** > **Modules** > **Channels** > **Online Stores**.
* On the **Action pane** click **New**.

![New online channel](media/channel-setup-online-1.png)

## Configure the new online channel
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

Below is an example online channel.

![Example online channel](media/channel-setup-online-2.png)

## Additional channel set up
There are additional items that need to be set up for a channel that can be found on the **Action pane** under the **Set up** section.

![Set up channel](media/channel-setup-online-3.png)

### Set up payment methods
* On the **Action pane**, select the **Set Up** tab and click **Payment methods**.

For each payment type supported on this channel do the following:
* On the **Action pane**, select **New**.
* Select an appropriate **Payment method**.
* In the **General** section provide an **Operation name** and set any other desired settings.
* Configure any additional settings as required for the payment type.
* Select **Save**.

![Example payment methods](media/channel-setup-retail-5.png)

### Set up modes of delivery
By selecting **Modes of delivery** from the **Set Up** tab on the **Action pane** you can see the configured modes of delivery.  To change or add a mode of delivery follow the below steps.
* Go to **Navigation pane** > **Modules** > **Invetory management** > **Modes of delivery**.
* On the **Action pane**, select **New** to create a new mode of delivery of select an existing mode.
* In the **Retail channels** section select **Add line** to add the channel.  Channels can be added via organization nodes which can streamline adding channels versus adding each individual channel.

![Set up modes of delivery](media/channel-setup-retail-7.png)

### Set up fulfillment group assignment
* On the **Action pane**, select the **Set Up** tab and click **Fulfullment group assignment**.
* On the **Action pane**, select **New**.
* Select a **Fulfillment group**.
* Provide a **Description**.
* Select **Save**.

![Set up fulfillment group assignment](media/channel-setup-retail-9.png)
