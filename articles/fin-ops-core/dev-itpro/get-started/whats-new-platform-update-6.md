---
title: What's new or changed in Dynamics 365 for Operations platform update 6 (April 2017)
description: Learn about new or changed features in Dynamics 365 for Operations platform update 6. This version was released in April 2017.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.dyn365.ops.version: Platform update 6
ms.assetid: 13d2b8a5-c2e0-4f32-a43b-7726ae20392c
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Operations platform update 6 (April 2017)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Dynamics 365 for Operations platform update 6. This version was released in April 2017 and has a build number of 7.0.4509.16180.

## Browser framework – Power Apps Host control

Dynamics 365 for Operations introduces a new control for developers, the Microsoft Power Apps Host control. This control allows a developer to host or embed a Power App within a Dynamics 365 for Operations form. For more details, see [Power Apps Host control](../user-interface/powerapps-host-control.md).

## Browser client – Ability to model toolbar actions in the overflow menu

You can now provide a cleaner action story on forms by designating certain buttons in toolbars to always render in overflow. This makes it easier to differentiate actions that users will commonly use versus those that are infrequently or rarely used. To utilize this feature, try the new **AlwaysInOverflow** metadata property on Button groups inside Toolbars.

## Build automation – Automatic update of model version during build

During an automated build, versions of models that are being built are updated to reflect the build number. This allows customers the ability to trace the model versions in the Dynamics 365 for Operations About window back to the build history in Azure DevOps.

## Build automation – Option to include runtime packages in the deployable package of the automated build output

A new option in the build definition instructs the automated build to include any source-controlled runtime packages in the deployable package that is generated for the build output. This allows customers to deploy one package, generated by the automated build, that includes both custom code as well as runtime packages supplied by third parties, such as ISVs.

## Document management – Attachment storage cleanup

When Dynamics AX 7.0 was released, the database storage for attachments was deprecated; however, some platform functionality remained that needed to be migrated. In Dynamics 365 for Operations platform update 6, the last remaining platform usage was removed and a migration button was added to the **Document Management Parameters** form. The migration button can be used to clean up any files that might remain in the database after an upgrade. The migration will migrate any attachments stored in the database to Blob storage. For more information, see [Apply the latest platform update to environments](../migration-upgrade/upgrade-latest-platform-update.md).

## Number sequence scope extensibility

You can now extend the number sequence scope through extensions. The scope of a number sequence defines which organization uses the number sequence. The scope can be combined with fiscal calendar periods to create even more specific number sequences. For more information, see [Extend the scope of number sequences](../extensibility/extend-number-sequence-scope.md).

## Mobile

- Added the ability to set workspace visibility for different user groups.

    - Mobile users will not see pages that they do not have access to in the underlying form in the web client. Before Platform update 6, users could see empty mobile workspaces if they did not have access to any of the pages. Also, the visibility of an entire workspace for a group of users could not be modified.
    - New security attributes and APIs are introduced, making it easy to declare visibility of a mobile workspace based on menu items. These APIs can be used to override mobile workspace access for specific user groups.

- Added the ability to auto detect required attributes, through form and table metadata, to denote mobile fields as mandatory during data entry. Action data cannot be submitted to the server if values for the required fields are not provided. (Requirement: Platform update 6 and Mobile April release.)
- Option to fully localize mobile workspaces for all Dynamics 365 for Operations supported languages.

## Ideas portal

Dynamics 365 for Operations Ideas forum is now available on our [Ideas portal](https://experience.dynamics.com/ideas/). With the Ideas portal, all Dynamics 365 for Operations users can submit new ideas, vote on existing ideas, and track status of their ideas in a consistent manner. This can now be achieved from both outside of the product ([https://experience.dynamics.com/ideas](https://experience.dynamics.com/ideas/)) and from within the application. The screenshot shows how to navigate to the Ideas portal from within Dynamics 365 for Operations.

[![ideas-menu.](../../fin-ops/get-started/media/ideas-menu.png)]

Click the **Ideas** link to go to the Dynamics 365 for Operations forum.

- The forums are pre-populated with existing ideas, so customers and partners can immediately vote or suggest new ideas.
- You can filter ideas by using status and time. You can also quickly view top, hot, and new ideas.
- You can either vote up or down on a specific idea (one vote per idea). To vote or suggest a new idea, you need to sign in using a Microsoft account.
- The **My Feedback** feature allows you to see a detailed view of your submitted ideas, the status of your ideas, and the total votes received.

[![ideas-options.](../../fin-ops/get-started/media/ideas-options.png)]

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
