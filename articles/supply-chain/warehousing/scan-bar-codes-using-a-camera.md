---
# required metadata

title: Scan bar codes using a camera in the Warehouse Management mobile app
description: This topic explains how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device. 
author: Mirzaab
ms.date: 01/03/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSMobileAppField
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2017-01-03
ms.dyn365.ops.version: AX 8.0.0

---

# Scan bar codes using a camera in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This topic explains how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device.

## Setup

In the display settings of the Warehouse Management mobile app, you can select if the camera should be used for bar code scanning. If you enable **Use the camera as scanner**, you can use the camera on every input field that has the preferred input mode set to **Scanning**.

To control whether an input field should be scannable, on the **Warehouse app field names** page, set **Preferred input mode** to **Scanning**. When this option is selected, a camera can be used for scanning in the Warehouse Management mobile app. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

## Supported bar code formats

The most common bar code formats are supported, including Code 128, Code 39, Code 93, EAN-8, EAN-13, UPC-E, UPC-A, and QR codes.

## Navigation

The camera page will be initiated on each page where the input field has its **Preferred input mode** set to *Scanning*, when you are on the camera page use the following options to navigate:

- Select the back button to go back to the **Task and details** page.
- Select the pencil on the **Task and details** page to go to the page where you can type input manually.
- Select the camera on the **Task and details** page to go back to the camera page.

On the camera page, when you select the camera button, it will appear dimmed while trying to identify a bar code. If a bar code is not identified within 5 seconds, the process will time out and the camera button will become available again. You will then be able to try to scan a bar code again.

When you aim the camera at a bar code, keep the bar code aligned within the brackets for best result. When a bar code is scanned successfully, the result will be processed, and you will be taken to the next step. If the next step contains another input field with the preferred input mode set to Scanning, the camera page will start again. If the next step is not a scanning field, then the camera page will not be initiated.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]