---
title: Known issues affecting the preview release of the Asset Management mobile app
description: This article describes known issues that affect the preview release of the Asset Management mobile app
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

# Known issues affecting the preview release of the Asset Management mobile app

The Asset Management mobile app is currently in public preview and therefore has a few known limitations that we expect to correct in the final release.

## Stuck on the loading or onboarding screen

After you install or update the preview application package or solution, you might get stuck at the loading screen or at the end of the onboarding screen. <!-- KFM: Where are we working here? Where do we get stuck?  E.g., are we installing on a mobile device, installing in Dataverse, or somewhere else?  -->

To work around this issue, open the canvas application for editing in Power Apps maker portal <!-- KFM: Is this the right name? It doesn't appear in the linked topic. Maybe we mean *Power Apps Studio*? --> and then republish it immediately without making any changes. For more information about how to republish a canvas application, see [Save and publish canvas apps](/power-apps/maker/canvas-apps/save-publish-app).

## Too much vertical whitespace on details pages

Occasionally, the first time you open job or work-order details from a list page, some of the fields will show too much vertical white space. To mitigate this issue, return to the list page and then reopen the details.

The following screenshot shows an example of this issue.

[<img src="media/asset-management-known-issue-vertical-space.png" alt="Too much vertical whitespace on the work-order details page" title="Too much vertical whitespace on the work-order details page" width="200" />](media/asset-management-known-issue-vertical-space.png#lightbox)

## Limited file-type support for attachments

The current release provides only limited support for viewing file attachments on the job details page. We plan to add support for more file types in the final release.

Supported attachment types:

- URL (link)
- PNG/JPEG/JPG/BMP/GIF (image)
- PDF (document)

Unsupported attachment types:

- Note
- All other file types
