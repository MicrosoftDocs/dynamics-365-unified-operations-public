---
title: Work with publish groups
description: This article describes the publish groups feature in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 08/01/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2019-12-12

---

# Work with publish groups

[!include [banner](includes/banner.md)]

This article describes the publish groups feature in Microsoft Dynamics 365 Commerce.

E-commerce websites are constantly updated with new content throughout the year. Updates are often published in batches around busy e-commerce events such as holidays, seasonal marketing campaigns, or promotional launches. These updates often require that groups of website content (for examples, pages, images, fragments, and templates) be staged, validated, and published concurrently in a single action.

The ability to group items into logical sets that publish items together, where each set has its own lifecycle, provides many advantages to site authors. In Commerce, these logical sets are known as publish groups. They let site authors track sets of updates as their own configurable, testable, and publishable entities.

Authors can preview updates in a staged publish group without affecting the live site or other self-contained publish groups. Authors can then schedule the publish action to simultaneously publish all the items in the publish group to the live site. The ability to group, preview, and schedule updates for publishing is important for many enterprise-level companies that generate considerable annual revenue around event-based site update milestones.

Companies can incur costs from slow or invalidated content rollouts that don't go smoothly. Publish groups help guarantee that launches are organized, validated, and published on time. Whether they are large or small, publish groups provide a valuable toolset that helps authors organize and simplify ongoing site update tasks.

The following video provides an overview of the publish group feature.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW17VjZ]

## When to use publish groups

You can use publish groups whenever you must stage and publish multiple documents together. For example, if your website updates content every season, you can create publish groups for these seasonal marketing motions. Your "Autumn Seasonal Update" publish group might contain new seasonal images, fragments that have seasonal marketing messages, pages that include seasonal product collections, or other seasonal website updates.

An advantage of publish groups is that you can stage multiple updates in parallel. For example, soon after the update for the "Autumn Seasonal Update" publish group, there might be a content update for a specific holiday weekend. In this case, you can stage content for the "Autumn Seasonal Update" publish group at the same time that you stage content for a subsequent "Autumn Holiday Update" publish group. Each publish group contains its own unique set of pages, images, fragments, templates, and so on. You can stage, preview, and validate these two publish groups independently but on a concurrent timeline. Each publish group can then be scheduled to go live on your site at specific dates and times.

## Turn on the publish groups feature

For some legacy environments, you must manually turn on the publish groups feature in site builder for each site.

> [!NOTE]
> The publish groups feature is turned on by default for new site builder deployments. 

To turn on the publish groups feature for legacy sites in site builder, follow these steps.

1. In the left navigation pane, select **Site Settings** to expand it.
1. Under **Site Settings**, select **Features**.
1. Set the **Publish groups** option to **On**.

## Create a publish group

To create a publish group for your site in the Commerce authoring tools, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. In the top command bar, select **New**.
1. In the **Create Publish Group** dialog box, under **Publish Group Name**, enter a descriptive name. Then select **OK**.

## Set the publish group authoring context

In Commerce, the default authoring context is the live site context. The live site authoring context is the default view where you can view and make changes directly to your website without using a publish group. It represents the latest direct updates to the published version of your site. If the context control under **Publish Groups** in the left navigation pane shows the name **Live site**, you're working in the live site authoring context. **Live site** is the default name of the context control. Otherwise, the context control shows the name of a publish group.

To work in a publish group, you must switch to the publish group authoring context for it. To set the publish group context, follow one of these steps.

- In the left navigation pane, select the context control directly under **Publish Groups**, and then select the name of the publish group in the list of options that appears. The context control is renamed and shows the name of the publish group.
- In the left navigation pane, select **Publish Groups**, and then, under **Publish Groups**, select the name of the publish group. The context control is renamed and shows the name of the publish group.

After you set your publish group authoring context, you're working in that publish group context when you preview and edit site content.

To return to the default live site authoring context, select the context control, and then select **Live site**.

## Add pages or other items to a publish group

After you've selected a publish group authoring context, and the context control in the left navigation pane shows its name, you can create content just as you do in the default live site context. You can also add existing pages or other items from other publish groups, or from the live site context.

To copy existing pages to a publish group, follow these steps.

1. Select the authoring context to copy from, and then, in the left navigation pane, select **Pages**.
1. Select the page to add to a publish group.
1. In the command bar, select **Copy to Publish group**.
1. In the **Select a Publish Group** dialog box, select the publish group to add the page to, and then select **OK**.

You can use the same basic steps to create customized product pages, URLs, templates, layouts, fragments, and media library assets, or to add existing items of these types to a publish group.

## Validate a publish group

To make sure that all dependencies in publish group content are satisfied, and that all validations are passed, you can run validation to identify any issues that must be addressed before you schedule a publish action.

To validate your publish group before you schedule it, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. Select the publish group to validate.
1. In the command bar, select **Validate**.

Validation is run on all content in the publish group. Any issues that will prevent a successful publish action are shown in a notification box that appears in the upper right.

> [!NOTE]
> Validation is always run automatically when a publish group is scheduled. However, the **Validate** button in the command bar is useful because it helps identify issues that you must fix before you try to schedule a publish group to go live.

## Schedule a publish group to go live

To schedule a publish group to go live on your site, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. Under **Publish Groups**, select the publish group to schedule.
1. In the command bar, select **Edit Schedule**. The **Edit Schedule** dialog box appears.
1. Select the date and time when your publish group should go live, and then select **OK**.

To unschedule a publish group, follow the same steps, but select **Unschedule publish group** in the **Edit Schedule** dialog box.

> [!NOTE]
> Very large publish groups might take up to a minute or two to be published when their scheduled time arrives. Be aware that a publish action isn't instantaneous, and that smaller publish groups will be published faster.

## Publish groups FAQ

**How many items can be in a publish group?**

Currently, there is a limit of 2,000 items per publish group. Be aware that very large publish groups might take several minutes to be published when their scheduled time arrives.

**Are publish groups like code "branches" in software development terminology?**

Yes and no. Publish groups can be thought of as forked versions of your site. In that way, they do act like branches. However, there is no concept of a merge at the level of individual items. The item that is published last just overwrites what previously existed, and the most recent publish action always supersedes previous publish actions.

**Can I schedule two publish groups to go live at the same time?**

No. For performance and conflict reasons, the system will force you to stagger scheduled publish groups at least five minutes apart.

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
