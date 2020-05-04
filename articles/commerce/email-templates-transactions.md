---
# required metadata

title: Create email templates for transactional events 
description: This topic describes how to create, upload, and configure email templates for transactional events in Microsoft Dynamics 365 Commerce.
author: stuharg
manager: annbe
ms.date: 05/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Create email templates for transactional events

[!include [banner](includes/banner.md)]

This topic describes how to create, upload, and configure email templates for transactional events in Microsoft Dynamics 365 Commerce.

## Overview

Dynamics 365 Commerce provides an out-of-box solution for sending emails that alert customers about transactional events (for example, when an order is placed, an order is ready for pickup, or an order has been shipped). This topic describes the steps for creating, uploading, and configuring the email templates that are used to send transactional emails.

## Create an email template

Before you can map a specific transactional event to an email template, you must create the template.

To create an email template, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Organization email templates**.
1. Select **New**.
1. Under **General**, set the following fields:

    - **Email ID** – The email ID is the unique identifier for a template, and it's the value that is shown when you select a template to map to an event.
    - **Email description** – You can use this optional field to provide a description of the template. The value that you enter appears only in Commerce headquarters.
    - **Sender name** – The name that you enter appears in the "from" field of most email clients.
    - **Sender email** – Enter the email address that should be used for emails that are sent by using this template.
    - **Default language code** – This field specifies the localized version of the email that is sent by default, if no language is provided by the channel that invokes this template.

1. Under **Email message content**, select **New**.
1. In the **Language** field, enter the language for the email template. You can add more languages and localized templates later.
1. In the **Subject** field, enter the email subject that should appear in the subject field of the email.
1. Select **Edit** to upload your email template.

## Create an email message body by using HTML

The message body of your email is composed in HTML. You can use any layout, styling, and branding that HTML and inline Cascading Style Sheets (CSS) allow for. You can also use images, if you host them on a publicly available web endpoint. To add an image, enter the image's URL in the **src** attribute of the HTML **&lt;img&gt;** tag.

> [!NOTE]
> Email clients impose layout and style limitations that might require adjustments to the HTML and CSS that you use for the message body. We recommend that you familiarize yourself with the best practices for creating HTML that will be supported by the most popular email clients.

## Add placeholders to the email message body

Your email can contain placeholders that are replaced with customer-specific and transaction-specific values when the email is generated. Placeholders are always surrounded by percent signs (%) and are inserted directly into the HTML document.

Here is an example.

```html
<p>
    Hello %customername%,<br />
    Order number %salesid%, can be picked up from the <b>%pickupstorename%</b> store.
</p>
```

### Order placeholders (sales order level)

The following placeholders retrieve and show data that is defined at the sales order level (as opposed to the sales line level).

| Placeholder name    | Placeholder value                                                |
|---------------------|------------------------------------------------------------------|
| customername        | The name of the customer who placed the order.                   |
| salesid             | The sales ID of the order.                                       |
| deliveryaddress     | The delivery address for shipped orders.                         |
| customeraddress     | The address of the customer.                                     |
| deliverydate        | The delivery date.                                               |
| shipdate            | The ship date.                                                   |
| modeofdelivery      | The delivery mode of the order.                                  |
| charges             | The total charges for the order.                                 |
| tax                 | The total tax for the order.                                     |
| total               | The total amount for the order.                                  |
| ordernetamount      | The total amount for the order, minus the total tax.             |
| discount            | The total discount for the order.                                |
| storename           | The name of the store where the order was placed.                |
| storeaddress        | The address of the store that placed the order.                  |
| storeopenfrom       | The opening time of the store that placed the order.             |
| storeopento         | The closing time of the store that placed the order.             |
| pickupstorename     | The name of the store where the order will be picked up.         |
| pickupstoreaddress  | The address of the store where the order will be picked up.      |
| pickupopenstorefrom | The opening time of the store where the order will be picked up. |
| pickupopenstoreto   | The closing time of the store where the order will be picked up. |

### Order line placeholders (sales line level)

The following placeholders retrieve and show data for individual products (lines) in the sales order.

