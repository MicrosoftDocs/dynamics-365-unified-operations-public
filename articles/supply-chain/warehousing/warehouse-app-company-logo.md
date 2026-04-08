---
title: Customize the company logo shown in the Warehouse Management mobile app
description: Learn how to customize the company logo shown in the Warehouse Management mobile app, including a step-by-step process for customizing logos.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 04/08/2026
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Customize the company logo shown in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

You can display your company logo in the Warehouse Management mobile app by uploading it through the legal entity settings in Supply Chain Management. The app retrieves the logo based on the legal entity the worker signs in to.

## How logo priority works

The app checks for a logo in two places on the **Legal entities** page. The setting on the **Dashboard image** FastTab takes priority over the **Report company logo image** FastTab, as summarized in the following table:

| Source | When the app uses it |
|---|---|
| **Dashboard image** FastTab (with **Dashboard company image type** set to *Logo*) | This logo is always used when available, regardless of whether a logo is also defined on the **Report company logo image** FastTab. |
| **Report company logo image** FastTab | Used only if no logo image is defined on the **Dashboard image** FastTab. This image is also used for printed reports that include a logo. |

> [!NOTE]
> The **Dashboard image** FastTab setting also controls the image shown on the Supply Chain Management web client home page. If you want a different image for the web client, upload your logo for the mobile app first. Then change the **Dashboard company image type** to a different value and upload the web client logo image. The mobile app continues to use the first logo you uploaded.

## Upload company logos for the app

To upload a company logo for each legal entity, follow these steps:

1. Go to **Organization Administration \> Organizations \> Legal entities**.
1. Select the legal entity you want to upload a logo for.
1. Choose one of the following methods:
    - **Dashboard image method (recommended)** – Expand the **Dashboard image** FastTab, set **Dashboard company image type** to *Logo*, and select **Change** to upload the image.
    - **Report company logo image method** – Expand the **Report company logo image** FastTab and select **Change** to upload the image.
1. On the Action Pane, select **Save**.
1. Repeat from step 2 for each legal entity that needs a logo.
