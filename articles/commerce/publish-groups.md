---
# required metadata

title: Work with publish groups
description: This topic describes why, when, and how to use the publish groups feature in Microsoft Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry:
ms.author: niholman
ms.search.validFrom: 2019-12-02
ms.dyn365.ops.version: Release 10.0.5

---
# Work with publish groups

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes why, when, and how to use the publish groups feature in Microsoft Dynamics 365 Commerce.

## Overview

E-commerce websites are constantly updated with new content throughout the year, and updates are often published in batches around busy e-commerce events such as holidays, seasonal marketing campaigns, or promotional launches. These updates often require groups of website content (pages, images, fragments, templates, etc.) to be staged, validated, and published concurrently in a single action. 

Grouping items into logical sets that publish items together, with each set having its own lifecycle, provides many advantages to site authors. These groupings, referred to in Commerce as "publish groups," enable site authors to track sets of updates as their own configurable, testable, and publishable entities.

Authors can preview updates within a staged publish group without affecting the live site or other self-contained publish groups. Authors can then schedule the publish action to simultaneously publish all items contained within the publish group to the live site. The ability to group, preview, and schedule updates for publishing is important for many enterprise-level companies that generate considerable annual revenue around event-based site update milestones.  

Slow or invalidated content rollouts can incur costs when they don't go smoothly, and publish groups provide a solution to ensure that launches are organized, validated, and published on time. Large or small, publish groups provide a valuable tool set for authors to organize and simplify ongoing site update tasks.

## When to use publish groups

You can use publish groups whenever you need to stage and publish multiple documents together. For example, if your website updates content seasonally, you can create publish groups for these seasonal marketing motions. Your "Autumn Seasonal Update" publish group might contain new seasonal images, fragments with seasonal marketing messages, pages with seasonal product collections, or other seasonal website updates.  

Another advantage of publish groups is that you can stage multiple updates in parallel. To build on the previous "Autumn Seasonal Update" example, soon after the update there might also be a specific holiday weekend content update. You could stage content for the  "Autumn Seasonal Update" publish group at the same time you are staging a subsequent "Autumn Holiday Update" publish group. Each publish group would contain its own unique set of pages, images, fragments, templates, etc. You could stage, preview, and validate these two publish groups independently, but on a concurrent timeline. Each publish group could then be scheduled to go live on your site at specific dates and times.  

## Enable the publish group feature

The publish groups capability is optional and must be enabled for your site.

To enable publish groups for your site in Commerce authoring tools, follow these steps.

1. In the left navigation pane, select **Site Settings** to expand it.
1. Under **Site Settings**, select **Features**.
1. Set the **Publish groups** toggle key to the **On** setting.

## Create a publish group

To create a publish group for your site in Commerce authoring tools, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. In the top command bar, select **New**.
1. In the **Create Publish Group** dialog box, enter a descriptive name under **Publish Group Name**, then click **OK**.

## Work within the context of a publish group

You can select your publish group context in one of two ways:

- The first option is to click on the Site Builder context control (directly below **Publish Groups**) in the left navigation panel, and select your desired authoring context. This is also where you can return to your default **Live site** context.

  >[!Note]
  >The "Live site" context is the default view where you can view and make changes directly to your website without using a publish group. The "Live site" context represents the latest direct updates to the published version of your site.

- The second option is to simply click on the name of the publish group in the list view shown by selecting **Publish groups** from the left navigation menu.  This will also set the publish group context in the left navigation context control mentioned above.

Once you have set your context, which will show either "Live site" or the name of your chosen publish group in the left navigation menu, you will be operating within that context for previewing and editing site content. 

## Add pages or other items to a publish group

Once you have selected a publish group context and it appears in the left navigation pane, you can create content just as you would in the default "Live site" context. You can also add existing pages or other items from other publish groups or from the default "Live site" context.

To copy existing pages to a publish group, follow these steps.

1. After selecting either the "Live site" context or a different publish group context, select **Pages** from the left navigation pane.
1. Select the page you want to add to a publish group.
1. In the command bar, select **Copy to Publish group**.
1. In the **Select a Publish Group** dialog box, select the publish group you wish to add the page to, and then click **OK**.

The same steps above can be used to create or add existing customized product pages, URLs, templates, layouts, fragments, and media library assets to a publish group.

## Validate a publish group

To ensure that all publish group content dependencies and validations are cleared to publish, you can run pre-publish validation to identify any issues that need to be addressed before you schedule a publish. 

To validate your publish group before scheduling, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. Select the publish group you want   to validate.
1. Select **Validate** in the top command bar.

A validation check will then be run on all content in the publish group, and any issues that would prevent a successful publish will be displayed in a notification box that appears on the top right.

>[!NOTE]
>Validation will always run automatically when scheduling a publish group. The command bar **Validate** functionality is helpful to identify issues to be fixed before attempting to schedule a publish group to go live.

## Schedule a publish group to go live

To schedule a publish group to go live on your site, follow these steps.

1. In the left navigation pane, select **Publish Groups**.
1. Under **Publish Groups**, select the publish group you want to schedule.
1. In the command bar, select **Edit Schedule**. The **Edit Schedule** dialog box appears.
1. Select the date and time for your publish group to go live, and then click **OK**.

To unschedule a publish group, follow the same steps above and click **Unschedule publish group** in the **Edit Schedule** dialog box.

>[!NOTE]
>Very large publish groups may take up to a minute or two to complete when their scheduled time arrives. Be aware that a publish action is not instant, and smaller publish groups will publish faster.

## Publish groups FAQ

#### Q: How many items can be in a publish group?

A: At this time, there is a limit of 2,000 items per publish group. Be aware that very large publish groups may take several minutes to publish at their scheduled time.

#### Q: Are publish groups like code "branches" in software development terminology?

A: Yes and no. Publish groups do act like branches in that they can be thought of as forked versions of your site. However, there is no concept of a merge at the individual item level. The last published item simply overwrites what was previously there, and the most recent publish always supercedes previous publishes.

#### Q: Can I schedule two publish groups to go live at the exact same time?

A: Not at this time. The system will force you to stagger scheduled publish groups at least 5 minutes apart for performance and conflict reasons.

#### Q: Can I schedule omnichannel back office items such as discounts and product updates using publish groups?

A: Currently publish groups functionality supports website content only, but there is awareness of the value that integration with back office merchandising scenarios would bring to omnichannel campaign launch coordination and automation.
