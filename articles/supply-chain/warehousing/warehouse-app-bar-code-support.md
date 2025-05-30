---
title: Warehouse Management Application supported barcodes
description: Here are the current barcode supported
author: pefreita
ms.author: pefreita
ms.topic: migration-to
ms.date: 05/30/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  MigrateWMA, WMAV4, NewWMA, UpdateWMA
---

# Warehouse Management Application supported barcodes

The Warehouse Mobile Application features built-in camera-based barcode scanning capabilities to streamline inventory management and data capture processes. Our barcode scanner supports a wide range of industry-standard formats across multiple platforms, ensuring compatibility with your existing warehouse operations.

**Important Note:** The supported barcode formats listed below are current as of this version. Support may be expanded or modified in future releases as we continue to enhance the application's capabilities.

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

## Future Updates

We continuously evaluate and expand our barcode format support based on user feedback and industry requirements. Check the application release notes for the latest updates to supported formats.

For technical support or feature requests regarding barcode scanning capabilities, please contact our development team through the standard support channels.
