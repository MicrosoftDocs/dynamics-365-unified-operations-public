---
title: Copy omnichannel content between tenants
description: This article describes how to copy content between tenants using omnichannel media management in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 5/26/2023
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

This article describes how to copy content between tenants using omnichannel media management in Microsoft Dynamics 365 Commerce.

Omnichannel content can be copied across tenants, much like site copies for individual websites in site builder. The copy process is always initiated from the destination tenant, by choosing a source tenant can be chosen to copy omnichannel content from.  The copy is performed by the CMS job service which can be monitored in from site builder's tenant view under **Tenant settings \> Jobs**.  The length of time to complete a copy is variable, and is dependent on the amount of content being copied.  If you wish to perform a partial copy or have the ability to audit which specific omnichannel media and product assignments are copied, it's recommended to use the media library's bulk import and export functionality instead of copy.

To copy all omnichannel content between two tenants, follow these steps:

1. From the **Sites** page within site builder's tenant view, select **Copy to** on the command bar, and then select **Omnichannel content** from the drop-down menu.
2. In the first **Tenant information** step, enter the **Source tenant** ID that you want to copy from and select **Next**.  If you don't know this string, it can normally be found in the source tenant's site builder URL immediately following the commerce.dynamics.com domain (example: ...commerce.dynamics.com/**[tenant ID]**/...).
3. Choose what behavior the copy job should use when it encounters existing files on the destination using the **Select a behavior for conflicting files** radio buttons.  **Keep destination files** will skip the copy operation for any files that already exist on the destination.  **Replace files in destination tenant** will always overwrite files in the destination, regardless of whether they already exist or not. **Keep latest version from either source or destination** will look at the last modified date for the file and keep whichever is more recent from either the source or destination.  If you're copying to an empty tenant, then any selection will work.
4. Choose whether to copy only the latest published version, or the latest published version and most recent draft from the **Select which document versions to copy** radio buttons.  Site copy doesn't currently copy all historical document versions, but does allow you to choose whether to copy the latest draft versions along with published versions.  If you only need the published versions, then this can save some time during the copy process.
5. On the **Channels and locales** step, validate that each **Source channel** is mapped to the correct **Destination channel**, and all **Source locale**(s) are mapped to the correct **Destination locale**(s) using the dropdown controls.  You can also remove any channels or locales that you do not wish to copy by selecting the **trash can** symbols next to each.  When finished mapping channels and locales from the source tenant to the destination tenant, select **Next**.
6. On the **Review and start copy** screen, review your selections, and then when ready select **Start copy job**.
7. To monitor the copy job progress, either: a) select the link in the job queue notification from the **Notifications (bell icon)** button in the upper right, or b) go to **Tenant settings** (lower left of navigation panel) > **Jobs**.  Job completion times will vary based on whether you have other tenant jobs in the queue, and the amount of content being copied.

## Additional resources

[Omnichannel media management overview](omnichannel-media-management-overview.md)

[Assign media to products and categories](assign-media-omnichannel.md)

[Publish media assignments](publish-media-omnichannel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
