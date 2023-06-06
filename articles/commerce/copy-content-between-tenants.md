---
title: Copy omnichannel content between tenants
description: This article describes how to copy content between tenants by using omnichannel media management in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 06/02/2023
ms.topic: overview
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2023-03-01

---

# Copy omnichannel content between tenants

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]
[!include[banner](../includes/production-ready-preview-banner.md)]

This article describes how to copy content between tenants by using omnichannel media management in Microsoft Dynamics 365 Commerce.

Omnichannel content can be copied across tenants. This copy operation resembles the site copy operation for individual websites in Commerce site builder. The process is always initiated from the destination tenant, where you specify the source tenant to copy omnichannel content from.

The copy operation is performed by the content management system (CMS) job service, which you can monitor the CMS job service from site builder's tenant view, at **Tenant settings \> Jobs**. The time that's required to complete the copy operation depends on the amount of content that's being copied.

If you want to do a partial copy or audit the specific omnichannel media and product assignments that you copy, we recommend that you use the media library's bulk import and export functionality instead of the copy operation.

To copy all the omnichannel content from one tenant to another, follow these steps.

1. In site builder's tenant view, on the **Sites** page, on the command bar, select **Copy to** \> **Omnichannel content**.
1. In the **Tenant information** step, enter the ID of the source tenant that you want to copy from, and then select **Next**. If you don't know the source tenant ID, it's usually immediately after the `commerce.dynamics.com` domain in the source tenant's site builder URL (for example, `...commerce.dynamics.com/<tenant ID>/...`).
1. In the **Select a behavior for conflicting files** field group, select one of the following options to specify what the copy job should do if it encounters existing files in the destination. If you're copying to an empty tenant, any option will work.

    - **Keep destination files** – Skip the copy operation for any files that already exist in the destination.
    - **Replace files in destination tenant** – Always overwrite files in the destination, regardless of whether they already exist.
    - **Keep latest version from either source or destination** – Compare the date when the source and destination files were last modified, and keep only the most recent files.

1. In the **Select which document versions to copy** field group, select an option to specify whether the copy job should copy only the latest published version, or both the latest published version and the most recent draft. The site copy operation doesn't currently copy all historical document versions, but it does let you choose whether the latest draft version is published together with published versions. If you only need the published versions, this option can help save time during the copy process.
1. In the **Channels and locales** step, confirm that each source channel is mapped to the correct destination channel, and that all source locales are mapped to the correct destination locales. You can remove any channels or locales that you don't want to copy by selecting the trash can symbol next to each item. When you've finished mapping channels and locales from the source tenant to the destination tenant, select **Next**.
1. In the **Review and start copy** step, review your selections, and then, when you're ready to copy, select **Start copy job**.
1. To monitor the progress of the copy job, select the notifications button (bell symbol) in the upper right, and then select the link in the job queue notification. Alternatively, in the lower left of the navigation pane, go to **Tenant settings \> Jobs**. Job completion times depend on whether other tenant jobs are in the queue and on the amount of content that's being copied.

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
