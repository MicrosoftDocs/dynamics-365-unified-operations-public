---
# required metadata

title: Add channel to org hierarchy
description: This topic presents the instructions to add a channel to an organizational hierarchy in Microsoft Dynamics 365 Commerce.
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
# Add channel to org hierarchy

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents the instructions to add a channel to an organizational hierarchy in Microsoft Dynamics 365 Commerce.

## Overview
Channels need to be assosiated with one or more organizational hierarchies, follow the instructions below to add.  

See [Organizational hierarchies](channels-org-hierarchies.md) for more details on how to create an organizational hierarchies.

## Select a hierachy
* Go to **Navigation pane** > **Modules** > **Retail** > **Channel Setup** > **Organization hierarchies**.
* Select the organization hierarchy that you'll be adding the channel to from the list.
* From the **Action pane** select "View" to load the visual 

![Select a hierarchy](media/channel-add-to-org-hierarchy-1.png)

## Add a channel to a hierachy node
* In the **Action pane**, select **Edit**.
* Select the hierachy node you want the channel added to and select the **Insert** drop down followed by **Retail Channel**. 
* Select the channel to add, then hit the **OK** button.
* Select **Save** in the **Action pane**.
* In the **Action pane**, select **Publish** and provide an **Effective date** in the past to have this go into effect immediately.

![Add a channel](media/channel-add-to-org-hierarchy-2.png)

Below example shows a hierarchy with various channels added.
![Channels example](media/channel-add-to-org-hierarchy-3.png)

