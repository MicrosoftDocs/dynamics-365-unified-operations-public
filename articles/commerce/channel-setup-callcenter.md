---
# required metadata

title: Set up a call center channel
description: This topic describes how to create a new call center channel in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 02/03/2020
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Release 10.0.8

---
# Set up a call center channel

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new call center channel in Microsoft Dynamics 365 Commerce.

## Overview
TBD

## Create and configure new call center channel

Before a new call center channel is created, ensure that you have completed the [Channel set up prerequisites](channels-prerequisites.md).

To create and configure a new call center channel, follow these steps.

1. Go to **Navigation pane \> Modules \> Channels \> Call centers \> All call centers**.
1. On the **Action pane**, select **New**.
1. In the **Name** field, provide a name for the new channel.
1. Select the appropriate **Legal entity** from the drop down.
1. Select the appropriate **Warehouse** location from the drop down.
1. In the **Default customer** field, provide a valid default customer.
1. In the **Email notification profile** field, provide a valid email notification profile.
1. Provide a **Price override** info code.  Note you may need to create an info code for this first.
1. Provide a **Hold code** info code.  Note you may need to create an info code for this first.
1. Provide a **Credit** info code.  Note you may need to create an info code for this first.
1. Select **Save**

The following image shows how to create a new call center channel.

![New call center channel](media/channel-setup-callcenter-1.png)

The following image shows an example call center channel.

![Example call center channel](media/channel-setup-callcenter-2.png)

## Additional channel setup

Additional tasks required for call center channel setup include setting up payment methods and modes of delivery.

The following image shows **Modes of delivery** and **Payment methods** on the **Set up** tab.

![Additional channel setup actions](media/channel-setup-callcenter-3.png)

### Set up payment methods

To set up payment methods, for each payment type supported on this channel follow these steps.

1. On the **Action pane**, select the **Set up** tab, and then select **Payment methods**.
1. On the **Action pane**, select **New**.
1. In the navigation pane, select a desired payment method.
1. In the **General** section, provide an **Operation name** and configure any other desired settings.
1. Configure any additional settings as required for the payment type.
1. On the **Action pane**, select **Save**.

The following image shows an example for a cash payment method.

![Example payment methods](media/channel-setup-retail-5.png)

### Set up modes of delivery

You can see the configured modes of delivery by selecting **Modes of delivery** from the **Set up** tab on the **Action pane**.  

To change or add a mode of delivery, follow these steps.

1. Go to **Navigation pane \> Modules \> Inventory management \> Modes of delivery**.
1. On the **Action pane**, select **New** to create a new mode of delivery, or select an existing mode.
1. In the **Retail channels** section, select **Add line** to add the channel. Adding channels using organization nodes instead of adding each channel individually can streamline adding channels.

The following image shows an example of a mode of delivery.

![Set up modes of delivery](media/channel-setup-retail-7.png)

## Additional resources

[Channel set up prerequisites](channels-prerequisites.md)

[Call center sales functionality](../retail/call-center-functionality.md?toc=/dynamics365/commerce/toc.json)

[Set up call center order processing options](../retail/set-up-order-processing-options.md?toc=/dynamics365/commerce/toc.json)

[Call center catalogs](../retail/call-center-catalogs.md?toc=/dynamics365/commerce/toc.json)

[Set up and work with fraud alerts](../retail/set-up-fraud-alerts.md?toc=/dynamics365/commerce/toc.json)

[Set up continuity programs for call centers](../retail/set-up-continuity-program.md?toc=/dynamics365/commerce/toc.json)
