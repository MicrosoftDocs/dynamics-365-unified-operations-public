---
title: Copy omnichannel content between tenants
description: This article describes how to copy content between tenants using omnichannel media management in Microsoft Dynamics 365 Commerce.
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

This article describes how to copy content between tenants using omnichannel media management in Microsoft Dynamics 365 Commerce.

Omnichannel content can be copied across tenants, much like the site copy operation for individual websites in Commerce site builder. The copy process is always initiated from the destination tenant, where you specify a source tenant from which to copy omnichannel content. The copy operation is performed by the CMS job service which can be monitored from site builder's tenant view under **Tenant settings \> Jobs**. The time it takes to complete a copy operation varies, and is dependent on the amount of content being copied. If you want to perform a partial copy or have the ability to audit which specific omnichannel media and product assignments that you copy, Microsoft recommends that you instead use the media library's bulk import and export functionality instead of the copy operation.

To copy all the omnichannel content from one tenant to another, follow these steps.

1. From the **Sites** page within site builder's tenant view, select **Copy to** on the command bar, and then select **Omnichannel content** from the drop-down menu.
2. In the first **Tenant information** step, enter the **Source tenant** ID that you want to copy from, and then select **Next**. If you don't know the source tenant ID string, it can usually be found in the source tenant's site builder URL, immediately following the `commerce.dynamics.com` domain (for example, `...commerce.dynamics.com/<tenant ID>/...`).
3. Choose what behavior the copy job should use when it encounters existing files on the destination using one of the **Select a behavior for conflicting files** radio buttons. If you're copying to an empty tenant, any selection will work.
    - **Keep destination files** - Skips the copy operation for any files that already exist at the destination.
    - **Replace files in destination tenant** - Always overwrite files at the destination, regardless of whether they already exist or not.
    - **Keep latest version from either source or destination** - Compares the last modified dates for the source and destination files and keeps the most recent file.  
5. Choose whether to copy only the latest published version, or the latest published version and most recent draft using the **Select which document versions to copy** radio buttons. The site copy operation doesn't currently copy all historical document versions, but does allow you to choose whether to copy the latest draft versions along with published versions. If you only need the published versions, this option can save some time during the copy process.
6. On the **Channels and locales** step, validate that each **Source channel** is mapped to the correct **Destination channel**, and that all **Source locale**(s) are mapped to the correct **Destination locale**(s) using the drop-down menus. You can also remove any channels or locales that you do not wish to copy by selecting the trash can symbols next to each item. When finished mapping channels and locales from the source tenant to the destination tenant, select **Next**.
7. On the **Review and start copy** screen, review your selections, and then when you are ready to copy, select **Start copy job**.
8. To monitor the copy job progress, you can either select the link in the job queue notification from **Notifications** (bell icon) on the upper right, or on the lower left of navigation pane, go to **Tenant settings \> Jobs**. Job completion times will vary based on whether you have other tenant jobs in the queue, and the amount of content being copied.

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
