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
# Publish groups and scheduled publishes

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic describes why, when, and how to use the publish groups feature in Microsoft Dynamics 365 Commerce.

## Overview

E-commerce websites are constantly updated with new content throughout the year, and updates are often published in batches around busy e-commerce events such as holidays, seasonal marketing campaigns, or promotional launches. These updates often require groups of website content (pages, images, fragments, templates, etc.) to be staged, validated, and concurrently published in a single action. 

Grouping items into logical sets that need to publish together, each set with its own lifecycle, provides many advantages to site authors. These groupings, referred to in Commerce as "publish groups," enable site authors to track a whole set of updates as its own author-able, testable, and publishable entity. 

Authors can preview broad updates within a staged publish group without affecting the live site or other self-contained publish groups.  
Authors can then schedule the publish action to simultaneously publish all items contained within the publish group to the live site.  

This is incredibly important for many enterprise level companies that generate considerable annual revenue around event-based site update milestones.  

Slow or invalidated content rollouts can have big opportunity costs when they don’t go smoothly, and publish groups provide a solution to ensure launches are organized, validated, and publish on-time.  

Large or small, publish groups and scheduled publish features provide a valuable tool set for authors to organize and simplify ongoing site update tasks.

## When to use publish groups

Use publish groups whenever you need to stage and publish multiple documents together.  For example, if your website updates content seasonally, you can create publish groups for these seasonal marketing motions. Your "Autumn Season Update" publish group might contain new seasonal images, fragments with seasonal marketing messages, pages with seasonal product collections, or other seasonal website updates.  

Another advantage of publish groups is that you can stage multiple updates in parallel.  To build on the previous example, quickly after an autumn update there might also be a specific holiday weekend content update.  You can stage content for the  "Autumn Seasonal Update" publish group at the same time you are staging a fast-follow "Autumn Holiday Update" publish group.  Each publish group can contain its own distinct version of pages, fragments, etc.  You can stage, preview, and validate these two publish groups independently, but on a concurrent timeline.  Each publish group can then be scheduled to go live on your site at a specific dates and times.  

## Enable publish group feature flag in Site Builder settings

The publish groups capability is optional and must be enabled for your site through a feature switch in Site Builder's settings.  To enable publish groups, follow these steps for a site within the Site Builder tool:

1. Expand the **Site Settings** in the left navigation panel.
2. Select **Features** from the options.
3. Toggle the **Publish groups** feature switch control to the **On** setting.

## Create a publish group

To create a publish group, follow these steps:

1. In the left navigation panel, select **Publish groups**.
2. In the top command bar, click the **New** button.
3. Enter a descriptive name in the dialog and click the **Ok** button.

## Work within the context of a publish group

You can select your publish group context in one of two ways:

* The first option is to click on the Site Builder context control (directly below **Publish Groups**) in the left navigation panel, and select your desired authoring context.  This is also where you can return to your default **Live site** context.

  >[!Note]
  >The "Live site" context is the default view where you can view and make changes directly to your website without using a publish group. The "Live site" context  represents the latest direct updates to the published version of your site.

* The second option is to simply click on the name of the publish group in the list view shown by selecting **Publish groups** from the left navigation menu.  This will also set the publish group context in the left navigation context control mentioned above.

Once you have set your context, which will show either "Live site" or the name of your chosen publish group in the left navigation menu, you will be operating within that context for previewing and editing site content. 

## Add items to a publish group

Once you have selected a publish group context and see this in the left navigation panel, you can create content just as you would in the default "Live site" context.  You can also add existing pages from other publish groups or from the default "Live site" context.  To copy existing pages to a publish group, follow these steps:

1. After selecting either the "Live site" context or a different publish group context, select **Pages** from the left navigation panel.
2. Select the page you want to add to a publish group.
3. Click the **Copy to publish group** button in the top command bar.
4. Select the publish group you wish to add the page into and click **Ok**.

The same steps above can be used to create or add existing customized product pages, URLs, templates, layouts, fragments, and media library assets to a publish group.

## Validate a publish group

To ensure that all content dependencies and validations are ok to publish, you can run a pre publish validation to identify any issues that need to be addressed before you can schedule a publish.  To validate your publish group, follow these steps:

1. Select **Publish groups** from the left navigation panel.
2. Select the publish group you wish to validate.
3. Click the **Validate** button in the top command bar.

A validation check will be run across all content in the publish group, and any issues that would prevent successful publish will be displayed in the notification dialogs in the top right.

>[!NOTE]
>Validation will always automatically run when scheduling a publish group. The designated "Validate" button is helpful to identify issues early, before attempting to schedule a publish group to go live.
## Schedule a publish group to go live
To schedule a publish group to go live on your site, follow these steps:

1. Select **Publish groups** from the left navigation panel.

2. Select the publish group you wish to schedule.

3. Click the **Publish schedule** button in the top command bar.

4. Select the date and time for your publish group to go live on your website.

5. Click the **Ok** button.

>[!NOTE]
>To un-schedule a publish group, follow the same steps above and click the "Un-schedule publish group" option in the scheduling modal window.
>[!NOTE]
>Very large publish groups may take up to a minute or two to complete when their scheduled time arrives.  Be aware that a publish action is not instant, and smaller publish groups will publish faster.
## Publish groups FAQ

Q: How many items can be in a publish group?

A: At this time, there is a limit of 2,000 items per publish group.  Be aware that very large publish groups may take several minutes to publish at their scheduled time.



Q: Are publish groups like code 'branches' in software development terminology?

A: Yes and no.  Publish groups do act like branches in that they can be though of as forked versions of your site.  However, there is no concept of a merge at the individual item level.  The last published item simply over-writes what was previously there, and last publish always wins.



Q: Can I schedule two publish groups to go live at the exact same time?

A: Not at this time.  The system will currently force you to stagger scheduled publish groups at least 5 minutes apart for performance and conflict reasons.



Q: Can I schedule omnichannel back office items though publish groups, like discounts and product updates?

A: Currently publish groups support website content only, but we are fully aware of the value that integration with back office merchandising scenarios would bring to omnichannel campaign launch coordination and automation.
