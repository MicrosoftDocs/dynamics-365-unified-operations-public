---
title: Publish media assignments
description: This article describes how to publish media assignments using omnichannel media management in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 5/10/2023
ms.topic: overview
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2023-03-01

# Publish media assignments

[!include[banner](../includes/banner.md)]

This article describes how to publish media assignments using omnichannel media management in Microsoft Dynamics 365 Commerce.

Publishing product and category media assignments involves several automatic sequential steps that happen in the background. The content management system (CMS) first publishes all the media library items (images, videos, documents, etc.) that are assigned to a product or category. This is the same as going to the **Media library** and clicking **Publish** for each assigned media item. After this step, the individual media items each have public CMS URLs. Next, the product (or category) assignments and fallback defaults are flattened and stored in the headquarters SQL database via batch job. Then, the headquarters data-sync jobs push the flattened media assignments to Commerce Scale Unit (CSU) database(s) across configured channels. The CSU architecture has a two-hour rolling cache for product and category merchandising data from its own database. To summarize, the time for product and category media assignments to appear for end users after a **Publish** action depends on these factors: 1) the number of media items and assignments for the publish action, 2) the frequency of the headquarters omnichannel media batch job in headquarters, 3) the frequency of the headquarters -> CSU data sync jobs in headquarters, 4) the default 2-hour cache for CSU merchandising data.

To publish product (or category) media assignments, follow these steps:
1. Navigate to the **Product media** assignments view in either **site builder's** **Omnichannel content** workspace, or to the same view in headquarters via the **Product media assignments** button in the released products by category view.
2. Search for a product (or category) using its name or product ID in the search view on the left, and select it.
3. Ensure that the product (or category) isn't still being edited.  If it's still being edited, and the edits are yours, then click the **Finish editing button** to check in the changes to the CMS.  If someone else is editing the media assignments, then ask them to check in their changes (or if necessary, you can **Discard edits** to return to the previously checked-in media assignments).
4. Click the **Publish** button on the action bar at the top.  For products, this will publish all draft media assignments in **Master**, **Dimensions**, and **Variants** for the selected product.
5. The first time you publish media assignments you'll see a dialog explaining the sequential publish behavior described in the [paragraph above](#publish-media-assignments). To skip this dialog for future publish actions, select the **Don't show this message again** checkbox, and then click the **I understand** button.
6. If the media assignments reference any unpublished CMS items, you'll see a dialog listing the unpublished dependencies.  Click the **Publish all** to automatically publish the unpublished CMS item dependencies.
7. The assignments are now **Published**, and will appear for channel-specific end-users after the configured headquarters batch jobs, CSU data-sync, and CSU cache schedule are completed.

## Use publish groups for media assignments

Omnichannel content (example: **Product media** assignments) can use site builder's publish group feature to trigger a publish action for a set of changes at a scheduled date and time.  For more information about the publish group feature, see [Work with publish groups](../publish-groups.md).

To use a publish group for product media assignments, follow these steps:
1. In the **Omnichannel content** workspace, click **Publish groups** in the left navigation panel.
2. In the publish groups list view, click the **New** button in the top action bar, enter a friendly name for your publish group, and click **Ok**.
3. In the left navigation publish group context selector control (the default will be **Live site**), select your new publish group.  
4. Go to **Product media** in the left navigation panel.
5. Select and edit the product media assignments you wish to stage inside the publish group as you would normally. 

    > [!NOTE]
    > By clicking the **Edit product media** button when working inside a publish group, the product media assignments are automatically added to the publish group context.  You can see which products have been edited and added to the publish group by noting the yellow **Draft** tag that is shown next to each edited product media assignment.

6. When all edits are staged within the publish group, go to **Publish groups** in the left navigation panel and schedule your publish date and time using the same instructions explained in the [Schedule a publish group to go live].(../publish-groups.md#schedule-a-publish-group-to-go-live) article.

## Additional resources