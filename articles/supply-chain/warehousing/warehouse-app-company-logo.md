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

Follow these steps to customize the logo shown in the Warehouse Management mobile app:

1. Go to **Organization Administration \> Organizations \> Legal entities**.
1. From the list pane, select the legal entity you want to upload a logo for.
1. Do one of the following steps:
    - Expand the **Dashboard image** FastTab and set **Dashboard company image type** to *Logo*. Then select **Change** from the FastTab toolbar to open a dialog where you can select and upload the image. If a logo image is uploaded here, then this image is always used by the Warehouse Management mobile app, even if an image is also defined on the **Report company logo image** FastTab, and even if you save the page with **Dashboard company image type** set to a value other than *Logo*. The settings on the **Dashboard image** FastTab also set the image shown at the top of the home page of the Supply Chain Management web client. If you prefer to use one of the other image types for the web client, then set **Dashboard company image type field** to a value other than *Logo* after you upload the logo.
    - Expand the **Report company logo image** FastTab and select **Change** from the FastTab toolbar to open a dialog where you can select and upload the image. The Warehouse Management mobile app only uses the logo selected here if no image is defined on the **Dashboard image** FastTab for **Dashboard company image type** *Logo*. The image selected on the **Report company logo image** FastTab is also used for reports that include a logo.
1. On the Action Pane, select **Save**.
1. Repeat this procedure from step 2 for each legal entity you want to upload a logo for.
