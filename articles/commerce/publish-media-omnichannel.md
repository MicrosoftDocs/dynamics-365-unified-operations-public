---
title: Publish media assignments
description: This article describes how to publish media assignments using omnichannel media management in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 06/02/2023
ms.topic: overview
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2023-03-01

---

# Publish media assignments

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]
[!include[banner](../includes/production-ready-preview-banner.md)]

This article describes how to publish media assignments using omnichannel media management in Microsoft Dynamics 365 Commerce.

Publishing product and category media assignments involves several automatic, sequential steps that execute in the background. The content management system (CMS) first publishes all the media library items (images, videos, and documents) that are assigned to a product or category. This is the same as going to the Commerce site builder **Media library** and selecting **Publish** for each assigned media item. After the CMS publishes all media library items, each media item is assigned its own public CMS URL. Next, the product (or category) assignments and fallback defaults are flattened and stored in the headquarters SQL database via a batch job. Then, the headquarters data sync jobs push the flattened media assignments to Commerce Scale Unit (CSU) database(s) across configured channels. The CSU architecture has a two hour rolling cache for product and category merchandising data from its own database. 

The time it takes for product and category media assignments to appear for site users after a **Publish** action depends on the following factors:

- The number of media items and assignments for the publish action.
- The frequency of the headquarters omnichannel media batch job in headquarters.
- The frequency of the headquarters to CSU data sync jobs in headquarters.
- The default two hour cache for CSU merchandising data.

To publish product (or category) media assignments, follow these steps.

1. Navigate to the **Product media** assignments view in either site builder's **Omnichannel content** workspace, or to the same view in headquarters via the **Product media assignments** button in the released products by category view.
1. In the search box on the left, search for a product (or category) using its name or product ID, and then select it.
1. Check that the product (or category) isn't still being edited. If it's still being edited, and the edits are yours, then select **Finish editing** to check in the changes. If someone else is editing the media assignments, then then request that they check in their changes. Or, if necessary, select **Discard edits** to return to the previously checked-in media assignments.
1. Select **Publish**. For products, this will publish all draft media assignments in **Master**, **Dimensions**, and **Variants** for the selected product.
1. The first time you publish media assignments, you'll see a dialog box that explains the sequential publish behavior described earlier in this article. To skip seeing this dialog box during future publish actions, select the **Don't show this message again** checkbox, and then select **I understand**.
1. If the media assignments reference any unpublished CMS items, a dialog box appears that lists the unpublished dependencies. Select **Publish all** to publish the unpublished CMS item dependencies.

Once the media assignments are published, they will appear for channel-specific site users after the configured headquarters batch jobs, CSU data sync, and CSU cache schedule are completed.

## Use publish groups for media assignments

Omnichannel content (for example, product media assignments) can use site builder's publish group feature to trigger a publish action for a set of changes at a scheduled date and time. For more information about the publish group feature, see [Work with publish groups](publish-groups.md).

To use a publish group for product media assignments, follow these steps.

1. In the **Omnichannel content** workspace, in the left navigation pane, select **Publish groups**.
1. In the publish groups list view, select **New** on the command bar, enter a friendly name for your publish group, and then select **OK**.
1. In the navigation publish group context selector control on the left, select your new publish group. The default value is **Live site**.
1. In the left navigation pane, go to **Product media**.
1. Select and edit the product media assignments you want to stage inside the publish group. 

    > [!NOTE]
    > When you select **Edit product media** when working inside a publish group, the product media assignments are automatically added to the publish group context. You can see which products have been edited and added to the publish group by noting the yellow **Draft** tag that is shown next to each edited product media assignment.

1. When all edits are staged within the publish group, in the left navigation pane, go to **Publish groups** and schedule your publish date and time following the instructions in [Schedule a publish group to go live].(publish-groups.md#schedule-a-publish-group-to-go-live).

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Copy omnichannel content between tenants](copy-content-between-tenants.md)

[Work with publish groups](publish-groups.md)

[Schedule a publish group to go live].(publish-groups.md#schedule-a-publish-group-to-go-live)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
