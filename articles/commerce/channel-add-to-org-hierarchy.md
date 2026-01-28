---
title: Add a channel to an organizational hierarchy
description: Learn how to add a channel to an organizational hierarchy in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-01-20
ms.custom: 
  - bap-template
---
# Add a channel to an organizational hierarchy

[!include [banner](includes/banner.md)]

This article describes how to add a channel to an organizational hierarchy in Microsoft Dynamics 365 Commerce.

You need to associate channels with one or more organizational hierarchies. Before creating channels, confirm that your organizational hierarchies are set up.  

For more information about creating organizational hierarchies, see [Organizational hierarchies](channels-org-hierarchies.md).

## Select a hierarchy

To select a hierarchy, follow these steps:

1. In the navigation pane, go to **Go to Navigation pane > Modules > Organization administration > Organizations > Organization hierarchies**.
1. From the list, select the organization hierarchy to which you want to add the channel.
1. On the action pane, select **View** to view hierarchy details.

The following image shows organizational hierarchy details for the selected hierarchy.

:::image type="content" source="media/channel-add-to-org-hierarchy-1.png" alt-text="Screenshot of organizational hierarchy details for the selected hierarchy.":::

## Add a channel to a hierarchy node

To add a channel to a hierarchy node, follow these steps:

1. On the action pane, select **Edit**.
1. Select the hierarchy node you want the channel added to. Then, from the **Insert** drop-down list, select **Retail Channel**. 
1. Select the channel to add, and then select **OK**.
1. On the action pane, select **Save**.
1. On the action pane, select **Publish** and provide an **Effective date** in the past to make this change take effect immediately.

The following image shows how to select a channel to add to a hierarchy node.

:::image type="content" source="media/channel-add-to-org-hierarchy-2.png" alt-text="Screenshot of selecting a channel to add to a hierarchy node.":::

The following image shows a hierarchy with various channels added.

:::image type="content" source="media/channel-add-to-org-hierarchy-3.png" alt-text="Screenshot of a hierarchy with various channels added.":::

## Additional resources

[Channels overview](channels-overview.md)

[Channel setup prerequisites](channels-prerequisites.md)

[Organizations and organizational hierarchies overview](../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md?toc=/dynamics365/commerce/toc.json)

[Plan your organizational hierarchy](../fin-ops-core/fin-ops/organization-administration/plan-organizational-hierarchy.md?toc=/dynamics365/commerce/toc.json)

[Organization hierarchies](channels-org-hierarchies.md)

[Set up a retail channel](channel-setup-retail.md)

[Set up an online channel](channel-setup-online.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
