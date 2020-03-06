---
# required metadata
title: Enable and configure auto charges by channel of order creation
description: This topic describes how to enable and configure auto charges by the channel of the order creation in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
manager: annbe
ms.date: 03/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2020-03-01
ms.dyn365.ops.version: 10.0.10
---

# Enable and configure auto charges by the channel of order creation

This topic describes how to enable and configure auto charges by the channel of order creation in Microsoft Dynamics 365 Commerce.

## Overview

You may have scenarios where you need to apply recycling or other fees for a group of products that are sold in all or some of the stores in a particular state (for example, California). The "Enable filter auto charges by channel" feature switch allows you to enable auto charges by channel. This feature is available in Dynamics 365 Commerce in version 10.0.10 or later. 

> [!NOTE]
> The auto charges by channel feature only works when the advanced auto charges feature is enabled. For information on how to enable advanced auto charges, see [Omni-channel advanced auto charges](omni-auto-charges.md). 

## Enable filter auto charges by channel

To enable filter auto charges by channel in Commerce, follow these steps.

1. Go to **System administrator \> Workspaces \> Feature management**.
1. Select the **Not enabled** tab. Under the **Feature name** list, find and select **Enable filter auto charges by channel**.
1. In the right bottom corner, select **Enable now**. After this feature is enabled, it will be located in the **All** tab list.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. In the left pane, find and select the **1110 Global configuration** job.
1. On the action pane, select **Run now** to propagate the configuration changes. 

> [!WARNING]
> If you decide to deactivate the **Enable filter auto charges by channel** switch after using the feature, the **Retail channel relation** drop down menu under **Auto charges** will disappear and you will lose all existing configurations. If removing **Retail channel relation** configurations would result in duplicate auto charges rules, then deactivation will fail. Please review all auto charges rules and make any necessary changes prior to deactivating.

## Configure organization hierarchy purpose

A new organization hierarchy purpose called "Retail auto charge" has been created for managing hierarchy for auto charges by channel. 

To configure an organization hierarchy purpose with a default hierarchy in Commerce, follow these steps. 
		
1. Go to **Organization administration \> Organizations \> Organization hierarchy purposes**. 
1. In the left pane, select **Retail auto charge**.
1. Under **Assigned hierarchies**, select **+ Add**. 
1. In the **Organization hierarchies** pane, select an organization hierarchy (for example, **Retail Stores by Region**) and then select **OK**.
1. Under **Assigned hierarchies**, select **Set as default**.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. In the left pane, find and select the **1040 Products** job.
1. On the action pane, select **Run now**. 
1. Repeat the previous 2 steps to run the **1070 Channel configuration** and **1110 Global configuration** jobs. 

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-org-hierarchy-purpose.png)

## Define auto charges by channel

After enabling the "auto charges by channel" feature switch and configuring the "Retail auto charges" organization hierarchy purpose, auto charges by channel can be defined at the order header level or line level.

To define auto charges by channel in Commerce, follow these steps.

1. Go to **Accounts receivable \> Charges setup \> Auto charges** . 
1. In the left pane **Level** drop down menu, select either the **Header** level or **Line** level, based on business requirements. 
1. On the **Retail channel code** drop down menu, select the appropriate channel code (for example, **Table** or **Group**). The default setting is **All**, which means that charge rules are applied for all channels. 
    - For **Group**, make sure that a **Retail channel charges group** is created that you can find under **Retail and Commerce \> Channel setup \> Charges \> Retail channel charge groups**.
    - For **Table**, you can select a specific channel from the under **Retail channel relation** drop down menu (for example, **San Francisco**).  
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. In the left pane, find and select the **1040 Products** job.
1. On the action pane, select **Run now**. 
1. Repeat the previous 2 steps to run the **1070 Channel configuration** and **1110 Global configuration** jobs. 
	
![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-line-charge-by-channel.png)

## Example scenario

The following example scenario outlines the steps to configure a product with recycling fees when it is sold through a San Francisco brick and mortar channel, and also shows the corresponding rendering of the auto charges in the Dynamics 365 Commerce point of sale (POS) application.

In this scenario, the organization has defined charges code called **RECYCLE** as shown in the following image. 

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-charge-code.png)

An auto charge has been created at the line level where:
- **Account code** is set to **All**.
- **Item code** is set to **Table**.
- **Item relation** is set to product ID **91001**.
- **Mode of delivery code** is set to **All**.
- **Retail channel code** is set to **Table**.
- **Retail channel relation** is set to **San Francisco** store. 

An auto charges line has been created where:
- **Currency** is set to **USD**.
- **Charges code** is set to **RECYCLE**.
- **Category** is set to **Fixed**.
- **Charges** is set to **$6.25**.

![Dynamics 365 Commerce - Auto charges by channel](media/Auto-charges-recyclingfee-line-fee.png)

In the POS application, a sales order is created in the **San Francisco** store channel with the **CHARGES** line showing the recycling fee of **$6.25**. 

Navigating to **Transaction options \> Charges \> Manage charges** in the POS application will display the recycling fee charges code and description. 

![Dynamics 365 Commerce - Auto charges by channel](media/pos-auto-charges-recyclingfee-line-fee.png)

## Additional resources

[Omni-channel advanced auto charges](omni-auto-charges.md)

[Prorate header charges to matching sales lines](pro-rate-charges-matching-lines.md)


