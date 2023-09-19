---
title: Asset Management mobile app FAQs and known issues
description: This article provides answers to several frequently asked questions (FAQs) about the Asset Management mobile app. It also describes a few known issues that affect the app and how to work around them.
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

# Asset Management mobile app FAQs and known issues

This article provides answers to several frequently asked questions (FAQs) about the Asset Management mobile app. It also describes a few known issues that affect the app and how to work around them.

## What platforms and mobile devices are supported?

The Asset Management mobile app runs within the Power Apps mobile app. All platforms supported by the Power Apps mobile app can also run the Asset Management mobile app. For details, see [System requirements, limits, and configuration values for Power Apps](/power-apps/limits-and-config).

## Why don't I see anything when I sign in to the app?

If you don't see any features in the app, you probably lack the permissions required to access them. Access to each feature is controlled by security roles assigned to your user account in Supply Chain Management. For more information, see the [Configure users and workers in Supply Chain Management](onboard-app.md#roles-workers)

## What versions of Supply Chain Management support the app?

The Asset Management mobile app requires Supply Chain Management version 10.0.36 or newer.

## Can I customize and extend the app?

No, it isn't currently possible to customize or extend the app.

## Does the app support offline mode?

No, the Asset Management mobile app doesn't currently support offline mode.

## Is there multi-language support?

Yes, the Asset Management mobile app is available in all the same languages as Supply Chain Management, except for right-to-left (RTL) languages. We are awaiting RTL support from the canvas app platform and plan to add RTL support in a future release.

## Where can I go to discuss the app with the community and submit suggestions to Microsoft?

The [Asset Management Viva Engage (Yammer) group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=17556554&view=all) is a great place to go if you want to exchange tips, ask questions, or submit suggestions for improvement. Yammer group participants include Microsoft partners, customers, experts, and employees.

## How can I diagnose "Error when trying to retrieve data from the network" issues?

If the issue reproduces from a computer, restart the app and [capture an HAR file to share with Microsoft support](/microsoft-edge/devtools-guide-chromium/network/reference#save-all-network-requests-to-a-har-file). Before sharing the HAR file with anyone, make sure to redact secrets from it using a tool such as the [Google HAR analyzer](https://toolbox.googleapps.com/apps/har_analyzer/).

## Are there any known issues affecting the release of the Asset Management mobile app?

Yes. The Asset Management mobile app has a few known issues that we expect to correct in an upcoming release. The following subsections describe the known issues.

### Limited file-type support for attachments

The current release provides only limited support for viewing file attachments on the job details page. We plan to add support for more file types in the final release.

Supported attachment types:

- URL (link)
- PNG/JPEG/JPG/BMP/GIF (image)
- PDF (document)

Unsupported attachment types:

- Note
- All other file types
