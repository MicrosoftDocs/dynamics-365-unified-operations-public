---
title: Publish media assignments
description: This article describes how to publish media assignments by using omnichannel media management in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 06/09/2023
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

This article describes how to publish media assignments by using omnichannel media management in Microsoft Dynamics 365 Commerce.

Publication of product and category media assignments involves several automatic, sequential steps that run in the background. The content management system (CMS) first publishes all the media library items (images, videos, and documents) that are assigned to a product or category. This process has the same result as going to the Commerce site builder media library and selecting **Publish** for each assigned media item. After the CMS publishes all media library items, each media item is assigned its own public CMS URL. Next, the product (or category) assignments and fallback defaults are flattened and stored in the headquarters SQL database via a batch job. The headquarters data synchronization jobs then push the flattened media assignments to Commerce Scale Unit (CSU) databases across configured channels. The CSU architecture has a two-hour rolling cache for product and category merchandising data from its own database.

The time that product and category media assignments take to appear for site users after a **Publish** action depends on the following factors:

- The number of media items and assignments for the **Publish** action
- The frequency of the headquarters omnichannel media batch job in headquarters
- The frequency of the headquarters-to-CSU data sync jobs in headquarters
- The default two-hour cache for CSU merchandising data

To publish product (or category) media assignments, follow these steps.

1. In the site builder **Omnichannel content** workspace, open the **Product media** assignment view. Alternatively, you can open the same view in headquarters by selecting **Product media assignments** in the **Released products by category** view (**Modules \> Retail and Commerce \> Products and categories \> Released products by category**).
1. In the search field on the left, search for a product (or category) by its name or product ID. Then select it.
1. Confirm that the product (or category) isn't still being edited. If it's still being edited, and the edits are yours, select **Finish editing** to check in the changes. If someone else is editing the media assignments, request that they check in their changes. Or, if necessary, select **Discard edits** to return to the previously checked-in media assignments.
1. Select **Publish**. For products, this action publishes all draft media assignments in **Master**, **Dimensions**, and **Variants** for the selected product.
1. The first time that you publish media assignments, a message box explains the sequential publication behavior that was described earlier in this article. To prevent this message box from appearing during future **Publish** actions, select the **Don't show this message again** checkbox, and then select **I understand**.
1. If the media assignments reference any unpublished CMS items, a dialog box lists the unpublished dependencies. Select **Publish all** to publish the unpublished CMS item dependencies.

The published media assignments will appear for channel-specific site users after the configured headquarters batch jobs, CSU data synchronization, and CSU cache schedule are completed.

## Use publish groups for media assignments

Omnichannel content (for example, product media assignments) can use site builder's publish group feature to trigger a **Publish** action for a set of changes at a scheduled date and time. For more information about the publish group feature, see [Work with publish groups](publish-groups.md).

To use a publish group for product media assignments, follow these steps.

1. In the **Omnichannel content** workspace, on the left navigation pane, select **Publish groups**.
1. In the publish groups list view, on the command bar, select **New**. Enter a friendly name for the publish group, and then select **OK**.
1. In the navigation publish group context selector control on the left, select the new publish group. The default value is **Live site**.
1. On the left navigation pane, go to **Product media**.
1. Select and edit the product media assignments that you want to stage inside the publish group.

    > [!NOTE]
    > If you select **Edit product media** while you're working inside a publish group, the product media assignments are automatically added to the publish group context. A yellow **Draft** tag next to each edited product media assignment indicates which products have been edited and added to the publish group.

1. When all edits are staged inside the publish group, on the left navigation pane, go to **Publish groups**. Schedule a publication date and time by following the instructions in [Schedule a publish group to go live](publish-groups.md#schedule-a-publish-group-to-go-live).

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Copy omnichannel content between tenants](copy-content-between-tenants.md)

[Bulk import and export digital assets using manifests](import-export-manifest.md)

[Work with publish groups](publish-groups.md)

[Schedule a publish group to go live](publish-groups.md#schedule-a-publish-group-to-go-live)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
