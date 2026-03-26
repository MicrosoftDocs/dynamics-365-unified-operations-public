---
title: Enable and configure auto charges by channel
description: Learn how to enable and configure auto charges by channel in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/15/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2020-03-01
ms.custom: 
  - bap-template
---

# Enable and configure auto charges by channel

This article explains how to enable and configure automatic charges (auto charges) by channel in Microsoft Dynamics 365 Commerce.

## Overview

You might have scenarios where recycling fees or other fees must be applied to a group of products that are sold in all or some stores in a specific state (for example, California). The **Enable filter auto charges by channel** feature in Commerce lets you specify auto charges by channel (for example, a specific brick-and-mortar channel). This feature is available in Dynamics 365 Commerce version 10.0.10 and later.

To enable and configure auto charges by channel, complete the following tasks:

- Turn on the **Enable filter auto charges by channel** feature.
- Configure the organization hierarchy purpose.
- Define auto charges by channel.

> [!NOTE]
> The **Enable filter auto charges by channel** feature works only if the advanced auto charges feature is also turned on. For information about how to turn on the advanced auto charges feature, see [Omni-channel advanced auto charges](omni-auto-charges.md).

## Turn on the Enable filter auto charges by channel feature

To turn on auto charges by channel in Commerce, follow these steps:

1. Go to **System administrator \> Workspaces \> Feature management**.
1. On the **Not enabled** tab, in the **Feature name** list, find and select **Enable filter auto charges by channel**.
1. In the lower-right corner, select **Enable now**. After the feature is turned on, it appears in the list on the **All** tab.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. In the left pane, find and select the **1110** (**Global configuration**) job.
1. On the Action Pane, select **Run now** to propagate the configuration changes.

> [!WARNING]
> If you turn off the **Enable filter auto charges by channel** feature after you use it, the **Retail channel relation** field under **Auto charges** no longer appears, and you lose all existing configurations. If removal of the **Retail channel relation** configurations causes auto charges rules to be duplicated, an attempt to turn off the feature fails. Before you turn off the feature, review all auto charges rules and make any required changes.

## Configure the organization hierarchy purpose

Create an organization hierarchy purpose named **Retail auto charge** to manage the hierarchy for auto charges by channel.

To assign a default hierarchy to an organization hierarchy purpose in Commerce, follow these steps:
		
1. Go to **Organization administration \> Organizations \> Organization hierarchy purposes**.
1. In the left pane, select **Retail auto charge**.
1. Under **Assigned hierarchies**, select **Add**.
1. In the **Organization hierarchies** dialog box, select an organization hierarchy (for example, **Retail Stores by Region**), and then select **OK**.
1. Under **Assigned hierarchies**, select **Set as default**.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. In the left pane, find and select the **1040** (**Products**) job.
1. On the Action Pane, select **Run now**.
1. Repeat the previous two steps to run the **1070** (**Channel configuration**) and **1110** (**Global configuration**) jobs.

:::image type="content" source="media/Auto-charges-org-hierarchy-purpose.png" alt-text="Screenshot of the configuration of the Retail auto charge organization hierarchy purpose.":::

## Define auto charges by channel

After you turn on the **Enable filter auto charges by channel** feature and configure the **Retail auto charge** organization hierarchy purpose, you can define auto charges by channel at either the order header level or the order line level.

To define auto charges by channel in Commerce, follow these steps:

1. Go to **Accounts receivable > Charges setup > Auto charges**.
1. In the left pane, in the **Level** field, select either **Header** or **Line**, depending on your business requirements.
1. In the **Retail channel code** field, select the appropriate channel code (for example, **Table** or **Group**). If you use the default setting, **All**, charge rules apply to all channels.

    - If you select **Group**, make sure that you create a retail channel charges group at **Retail and Commerce > Channel setup > Charges > Retail channel charge groups**.
    - If you select **Table**, you can select a specific channel (for example, **San Francisco**) in the **Retail channel relation** field.

1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. In the left pane, find and select the **1040** (**Products**) job.
1. On the Action Pane, select **Run now**.
1. Repeat the previous two steps to run the **1070** (**Channel configuration**) and **1110** (**Global configuration**) jobs.
	
:::image type="content" source="media/Auto-charges-line-charge-by-channel.png" alt-text="Screenshot of auto charges defined by channel.":::

## Example scenario

The following example outlines the steps to configure a product so that recycling fees are charged when the product is sold through a San Francisco brick-and-mortar channel. The example also shows how the auto charges appear in the Commerce point of sale (POS) application.

The organization defines a charges code named **RECYCLE**, as shown in the following illustration.

:::image type="content" source="media/Auto-charges-charge-code.png" alt-text="Screenshot of the RECYCLE charges code configuration.":::

Create an auto charge at the line level with the following configuration:

- Set the **Account code** field to **All**.
- Set the **Item code** field to **Table**.
- Set the **Item relation** field to product ID **91001**.
- Set the **Mode of delivery code** field to **All**.
- Set the **Retail channel code** field to **Table**.
- Set the **Retail channel relation** field to the **San Francisco** store.

Create an auto charges line with the following configuration:

- Set the **Currency** field to **USD**.
- Set the **Charges code** field to **RECYCLE**.
- Set the **Category** field to **Fixed**.
- Set the **Charges** field to **$6.25**.

:::image type="content" source="media/Auto-charges-recyclingfee-line-fee.png" alt-text="Screenshot of the configuration of the line-level auto charge and the auto charges line.":::

In the POS application, create a sales order in the **San Francisco** store channel. The **Charges** line shows the recycling fee of **$6.25**.

By selecting **Transaction options \> Charges \> Manage charges** in the POS application, you can view the charges code and description for the recycling fee.

:::image type="content" source="media/pos-auto-charges-recyclingfee-line-fee.png" alt-text="Screenshot of the recycling fee in the POS application.":::

## Additional resources

[Omni-channel advanced auto charges](omni-auto-charges.md)

[Prorate header charges to matching sales lines](pro-rate-charges-matching-lines.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