| Placeholder name               | Placeholder value |
|--------------------------------|-------------------|
| productid                      | The product ID for the line. |
| lineproductname                | The name of the product. |
| lineproductdescription         | The description of the product. |
| linequantity                   | The number of units that were ordered for the line, plus the unit of measure (for example, **ea**, or **pair**). |
| lineunit                       | The unit of measure for the line. |
| linequantity_withoutunit       | The number of units that were ordered for the line, without the unit of measure. |
| linequantitypicked             | When the **PickOrder** event is used, the number of units that were picked. Otherwise, **0** (zero). |
| linequantitypicked_withoutunit | When the **PickOrder** event is used, the number of units that were picked, without the unit of measure. Otherwise, **0** (zero). |
| linequantitypacked             | When the **PackOrder** and **Order ready for pickup** events are used, the number of units that were packed. Otherwise, **0** (zero). |
| linequantitypacked_withoutuom  | When the **PackOrder** and **Order ready for pickup** events are used, the number of units that were packed, without the unit of measure. Otherwise, **0** (zero). |
| linequantityshipped            | Always **0**, except when specific events are used, as described in the next row. |
| linequantityshipped_withoutuom | When the **ShipOrder** event is used, the number of units that were picked, without the unit of measure. Otherwise, **0** (zero). |
| lineprice                      | The price of a single unit. |
| linenetamount                  | The price of the line after the number of units and discount are applied. |
| linediscount                   | The discount for an individual unit. |
| lineshipdate                   | The ship date for the line. |
| linedeliverydate               | The delivery date for the line. |
| linedeliverymode               | The delivery mode for the line. |
| linedeliveryaddress            | The delivery address for the line. |
| giftcardnumber                 | The gift card number, for products of the gift card type. |
| giftcardbalance                | The gift card balance, for products of the gift card type. |
| giftcardmessage                | The gift card message, for products of the gift card type. |
| giftcardpin                    | The personal identification number (PIN) of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| giftcardexpiration             | The expiration date of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| giftcardrecipientname          | The name of the gift card recipient, for products of the gift card type. |
| giftcardbuyername              | The name of the gift card buyer, for products of the gift card type. |

### Format of order line placeholders in the email message body

When you create the HTML for the individual order lines in the email message body, surround the repeating block of HTML and placeholders for the lines with the following placeholders that are put inside HTML comment tags.

```html
<!--%tablebegin.salesline%-->

(Insert the repeating block of HTML and placeholders for individual lines here.)

<!--%tableend.salesline%-->
```

Here is an example.

```HTML
<table>
    <tr>
        <td>Product name</td>
        <td>Quantity</td>
        <td>Price</td>
    </tr>
    <!--%tablebegin.salesline%-->
    <tr>
        <td>%lineproductname%</td>
        <td>%linequantity_withoutunit%</td>
        <td>%lineprice%</td>
    </tr>
    <!--%tableend.salesline%-->
</table>
```

## Create a template for emailed receipts

Receipts can be emailed to customers who make purchases at a retail point of sale (POS). In general, the steps for creating the emailed receipt template are the same as the steps for creating templates for other transactional events. However, the following changes are required:

- The email ID of the email template must be **emailRecpt**.
- The text of the receipt is inserted into the email by using the **%message%** placeholder. To ensure that the receipt body is correctly rendered, surround the **%message%** placeholder with HTML **&lt;pre&gt;** and **&lt;/pre&gt;** tags.
- Line breaks in the HTML for the header and footer of the email are converted to HTML **&lt;br /&gt;** tags so that the receipt body is rendered correctly. To eliminate unwanted vertical space in your receipt emails, remove line breaks from any place in the HTML where vertical space isn't required.

For more information about how to configure email receipts, see [Set up email receipts](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-email-receipts).

## Upload the email HTML

After you've created and tested the HTML for your message body, it must be uploaded to Commerce headquarters. Currently, email HTML can't be exported. Therefore, you must maintain the master copy of your HTML outside Commerce headquarters.

To upload a new or edited email template HTML, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Organization email templates**.
1. Select the row for the language that you want to add or replace HTML for. Alternatively, select **New** to create a row for a new language.
1. Select **Edit**.
1. In the dialog box that appears, select **Browse**. Browse to the HTML document that you want to upload, select it, and then select **Open**.
1. Select **Upload**.
1. After your email HTML appears in the preview window, select **OK**.
1. Make sure that the **Has body** check box is selected for the row.

If you've already configured Commerce headquarters to send email, your new or updated email will be sent to all customers who perform a transaction that invokes the event that is mapped to the template.

For more information about how to configure emails in Dynamics 365 Commerce, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md).

## Additional resources 

[Set up an email notification profile](email-notification-profiles.md)

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md)

[Set up email receipts](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-email-receipts)

[Send email receipts from Modern POS ](email-receipts.md)
