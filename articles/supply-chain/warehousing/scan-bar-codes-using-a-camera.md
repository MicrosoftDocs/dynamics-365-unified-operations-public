---
title: Scan bar codes using a camera in the Warehouse Management mobile app
description: Learn how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device, including an outline on supported bar code formats. 
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 06/04/2025
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppField
---

# Scan bar codes using a camera in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article explains how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device.

## Setup

In the display settings of the Warehouse Management mobile app, you can select if the camera should be used for bar code scanning. If you enable **Use the camera as scanner**, you can use the camera on every input field that has the preferred input mode set to **Scanning**.

To control whether an input field should be scannable, on the **Warehouse app field names** page, set **Preferred input mode** to **Scanning**. When this option is selected, a camera can be used for scanning in the Warehouse Management mobile app. Learn more in [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

## Navigation

The camera page will be initiated on each page where the input field has its **Preferred input mode** set to *Scanning*, when you are on the camera page use the following options to navigate:

- Select the back button to go back to the **Task and details** page.
- Select the pencil on the **Task and details** page to go to a page where you can manually enter input.
- Select the camera on the **Task and details** page to go back to the camera page.

On the camera page, when you select the camera button, it appears dimmed while the camera tries to identify a bar code. If a bar code isn't identified within five seconds, the process time outs, and the camera button becomes available again. You can then try to scan a bar code again.

When you aim the camera at a bar code, a green check mark button indicates that you can scan it. Select the button to scan the code. If more than one bar code is scanned, the app asks you to identify the correct bar code.

## Supported bar code formats

The following table shows the bar code formats that are supported on each platform.

| Bar code format | Android | iOS | Windows | Common use cases |
|-----------------|---------|-----|---------|------------------|
| Aztec | Yes | Yes | Yes | Transportation tickets, identification documents |
| Codabar | Yes | Yes | Yes | Libraries, blood banks, shipping labels |
| Code 39 | Yes | Yes | Yes | Automotive, healthcare, government applications |
| Code 93 | Yes | Yes | Yes | Logistics, inventory management |
| Code 128 | Yes | Yes | Yes | Supply chain, shipping, product identification |
| DataBar (RSS-14) | No | No | Yes | Fresh foods, healthcare, small items |
| DataBar Limited | No | No | Yes | Small item identification, healthcare |
| DataBar Expanded | No | No | Yes | Coupons, loyalty cards, variable data |
| Data Matrix | Yes | Yes | Yes | Electronics, automotive parts, pharmaceuticals |
| DX Film Edge | No | No | Yes | Photography, film processing |
| EAN-8 | Yes | Yes | Yes | Small retail products, magazines |
| EAN-13 | Yes | Yes | Yes | Retail products, books, international trade |
| ITF (ITF-14) | Yes | Yes | Yes | Shipping cartons, distribution packaging |
| MaxiCode | No | No | Yes | UPS shipping, package tracking |
| PDF417 | Yes | Yes | Yes | Driver's licenses, identification cards, forms |
| QR Code | Yes | Yes | Yes | Marketing, inventory, contact information |
| Micro QR Code | No | No | Yes | Small components, electronics, jewelry |
| rMQR Code | No | No | Yes | Rectangular applications, space-constrained items |
| UPC-A | Yes | Yes | Yes | Retail products, grocery items |
| UPC-E | Yes | Yes | Yes | Small retail products, compressed UPC |

## Usage tips

Here are a few tips for effective bar code scanning in the Warehouse Management mobile app:

- **Optimal scanning conditions** – For the best scanning results, ensure adequate lighting, and hold the device steady.
- **Format selection** – The app automatically detects supported formats. Manual selection isn't required.
- **Compatibility check** – Before deployment, verify that your platform supports your specific bar code format.
- **Performance** – QR codes and standard retail formats (UPC and EAN) typically offer the fastest scanning performance.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]