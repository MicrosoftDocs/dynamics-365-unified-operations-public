---
title: Add a QR code or bar code to transactional and receipt emails
description: This article explains how to insert QR codes and bar codes that represent order IDs into transactional and receipt emails in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: stuharg
ms.search.validFrom: 2021-02-16
ms.dyn365.ops.version: Release 10.0.18
ms.custom: 
ms.assetid: 
---

# Add a QR code or bar code to transactional and receipt emails

[!include [banner](includes/banner.md)]

This article explains how to insert QR codes and bar codes that represent order IDs into transactional and receipt emails in Microsoft Dynamics 365 Commerce.

You can easily include QR codes and bar codes in transactional emails to help speed up the order lookup process in a retail environment. To insert QR codes and bar codes into emails, you use an HTML **\<img\>** tag that requests a QR code or bar code image from a generation and rendering service. Microsoft doesn't provide this service. However, there are many free or inexpensive services that can serve QR codes or bar codes that are dynamically generated based on a value that is passed in a query string.

## Add a QR code or bar code to a transactional email

To insert a QR code or bar code into a transactional email that is sent as part of an e-commerce purchase, follow these steps.

1. Open the source HTML for the transactional email template, and add an HTML **\<img\>** tag that points to your QR code or bar code service. Here is an example.

    ```HTML
    <img src="https://YOUR_QR_CODE_BAR_CODE_SERVICE?data=%salesid%&param1=value1&param2=value2" alt="%salesid%" />
    ```

    Here is an explanation of the preceding example:

    - **YOUR\_QR\_CODE\_BAR\_CODE\_SERVICE** represents the domain of your QR code or bar code service.
    - **data** represents the parameter that the QR code or bar code service uses to receive the content that should be rendered as a QR code or bar code.

        The value **%salesid%** must be assigned to this parameter. In this example, notice that the value is also used as alt text for the image.

    - **param1** and **param2** represent additional optional parameters.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates**, and upload the updated HTML to the appropriate transactional email template.

> [!NOTE]
> Parameters might differ among QR code and bar code service providers. Therefore, be sure to contact your service provider to confirm the parameters that you must assign values to.

## Add a QR code or bar code to a receipt email 

To insert a QR code or bar code into a receipt email that can be sent after a purchase is made at the point of sale (POS), follow these steps.

1. Open the source HTML for the receipt email template, and add an HTML **\<img\>** tag that points to your QR code or bar code service. Here is an example below.

    ```HTML
    <img src="https://YOUR_QR_CODE_BAR_CODE_SERVICE?data=%receiptid%&param1=value1&param2=value2" alt="%receiptid%" />
    ```

    Here is an explanation of the preceding example:

    - **YOUR\_QR\_CODE\_BAR\_CODE\_SERVICE** represents the domain of your QR code or bar code service.
    - **data** represents the parameter that the QR code or bar code service uses to receive the content that should be rendered as a QR code or bar code.

        The value **%receiptid%** must be assigned to this parameter. In this example, notice that the value is also used as alt text for the image.

    - **param1** and **param2** represent additional optional parameters.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Organization email templates**, and upload the updated HTML to the email template that has the email ID **emailrecpt**.

> [!NOTE]
> Parameters might differ among QR code and bar code service providers. Therefore, be sure to contact your service provider to confirm the parameters that you must assign values to.

## Additional resources

[Send email receipts from Store Commerce](email-receipts.md)

[Create email templates for transactional events](email-templates-transactions.md)
