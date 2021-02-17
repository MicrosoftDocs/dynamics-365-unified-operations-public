---
# required metadata

title: Add a QR code or barcode to transactional emails
description: This topic explains how to insert a QR code or barcode representing an order ID into a transactional email or emailed receipt in Dynamics 365 Commerce.
author: bicyclingfool
manager: annbe
ms.date: 03/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Commerce, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2021-02-16
ms.dyn365.ops.version: Release 10.0.18

---

# Add a QR code or barcode to emails

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic explains how to insert a Quick Response (QR) code or barcode representing an order ID into a transactional email or emailed receipt in Dynamics 365 Commerce.

QR codes and barcodes can easily be included in transactional emails to facilitate faster order lookup in a retail environment. QR codes and barcodes are inserted into emails using an HTML **\<img\>** tag that requests a QR code or barcode image from a generation and rendering service. Microsoft does not provide this service, but there are many free and inexpensive QR code and barcode generation services that can serve dynamically generated QR codes or barcodes based on a value passed in a query string. 

## Add a QR code or barcode to a transactional email

To insert a QR code or barcode into a transactional email that is sent as part of an e-commerce purchase, follow these steps.

1. Open the source HTML for the transactional email template and add an HTML **\<img\>** tag that refers to your QR code or barcode service, following the code example below. 
2. In the parameter your QR code or barcode generation service uses to receive the content to render as a QR code or barcode, insert **%salesid%** as the value.
3. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates** and upload the updated HTML to the appropriate transactional email template.

The following example shows an HTML **\<img\>** tag in a transactional email that requests a QR code or barcode from a service. 

```HTML
<img src="https://YOUR_QRCODE_SERVICE?data=%salesid%&param1=value1&param2=value2" alt="%salesid%" />
```

## Add a QR code or barcode to an email receipt

To insert a QR code or barcode into an emailed receipt that can be emailed from a purchase at a point of sale, follow these steps.

1. Open the source HTML for the email receipt template and add an HTML **\<img\>** tag that refers to your QR code or barcode service, following the code example below. 
2. In the parameter your service uses to receive the content to render as a QR code or barcode, insert **%receiptid%** as the value.
3. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates** and upload the updated HTML to the email template with email ID **emailrecpt**.

The following example shows an HTML **\<img\>** tag in an email receipt that requests a QR code or barcode from a service. 

```HTML
<img src="https://YOUR_BARCODE_SERVICE?data=%receiptid%&param1=value1&param2=value2" alt="%receiptid%" />
```

## Additional resources

[Send email receipts from Modern POS (MPOS)](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions.md)
