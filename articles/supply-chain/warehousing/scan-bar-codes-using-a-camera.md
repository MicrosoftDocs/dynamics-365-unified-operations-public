---
title: Scan bar codes using a camera in the Warehouse Management mobile app
description: Learn how to set up the Warehouse Management mobile app to scan bar codes using a camera on a mobile device, including an outline on supported bar code formats. 
author: pefreita
ms.author: pefreita
ms.topic: article
ms.date: 02/06/2025
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
- Select the pencil on the **Task and details** page to go to the page where you can type input manually.
- Select the camera on the **Task and details** page to go back to the camera page.

On the camera page, when you select the camera button, it will appear dimmed while trying to identify a bar code. If a bar code is not identified within 5 seconds, the process will time out and the camera button will become available again. You will then be able to try to scan a bar code again.

When you aim the camera at a bar code, there will be a ✅ signing that you can scan that value. If you click on the button, the value is used. In the situation, were more than one barcode is scanned, a popup is displayed allowing you to specify the right barcode. That is an improvement that we did from version 4+.

## Supported Barcode Formats

The following table shows which barcode formats are supported on each platform:

| Barcode Format | Android | iOS | Windows | Common Use Cases |
|----------------|---------|-----|---------|------------------|
| **Aztec** | ✅ | ✅ | ✅ | Transportation tickets, identification documents |
| **Codabar** | ✅ | ✅ | ✅ | Libraries, blood banks, shipping labels |
| **Code 39** | ✅ | ✅ | ✅ | Automotive, healthcare, government applications |
| **Code 93** | ✅ | ✅ | ✅ | Logistics, inventory management |
| **Code 128** | ✅ | ✅ | ✅ | Supply chain, shipping, product identification |
| **DataBar (RSS-14)** | ❌ | ❌ | ✅ | Fresh foods, healthcare, small items |
| **DataBar Limited** | ❌ | ❌ | ✅ | Small item identification, healthcare |
| **DataBar Expanded** | ❌ | ❌ | ✅ | Coupons, loyalty cards, variable data |
| **Data Matrix** | ✅ | ✅ | ✅ | Electronics, automotive parts, pharmaceuticals |
| **DX Film Edge** | ❌ | ❌ | ✅ | Photography, film processing |
| **EAN-8** | ✅ | ✅ | ✅ | Small retail products, magazines |
| **EAN-13** | ✅ | ✅ | ✅ | Retail products, books, international trade |
| **ITF (ITF-14)** | ✅ | ✅ | ✅ | Shipping cartons, distribution packaging |
| **MaxiCode** | ❌ | ❌ | ✅ | UPS shipping, package tracking |
| **PDF417** | ✅ | ✅ | ✅ | Driver's licenses, identification cards, forms |
| **QR Code** | ✅ | ✅ | ✅ | Marketing, inventory, contact information |
| **Micro QR Code** | ❌ | ❌ | ✅ | Small components, electronics, jewelry |
| **rMQR Code** | ❌ | ❌ | ✅ | Rectangular applications, space-constrained items |
| **UPC-A** | ✅ | ✅ | ✅ | Retail products, grocery items |
| **UPC-E** | ✅ | ✅ | ✅ | Small retail products, compressed UPC |

## Platform-Specific Information

### Universal Support (All Platforms)

The following formats are supported across Android, iOS, and Windows platforms:

- Aztec, Codabar, Code 39, Code 93, Code 128
- Data Matrix, EAN-8, EAN-13, ITF (ITF-14)
- PDF417, QR Code, UPC-A, UPC-E

### Windows-Only Support

These advanced formats are currently exclusive to the Windows version:

- DataBar family (RSS-14, Limited, Expanded)
- DX Film Edge, MaxiCode
- Micro QR Code, rMQR Code

## Usage Tips

1. **Optimal Scanning Conditions:** Ensure adequate lighting and hold the device steady for best scanning results
2. **Format Selection:** The app automatically detects supported formats - no manual selection required
3. **Compatibility Check:** Verify your specific barcode format is supported on your platform before deployment
4. **Performance:** QR codes and standard retail formats (UPC, EAN) typically offer the fastest scanning performance

[!INCLUDE[footer-include](../../includes/footer-banner.md)]