---
title: Known issues in the preview release
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

# Known issues in the preview release

The Asset Management mobile app is currently in public preview and therefore has a couple of known limitations that we expect to correct in the final release.

### Stuck on Loading Screen or at the end of Onboarding Screen

On iOS devices, the first time you open job details from the jobs list page, some of the fields will show too much vertical white space. This issue only occurs the first time you open the details page. To mitigate the issue, return to the jobs list and then reopen the details. This limitation only applies to iOS devices.
After installing or updating the preview application package or solution, users of the mobile application can get stuck in the Loading Screen or at the end of the Onboarding Screen.

To mitigate, "Edit" the Canvas application in Power Apps maker portal and re-publish immediately without making any changes. See [this](https://learn.microsoft.com/power-apps/maker/canvas-apps/save-publish-app) on how to re-publish a Canvas application.

This issue is being actively worked on.

### Too much vertical whitespace

Sometimes after opening the job- or work order details from the list page, some of the fields will show too much vertical white space. This issue only occurs the first time you open the details page. To mitigate the issue, return to the jobs list and then reopen the details.

[<img src="media/asset-management-known-issue-vertical-space.png" alt="Showing a visual issue where there is too much vertical whitespace between content" width="250" />](media/asset-management-known-issue-vertical-space.png#lightbox)

### Limited file-type support for attachments

The current release provides only limited support for file attachments on the job details page. We plan to add support for more file types in the final release.

Supported attachment types:

- URL (link)
- PNG/JPEG/JPG/BMP/GIF (image)
- PDF (document)
- 
Unsupported attachment types:

- Note
- All other file types

