---
title: Scan bar codes using a camera in the Warehouse Management mobile app
description: Learn how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device, including an outline on supported bar code formats. 
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 08/07/2026
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppField
---

# Scan bar codes using a camera in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article explains how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device.

> [!NOTE]
> This article applies to Warehouse Management mobile app version 4.1.5 and later. Earlier versions provide a more limited camera scanning experience, and they support fewer bar code formats.

## Setup

In the display settings of the Warehouse Management mobile app, you can choose whether to use the camera for bar code scanning. If you turn on **Use the camera as scanner**, you can use the camera on every input field that has the preferred input mode set to **Scanning**.

To control whether an input field is scannable, on the **Warehouse app field names** page, set **Preferred input mode** to **Scanning**. When you select this option, a camera can be used for scanning in the Warehouse Management mobile app. Learn more in [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

## Navigation

Each page where the input field has its **Preferred input mode** set to *Scanning* includes a link to the camera page. When you're on the camera page, use the following options to navigate:

- Select the back button to go back to the **Task and details** page.
- Select the pencil on the **Task and details** page to go to a page where you can manually enter input.
- Select the camera on the **Task and details** page to go back to the camera page.

The camera scans continuously while the camera page is open. Every bar code that the camera recognizes is outlined in the preview, and the decoded value is shown under the outline. You don't have to start or restart a scan, and there's no scanning time-out.

The following controls are available on the camera page:

- **Back** – Returns to the **Task and details** page.
- **Flashlight** – Turns the device flashlight on or off. Use it in dark aisles, in freezers, or when a label is in shadow. The button isn't available on devices that don't have a flashlight.
- **Accept** – Submits the bar code. The button shows a green check mark as soon as a bar code is recognized. If more than one bar code is recognized, the app asks you to identify the correct bar code.

## Customize the bar code scan marker

When you scan with the device camera, the app draws a highlight around each bar code that it recognizes, labeled with the decoded value. You can choose both the color and the thickness of that highlight.

A thin, pale marker can be hard to pick out against a busy label, a glossy surface, or in bright sunlight. Warehouse lighting and label stock vary from site to site, so a marker that works well in one facility might be hard to see in another.

To change the marker appearance:

1. Go to **Settings** > **Camera**.
1. Select **Scan marker color**, and choose one of the twelve available colors. Available options include: *Peach* (default), *White*, *Black*, *Red*, *Orange*, *Yellow*, *Lime*, *Green*, *Teal*, *Blue*, *Purple*, and *Magenta*.

    Pick a color that contrasts with the labels that you scan most often. Light colors, such as *White*, *Yellow*, and *Peach*, stand out against dark packaging and printed bar codes. *Black* and darker colors work better against pale or reflective label stock. If markers are hard to spot at a glance, increasing the thickness usually helps more than changing the color.

1. Select **Scan marker thickness**, and choose one of the five available widths. Available options include: *Thin*, *Normal* (default), *Medium*, *Thick*, and *Extra thick*.

The app shows a live preview of your settings, so you can see how the combination looks before you commit to it. Your new settings apply the next time you open the camera scanner.

Keep the following points in mind when you set the scan marker color or thickness:

- **The server saves the setting for the specific worker and device combination** – The setting follows the current worker on the current device, but it isn't shared across devices. If the worker signs in on a different device, that device uses its own setting. Each worker and device combination is configured independently.
- **The setting persists across sessions** – After you set it, your choice is remembered when you close the scanner, sign out, or restart the app.
- **The setting only affects the display** – It doesn't change how bar codes are detected or decoded, and it has no effect on scanning accuracy or on hardware (laser) scanning.

## Supported bar code formats

The following table shows the bar code formats that each platform supports.

| Bar code format | Android | iOS | Windows | Common use cases |
|-----------------|---------|-----|---------|------------------|
| Aztec | Yes | Yes | Yes | Transportation tickets, identification documents |
| Codabar | Yes | Yes | Yes | Libraries, blood banks, shipping labels |
| Code 39 | Yes | Yes | Yes | Automotive, healthcare, government applications |
| Code 93 | Yes | Yes | Yes | Logistics, inventory management |
| Code 128 | Yes | Yes | Yes | Supply chain, shipping, product identification |
| DataBar (RSS-14) | Yes | Yes | Yes | Fresh foods, healthcare, small items |
| DataBar Limited | Yes | Yes | Yes | Small item identification, healthcare |
| DataBar Expanded | Yes | Yes | Yes | Coupons, loyalty cards, variable data |
| Data Matrix | Yes | Yes | Yes | Electronics, automotive parts, pharmaceuticals |
| DX Film Edge | No | No | Yes | Photography, film processing |
| EAN-8 | Yes | Yes | Yes | Small retail products, magazines |
| EAN-13 | Yes | Yes | Yes | Retail products, books, international trade |
| ITF (ITF-14) | Yes | Yes | Yes | Shipping cartons, distribution packaging |
| MaxiCode | No | No | Yes | UPS shipping, package tracking |
| MSI Plessey | No | Yes | No | Shelf and inventory labels in retail |
| PDF417 | Yes | Yes | Yes | Driver's licenses, identification cards, forms |
| Micro PDF417 | Yes | Yes | No | Small parts marking, healthcare specimens |
| QR Code | Yes | Yes | Yes | Marketing, inventory, contact information |
| Micro QR Code | Yes | Yes | Yes | Small components, electronics, jewelry |
| rMQR Code | No | No | Yes | Rectangular applications, space-constrained items |
| UPC-A | Yes | Yes | Yes | Retail products, grocery items |
| UPC-E | Yes | Yes | Yes | Small retail products, compressed UPC |

The following platform notes apply:

- On Android, the Google ML Kit bar code scanner decodes bar codes. An extra scanner decodes the DataBar formats, Micro QR Code, and Micro PDF417. The extra scanner only runs  when ML Kit doesn't recognize a bar code, so it doesn't slow down everyday scanning. On iOS, the Apple Vision framework decodes bar codes. On Windows, scanning runs in the browser. Because each platform uses a different decoder, the supported formats differ, as shown in the preceding table.
- MSI Plessey is only supported on iOS 17 or later. No decoder is available for it on Android.
- On iOS, Codabar, the DataBar formats, Micro QR Code, and Micro PDF417 require iOS 15 or later.
- On iOS, UPC-A is reported as its EAN-13 equivalent, which is the same 12-digit number with a leading zero. Most hardware scanners behave the same way. If your process compares scanned values with a UPC-A item identifier, allow for the leading zero.
- The app scans all supported formats at the same time. You don't select a format in the app.

## Usage tips

Here are a few tips for effective bar code scanning in the Warehouse Management mobile app:

- **Optimal scanning conditions** – For the best scanning results, ensure adequate lighting, and hold the device steady. In poor lighting, turn on the flashlight from the camera page.
- **Distance** – Hold the camera close enough that the bar code fills most of the width of the preview. Dense, one-dimensional formats, such as Code 39 and Code 128, need more detail than QR codes do. If a bar code isn't recognized, the app gradually zooms in to help, but moving closer is faster.
- **Alignment** – Keep one-dimensional bar codes roughly parallel to the focal plane of the camera. Two-dimensional formats, such as QR Code and Data Matrix, can be scanned at any angle.
- **Format selection** – The app automatically detects supported formats. Manual selection isn't required.
- **Compatibility check** – Before deployment, verify that your platform supports your specific bar code format.
- **Performance** – QR codes and standard retail formats (UPC and EAN) typically offer the fastest scanning performance.
- **Damaged or glossy labels** – Change the angle slightly to avoid glare, and clean the camera lens. Torn or wrinkled labels might have to be entered manually. Select the pencil on the **Task and details** page to enter the value.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
