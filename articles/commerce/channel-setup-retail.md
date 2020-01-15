---
# required metadata

title: Set up a retail  channel
description: This topic describes how to create a new retail channel in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-31
ms.dyn365.ops.version: Release 10.0.8

---
# Set up a retail channel

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new retail channel in Microsoft Dynamics 365 Commerce.

## Overview
TBD

Microsoft Dynamics 365 Commerce supports multiple retail channels. These retail channels include online stores, call centers, and retail stores (also known as brick-and-mortar stores).

Before a retail channel is created ensure you follow the [channel prerequisites](channels-prerequisites.md).

## Create and configure a new retail channel

1. Go to **Navigation pane \> Modules \> Channels \> Retail stores \> All retail stores**.
1. On the **Action pane**, select **New**.
1. In the **Name** field, provide a name for the new channel.
1. In the **Store number** field, provide a unique store number. The number can be alphanumeric with a maximum of 10 characters.
1. In the **Legal entity** drop-down list, enter the appropriate legal entity.
1. In the **Warehouse** drop-down list, enter the appropriate warehouse.
1. In the **Store time zone** field, select the appropriate time zone.
1. In the **Sales tax group** drop-down list, select an appropriate sales tax group for the store.
1. In the **Currency** field, select the appropriate currency.
1. In the **Customer address book** field, provide a valid address book.
1. In the **Default customer** field, provide a valid default customer.
1. In the **Functionality profile** field, select a functionality profile if applicable.
1. In the **Email notification profile** field, provide a valid email notification profile.
1. On the **Action pane**, select **Save**.

The following image shows

![New retail channel](media/channel-setup-retail-1.png)

The following image shows

![Example retail channel](media/channel-setup-retail-2.png)

## Other settings

There are numerous others settings that can be optionally set in the **Statement/closing**, **Miscellaneous** sections based on the needs of the retail store.

Additionally see [screen layouts for the POS](https://docs.microsoft.com/en-us/dynamics365/retail/pos-screen-layouts?toc=/dynamics365/commerce/toc.json) to setup the default **Screen Layout** and [configure and install Retail hardware station](https://docs.microsoft.com/en-us/dynamics365/retail/retail-hardware-station-configuration-installation) for **Hardware stations** set up information.

The following image shows an example retail channel setup configuration.

![Example retail channel configuration](media/channel-setup-retail-3.png)

## Additional channel set up
There are additional items that need to be set up for a channel that can be found on the **Action pane** under the **Set up** section.

The following image shows

![Set up channel](media/channel-setup-retail-4.png)

### Set up payment methods

1. On the **Action pane**, select the **Set Up** tab and click **Payment methods**.

For each payment type supported on this channel do the following:
1. On the **Action pane**, select **New**.
1. Select an appropriate **Payment method**.
1. In the **General** section provide an **Operation name** and set any other desired settings.
1. Configure any additional settings as required for the payment type.
1. Select **Save**.

The following image shows

![Example payment methods](media/channel-setup-retail-5.png)

### Set up Cash declaration

1. On the **Action pane**, select the **Set Up** tab and click **Cash declaration**.
1. On the **Action pane**, select **New** and create all **Coin** and **Note** denominations that are applicable.

The following image shows

![Setup up cash declarations](media/channel-setup-retail-6.png)

### Set up modes of delivery

By selecting **Modes of delivery** from the **Set Up** tab on the **Action pane** you can see the configured modes of delivery.  To change or add a mode of delivery follow the below steps.

1. Go to **Navigation pane** > **Modules** > **Invetory management** > **Modes of delivery**.
1. On the **Action pane**, select **New** to create a new mode of delivery of select an existing mode.
1. In the **Retail channels** section select **Add line** to add the channel.  Channels can be added via organization nodes which can streamline adding channels versus adding each individual channel.

The following image shows

![Set up modes of delivery](media/channel-setup-retail-7.png)

### Set up Income/Expense account
1. On the **Action pane**, select the **Set Up** tab and click **Income/Expense account**.
1. On the **Action pane**, select **New**.
1. Provide a **Name** and **Search name**.
1. Select the **Account type**.
1. Provide a **Message line 1**, **Message line 2**, **Slip text 1** and **Slip text 2** as needed.
1. Fill out **Posting** information.
1. On the **Action pane**, select **Save**.

The following image shows

![Set up income/expense accounts](media/channel-setup-retail-8.png)

### Set up Sections

1. On the **Action pane**, select the **Set Up** tab and click **Sections**.
1. On the **Action pane**, select **New**.
1. Provide a **Section number** and **Description** and **Section size**.
1. Additional configurations can be set in the **General** and **Sales statistics** sections.
1. On the **Action pane**, select **Save**.

### Set up fulfillment group assignment

1. On the **Action pane**, select the **Set Up** tab and click **Fulfullment group assignment**.
1. On the **Action pane**, select **New**.
1. Select a **Fulfillment group**.
1. Provide a **Description**.
1. On the **Action pane**, select **Save**.

The following image shows

![Set up fulfillment group assignments](media/channel-setup-retail-9.png)

### Set up Safes

1. On the **Action pane**, select the **Set Up** tab and click **Safes**.
1. On the **Action pane**, select **New**.
1. Provide a name for the safe
1. On the **Action pane**, select **Save**.

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Set up an online channel](channel-setup-online.md)

[Set up a call center channel](channel-setup-callcenter.md)

