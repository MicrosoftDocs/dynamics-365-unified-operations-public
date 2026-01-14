---
title: Add a QR code or barcode to transactional and receipt emails
description: Learn how to insert QR codes and barcodes that represent order IDs into transactional and receipt emails in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/14/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2021-02-16
ms.custom: 
  - bap-template
---

# Add a QR code or barcode to transactional and receipt emails

[!include [banner](includes/banner.md)]

This article explains how to insert QR codes and barcodes that represent order IDs into transactional and receipt emails in Microsoft Dynamics 365 Commerce.

You can easily include QR codes and barcodes in transactional emails to help speed up the order lookup process in a retail environment. To insert QR codes and barcodes into emails, use an HTML **\<img\>** tag that requests a QR code or barcode image from a generation and rendering service. Microsoft doesn't provide this service. However, many free or inexpensive services can serve QR codes or barcodes that are dynamically generated based on a value that you pass in a query string.

## Add a QR code or barcode to a transactional email

To insert a QR code or barcode into a transactional email that you send as part of an e-commerce purchase, follow these steps:

1. Open the source HTML for the transactional email template, and add an HTML **\<img\>** tag that points to your QR code or barcode service. Here's an example.

    ```HTML
    <img src="https://YOUR_QR_CODE_BAR_CODE_SERVICE?data=%salesid%&param1=value1&param2=value2" alt="%salesid%" />
    ```

    Here's an explanation of the preceding example:

    - **YOUR\_QR\_CODE\_BAR\_CODE\_SERVICE** represents the domain of your QR code or barcode service.
    - **data** represents the parameter that the QR code or barcode service uses to receive the content that it should render as a QR code or bar code.

        Assign the value **%salesid%** to this parameter. In this example, the value is also used as alt text for the image.

    - **param1** and **param2** represent additional optional parameters.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates**, and upload the updated HTML to the appropriate transactional email template.

> [!NOTE]
> Parameters might differ among QR code and barcode service providers. Therefore, be sure to contact your service provider to confirm the parameters that you must assign values to.

## Add a QR code or bar code to a receipt email 

To insert a QR code or barcode into a receipt email that can be sent after a purchase is made at the point of sale (POS), follow these steps:

1. Open the source HTML for the receipt email template. Add an HTML **\<img\>** tag that points to your QR code or bar code service. Here's an example:

    ```HTML
    <img src="https://YOUR_QR_CODE_BAR_CODE_SERVICE?data=%receiptid%&param1=value1&param2=value2" alt="%receiptid%" />
    ```

    Here's an explanation of the preceding example:

    - **YOUR\_QR\_CODE\_BAR\_CODE\_SERVICE** represents the domain of your QR code or barcode service.
    - **data** represents the parameter that the QR code or barcode service uses to receive the content that it should render as a QR code or bar code.

        The value **%receiptid%** must be assigned to this parameter. In this example, notice that the value is also used as alt text for the image.

    - **param1** and **param2** represent additional optional parameters.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates**, and upload the updated HTML to the email template that has the email ID **emailrecpt**.

> [!NOTE]
> Parameters might differ among QR code and barcode service providers. Therefore, be sure to contact your service provider to confirm the parameters that you must assign values to.

## Additional resources

[Send email receipts from Store Commerce](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions.md)
