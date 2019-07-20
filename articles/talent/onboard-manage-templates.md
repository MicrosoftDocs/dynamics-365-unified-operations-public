---
# required metadata

title: Manage templates in Microsoft Dynamics 365 for Talent - Onboard
description: This topic explains how to work with managed templates in Microsoft Dynamics 365 for Talent - Onboard.
author: andreabichsel
manager:
ms.date: 07/19/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-talent
ms.technology:

# optional metadata

ms.search.form: HcmCourseType, HcmCourseTypeGroup, HRMCourseTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Talent
# ms.tgt_pltfrm:
# ms.custom:
# ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: anbichse
ms.search.validFrom: 2019-07-10
ms.dyn365.ops.version: Talent
---

# Manage templates

[!include [banner](includes/banner.md)]

## Create a guide from a template

Managed features only work on activities (including introductions), not on contacts or resources.

Activities have a lock icon on them. Bar across the top shows where the activity came from. Can't edit it, except for assignee, due date, anything on right-hand sign.

If you change the activity in the original template (will show **Used in** tab), the change will appear in guides that use that template.

If you go to activities tab in the guide, you get a notice that your guide has changed: Syncing to the original template has updated all activities to match the version. Hit **OK**. You'll see a black dot next to the activities that were updated.

If you're editing a guide and you don't want template updates to update an activity, click the **Lock** button on the activity. You can now edit the activity, and it will no longer receive updates from the template.

> [!NOTE]
>
> Sections aren't managed, so if you add or edit a section in a template, the changes won't propagate to any guides that use that template.
>
> If you add any new activities to a template, the new activities are added to the top of the guides that are based on that template.
>
> If you delete an activity from a guide, and push changes from that guide's template, the activity will remain deleted in the guide.

## Import a template into another

Go to a template. Select **Activities** tab. Select **Import** tab on the right.

Select **Open in new window** button to preview the tasks.
Drag and drop a template to the place in your template where you want the activities to appear.
The imported activities will contain a **Lock** button, which indicates those activities are managed by the template you imported from. When you make changes to the template you imported, those activities will update in the template you imported them to. However, the changes will not be pushed automatically to any guides created from the template you imported to.


