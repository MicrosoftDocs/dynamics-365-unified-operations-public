---
title: Customize the company logo shown in the Warehouse Management mobile app
description: Learn how to customize the company logo shown in the Warehouse Management mobile app, including a step-by-step process for customizing logos.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 10/12/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Customize the company logo shown in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

You can display your company logo in the Warehouse Management mobile app by uploading it through the legal entity settings in Supply Chain Management. The app retrieves the logo based on the legal entity the worker is signed in to.

## How logo priority works

The app checks for a logo in two places. The **Dashboard image** FastTab takes priority over the **Report company logo image** FastTab:

| Source | When the app uses it |
|---|---|
| **Dashboard image** FastTab (with **Dashboard company image type** set to *Logo*) | Always used when a logo image is uploaded here, regardless of whether a logo is also defined on the Report company logo image FastTab. |
| **Report company logo image** FastTab | Used only if no logo image is defined on the Dashboard image FastTab. This image is also used for printed reports that include a logo. |

> [!NOTE]
> The **Dashboard image** FastTab also controls the image shown on the Supply Chain Management web client home page. If you want a different image for the web client, upload your logo for the mobile app first, then change the **Dashboard company image type** to a different value. The mobile app continues to use the logo you uploaded.

## Upload a company logo

1. Go to **Organization Administration \> Organizations \> Legal entities**.
1. Select the legal entity you want to upload a logo for.
1. Do one of the following steps:
    - To use the **Dashboard image** method (recommended): Expand the **Dashboard image** FastTab, set **Dashboard company image type** to *Logo*, and select **Change** to upload the image.
    - To use the **Report company logo image** method: Expand the **Report company logo image** FastTab and select **Change** to upload the image.
1. On the Action Pane, select **Save**.
1. Repeat from step 2 for each legal entity that needs a logo.
