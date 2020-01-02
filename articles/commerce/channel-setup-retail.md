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
# Set up a retail channel

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents the steps needed to create a new retail channel within Microsoft Dynamics 365 Commerce.

## Overview
TBD

## Create a new retail channel
Before a retail channel is created ensure you follow the [channel prerequisites](channels-prerequisites.md).

* Go to **Navigation pane** > **Modules** > **Channels** > **Retail stores** > **All retail stores**.
* On the **Action pane** click **New**.

![New retail channel](media/channel-setup-retail-1.png)

## Configure the new retail channel
* In the **Name** field, provide a name for the new channel.
* In the **Store number** field, provide a unique store number. THe number can be alphanumeric with a maximum of 10 characters.
* Select the appropriate **Legal entity** from the drop down.
* Select the appropriate **Warehouse** location from the drop down.
* Set the appropriate time zone in the **Store time zone** field.
* Select an appropriate **Sales tax group** for the store.
* Set the appropriate currency in the **Currency** field.
* In the **Customer address book** field, provide a valid address book.
* In the **Default customer** field, provide a valid default customer.
* In the **Functionality profile** field, select one if applicable.
* In the **Email notification profile** field, provide a valid email notification profile.
* Select **Save**.

![Example retail channel](media/channel-setup-retail-2.png)

## Other settings
There are numerous others settings that can be optionally set in the **Statement/closing**, **Miscellaneous** sections based on the needs of the retail store.

Additionally see [screen layouts for the POS](https://docs.microsoft.com/en-us/dynamics365/retail/pos-screen-layouts?toc=/dynamics365/commerce/toc.json) to setup the default **Screen Layout** and [configure and install Retail hardware station](https://docs.microsoft.com/en-us/dynamics365/retail/retail-hardware-station-configuration-installation) for **Hardware stations** set up information.

Below image shows an example retail channel setup configuration.
![Example retail channel configuration](media/channel-setup-retail-3.png)

## Additional channel set up
There are additional items that need to be set up for a channel that can be found on the **Action pane** under the **Set up** section.

![Set up channel](media/channel-setup-retail-4.png)

### Set up payment methods
* On the **Action pane**, select the **Set Up** tab and click **Payment methods**.

For each payment type supported on this channel do the following:
* On the **Action pane**, select **New**.
* Select an appropriate **Payment method**.
* In the **General** section provide an **Operation name** and set any other desired settings.
* Configure any additional settings as required for the payment type.
* Select **Save**.

![Example payment methods](media/channel-setup-retail-5.png)

### Set up Cash declaration
* On the **Action pane**, select the **Set Up** tab and click **Cash declaration**.
* On the **Action pane**, select **New** and create all **Coin** and **Note** denominations that are applicable.

![Setup up cash declarations](media/channel-setup-retail-6.png)

### Set up modes of delivery
By selecting **Modes of delivery** from the **Set Up** tab on the **Action pane** you can see the configured modes of delivery.  To change or add a mode of delivery follow the below steps.
* Go to **Navigation pane** > **Modules** > **Invetory management** > **Modes of delivery**.
* On the **Action pane**, select **New** to create a new mode of delivery of select an existing mode.
* In the **Retail channels** section select **Add line** to add the channel.  Channels can be added via organization nodes which can streamline adding channels versus adding each individual channel.

![Set up modes of delivery](media/channel-setup-retail-7.png)

### Set up Income/Expense account
* On the **Action pane**, select the **Set Up** tab and click **Income/Expense account**.
* On the **Action pane**, select **New**.
* Provide a **Name** and **Search name**.
* Select the **Account type**.
* Provide a **Message line 1**, **Message line 2**, **Slip text 1** and **Slip text 2** as needed.
* Fill out **Posting** information.
* Select **Save**.

![Set up income/expense accounts](media/channel-setup-retail-8.png)

### Set up Sections
* On the **Action pane**, select the **Set Up** tab and click **Sections**.
* On the **Action pane**, select **New**.
* Provide a **Section number** and **Description** and **Section size**.
* Additional configurations can be set in the **General** and **Sales statistics** sections.
* Select **Save**.

### Set up fulfillment group assignment
* On the **Action pane**, select the **Set Up** tab and click **Fulfullment group assignment**.
* On the **Action pane**, select **New**.
* Select a **Fulfillment group**.
* Provide a **Description**.
* Select **Save**.

![Set up fulfillment group assignments](media/channel-setup-retail-9.png)

### Set up Safes
* On the **Action pane**, select the **Set Up** tab and click **Safes**.
* On the **Action pane**, select **New**.
* Provide a name for the safe
* Select **Save**.
