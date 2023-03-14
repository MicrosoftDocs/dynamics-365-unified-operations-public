---
title: Asset Management mobile app overview
description: This article introduces the Asset Management mobile app.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 03/17/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Asset Management mobile app overview

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

## Asset Management mobile app features

The Asset Management mobile app provides the following capabilities for workers and organizations that use Asset Management for Microsoft Dynamics 365 Supply Chain Management:

- **Manage work orders.** Maintenance workers use work orders as a daily to-do list that provides the information that they need to complete their planned maintenance tasks. In the app, workers can search for work orders that have been assigned to them. They then use the app to record their progress, so that the system can track labor, materials, and services for the work that's done. Workers can create new work orders, process existing orders, and perform tasks such as updating checklist items, updating asset counters, registering time and materials, and viewing and adding notes.
- **Create maintenance requests.** Administrators can use the role-based security setup in Supply Chain Management to grant workers permission to create new maintenance requests. Workers who receive this permission will then be able to use the mobile app to proactively request maintenance of assets.

To use the app, you must have a fully implemented setup of Asset Management in your Supply Chain Management environment.

The following illustration shows an example of a list of jobs for a work order in the Asset Management mobile app.

[<img src="media/mobile-app-in-phone.png" alt="Job list for a work order in the Asset Management mobile app." title="Job list for a work order in the Asset Management mobile app" width="250" />](media/mobile-app-in-phone.png#lightbox)

> [!NOTE]
> The Asset Management mobile app replaces the now-deprecated [Asset management mobile workspace](../asset-management-mobile-workspace.md).

## Known issues in the preview release

The Asset Management mobile app is currently in public preview and therefore has a couple of known limitations that we expect to correct in the final release.

### Too much vertical whitespace on the job details page on iOS devices

On iOS devices, the first time you open job details from the jobs list page, some of the fields will show too much vertical white space. This issue only occurs the first time you open the details page. To mitigate the issue, return to the jobs list and then reopen the details. This limitation only applies to iOS devices.

### Limited file-type support for attachments

The current release provides only limited support for file attachments on the job details page. We plan to add support for more file types in the final release.

Supported attachment types:

- URL (link)
- PNG (image)

Unsupported attachment types:

- Simple note
- All other file types

## Next steps

- [Onboard the Asset Management mobile app](onboard-app.md)
- [Manage work orders using the Asset Management mobile app](work-orders.md)
- [File maintenance requests using the Asset Management mobile app](maintenance-requests.md)
