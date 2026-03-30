---
title: Replace user IDs associated with tracked content changes
description: Learn how to replace user IDs that are associated with tracked content changes in Microsoft Dynamics 365 Commerce site builder.
author: BrianShook
ms.date: 02/19/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-04-13
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Replace user IDs associated with tracked content changes

[!include [banner](../includes/banner.md)]

This article describes how to replace user IDs that are associated with tracked content changes in Microsoft Dynamics 365 Commerce site builder.

In Dynamics 365 Commerce, the site builder authoring tool tracks changes that you make to items in the content management system (CMS). Therefore, you can view a document change history to help your team track their efforts when they collaborate on content. To assign user identities to tracked changes, the system uses user IDs from the Microsoft Entra identity management system. These user IDs are also the email addresses that Microsoft Entra ID issues. Commerce system admins can replace user ID references in the change tracking history logs in site builder as they require.

## Replace a user ID in site builder

To replace a user ID in site builder, follow these steps:

1. Go to the **Home** page for your site.
1. In the left navigation pane, expand **Tenant Settings**, and then select **Tracking Content Changes**.

    :::image type="content" source="../media/TrackingContentChanges.png" alt-text="Screenshot of Tracking Content Changes selected.":::

1. On the **Tracking Content Changes** page, select **Manage**.
1. In the **Replace email address** field, enter the user ID email address that you want to remove from the change tracking logs, and then select **Replace**. (You can enter multiple email addresses before you select **Replace**.)

    :::image type="content" source="../media/ReplaceEmailAddress.png" alt-text="Screenshot of email addresses entered in the Manage email address dialog box.":::

1. Select **OK**, and then select **Save**. A message box notifies you that the records for the user IDs that you entered are updated.

> [!NOTE]
> Site builder replaces every user ID email address with an anonymized, randomly generated string to remove all CMS references to the email address. This action affects only the history logs that are referenced in the specific e-Commerce environment (tenant) that is associated with the site builder instance.

## Additional resources

[Compliance overview](../compliance-overview.md)

[Accessibility features and capabilities](../accessibility.md)

[Cookie compliance](../cookie-compliance.md)

[Add a privacy policy page](../add-privacy-page.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
