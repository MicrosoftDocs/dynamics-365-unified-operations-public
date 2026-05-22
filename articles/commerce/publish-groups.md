---
title: Work with publish groups
description: Learn about the publish groups feature in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 01/28/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-12-12
ms.custom: 
  - bap-template
---

# Work with publish groups

[!include [banner](includes/banner.md)]

This article describes the publish groups feature in Microsoft Dynamics 365 Commerce.

E-commerce websites constantly update with new content throughout the year. Often, you publish updates in batches around busy e-commerce events such as holidays, seasonal marketing campaigns, or promotional launches. These updates often require that you stage, validate, and publish concurrently in a single action groups of website content (for examples, pages, images, fragments, and templates).

The ability to group items into logical sets that publish items together, where each set has its own lifecycle, provides many advantages to site authors. In Commerce, these logical sets are known as publish groups. They let site authors track sets of updates as their own configurable, testable, and publishable entities.

Authors can preview updates in a staged publish group without affecting the live site or other self-contained publish groups. Authors can then schedule the publish action to simultaneously publish all the items in the publish group to the live site. The ability to group, preview, and schedule updates for publishing is important for many enterprise-level companies that generate considerable annual revenue around event-based site update milestones.

Companies can incur costs from slow or invalidated content rollouts that don't go smoothly. Publish groups help guarantee that launches are organized, validated, and published on time. Whether they're large or small, publish groups provide a valuable toolset that helps authors organize and simplify ongoing site update tasks.

The following video provides an overview of the publish group feature.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=ee4b9a2c-3f68-4d61-bbf5-7058cddf04f8]

## When to use publish groups

Use publish groups whenever you must stage and publish multiple documents together. For example, if your website updates content every season, create publish groups for these seasonal marketing motions. Your "Autumn Seasonal Update" publish group might contain new seasonal images, fragments that have seasonal marketing messages, pages that include seasonal product collections, or other seasonal website updates.

An advantage of publish groups is that you can stage multiple updates in parallel. For example, soon after the update for the "Autumn Seasonal Update" publish group, there might be a content update for a specific holiday weekend. In this case, you can stage content for the "Autumn Seasonal Update" publish group at the same time that you stage content for a subsequent "Autumn Holiday Update" publish group. Each publish group contains its own unique set of pages, images, fragments, templates, and so on. You can stage, preview, and validate these two publish groups independently but on a concurrent timeline. Each publish group can then be scheduled to go live on your site at specific dates and times.

## Turn on the publish groups feature

For some legacy environments, you must manually turn on the publish groups feature in site builder for each site.

> [!NOTE]
> The publish groups feature is turned on by default for new site builder deployments. 

To turn on the publish groups feature for legacy sites in site builder, follow these steps:

1. In the left navigation pane, select **Site Settings** to expand it.
1. Under **Site Settings**, select **Features**.
1. Set the **Publish groups** option to **On**.

## Create a publish group

To create a publish group for your site in the Commerce authoring tools, follow these steps:

1. In the left navigation pane, select **Publish Groups**.
1. In the top command bar, select **New**.
1. In the **Create Publish Group** dialog box, under **Publish Group Name**, enter a descriptive name. Then select **OK**.

## Set the publish group authoring context

In Commerce, the default authoring context is the live site context. The live site authoring context is the default view where you can view and make changes directly to your website without using a publish group. It represents the latest direct updates to the published version of your site. If the context control under **Publish Groups** in the left navigation pane shows the name **Live site**, you're working in the live site authoring context. **Live site** is the default name of the context control. Otherwise, the context control shows the name of a publish group.

To work in a publish group, switch to the publish group authoring context. To set the publish group context, follow one of these steps.

- In the left navigation pane, select the context control directly under **Publish Groups**. Select the name of the publish group in the list of options that appears. The context control is renamed and shows the name of the publish group.
- In the left navigation pane, select **Publish Groups**. Under **Publish Groups**, select the name of the publish group. The context control is renamed and shows the name of the publish group.

After you set your publish group authoring context, you're working in that publish group context when you preview and edit site content.

To return to the default live site authoring context, select the context control, and then select **Live site**.

## Add pages or other items to a publish group

After you select a publish group authoring context, and the context control in the left navigation pane shows its name, you can create content just as you do in the default live site context. You can also add existing pages or other items from other publish groups, or from the live site context.

To copy existing pages to a publish group, follow these steps:

1. Select the authoring context to copy from. In the left navigation pane, select **Pages**.
1. Select the page to add to a publish group.
1. In the command bar, select **Copy to Publish group**.
1. In the **Select a Publish Group** dialog box, select the publish group to add the page to, and then select **OK**.

Use the same basic steps to create customized product pages, URLs, templates, layouts, fragments, and media library assets, or to add existing items of these types to a publish group.

## Validate a publish group

To make sure all dependencies in a publish group are satisfied and all validations pass, run validation to identify any problems you must fix before you schedule a publish action.

To validate your publish group before you schedule it, follow these steps:

1. In the left navigation pane, select **Publish Groups**.
1. Select the publish group to validate.
1. In the command bar, select **Validate**.

The portal runs validation on all content in the publish group. If any problems prevent a successful publish action, the portal shows them in a notification box that appears in the upper right.

> [!NOTE]
> The portal always runs validation automatically when you schedule a publish group. However, the **Validate** button in the command bar is useful because it helps identify problems that you must fix before you try to schedule a publish group to go live.

## Schedule a publish group to go live

To schedule a publish group to go live on your site, follow these steps:

1. In the left navigation pane, select **Publish Groups**.
1. Under **Publish Groups**, select the publish group to schedule.
1. In the command bar, select **Edit Schedule**. The **Edit Schedule** dialog box appears.
1. Select the date and time when your publish group should go live, and then select **OK**.

To unschedule a publish group, follow the same steps, but select **Unschedule publish group** in the **Edit Schedule** dialog box.

> [!NOTE]
> Large publish groups might take up to a minute or two to publish when their scheduled time arrives. Aware that a publish action isn't instantaneous, and that smaller publish groups publish faster.

## Publish groups FAQ

**How many items can a publish group contain?**

Currently, a publish group can contain up to 2,000 items. Large publish groups might take several minutes to publish when their scheduled time arrives.

**Are publish groups like code "branches" in software development terminology?**

Yes and no. You can think of publish groups as forked versions of your site. In that way, they act like branches. However, there's no concept of a merge at the level of individual items. The item that you publish last overwrites what previously existed. The most recent publish action always supersedes previous publish actions.

**Can I schedule two publish groups to go live at the same time?**

No. For performance and conflict reasons, the system requires you to stagger scheduled publish groups at least five minutes apart.

**Can I use publish groups to schedule omnichannel back-office items, such as discounts and product updates?**

Currently, the publish groups feature supports only website content. However, Microsoft is aware that integration with back-office merchandising scenarios could be valuable for the coordination and automation of omnichannel campaign launches.

## Additional resources

[Ways to add content](add-manage-content.md)

[Page model glossary](page-elements-overview.md)

[Document states and lifecycle](document-states-overview.md)

[Enable and use cross-channel sharing](cross-channel-sharing.md)

[Work with modules](work-with-modules.md)

[Work with fragments](work-with-fragments.md)

[Templates and layouts overview](templates-layouts-overview.md)

[Customize site navigation](customize-site-navigation.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
