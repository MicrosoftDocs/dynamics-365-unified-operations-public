---
# required metadata

title: Add a QR code or barcode to emails
description: This topic explains how to insert a QR code or barcode representing an order ID into a transactional email or emailed receipt.
author: bicyclingfool
manager: annbe
ms.date: 2/16/2021
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

 

[!include [banner](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/commerce/includes/banner.md)]



This topic explains how to insert a QR code or barcode representing an order ID into a transactional email or emailed receipt.


## Overview

 QR codes and barcodes can easily be included in transactional emails to facilitate faster order lookup in a retail environment. 

 

## Prerequisite

QR codes and barcodes are inserted into emails through an HTML img tag that requests a QR code or barcode image from a generation and rendering service. Microsoft does not provide this service, but there are many free and inexpensive QR code and barcode generation services that can serve dynamically generated QR codes or barcodes based on a value passed on the query string. 

 

## Add a QR code or barcode to a transactional email

To insert a QR code or barcode into a transactional email that is sent as part of an e-commerce purchase:

1. Open the source HTML for that email template and add an HTML img reference to your QR code or barcode service. 
2. In the parameter your service uses to receive the content to render as a QR code or barcode, insert **%salesid%** as the value.
3. Upload the updated HTML to the appropriate email template in **Organization email templates** (Retail & Commerce >  Headquarters setup > Parameters > Organization email templates)

The following HTML sample illustrates how to create an HTML img tag that requests a QR code or barcode from a service. 

<img src=”https://YOUR_QRCODE_SERVICE?data=%salesid%&param1=value1&param2=value2" alt=”%salesid%” /> 

 

## Add a QR code or barcode to an emailed receipt

To insert a QR code or barcode into an emailed receipt that can be emailed from a purchase at a point of sale:

1. Open the source HTML for that email template and add an HTML img reference to your QR code or barcode service. 
2. In the parameter your service  uses to receive the content to render as a QR code or barcode, insert **%receiptid%** as the value.
3. Upload the updated HTML to the email template whose email ID is **emailrecpt** in **Organization email templates** (Retail & Commerce > Headquarters setup > Parameters >  Organization email templates)

The following HTML sample illustrates how to create an HTML img tag that requests a QR code or barcode from a service. 

<img src=”https://YOUR_BARCODE_SERVICE?data=%receiptid%&param1=value1&param2=value2" alt=”%receiptid%” /> 

 

## Additional resources

[Send email receipts from Modern POS (MPOS)](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions)
