---
title: Create email templates for transactional events
description: This article describes how to create, upload, and configure email templates for transactional events in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 02/02/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: stuharg
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8
ms.custom: 
ms.assetid: 
---
# Create email templates for transactional events

[!include [banner](includes/banner.md)]


This article describes how to create, upload, and configure email templates for transactional events in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce provides an out-of-box solution for sending emails that alert customers about transactional events. For example, emails can be sent when an order is placed, is ready for pickup, or has been shipped. This article describes the steps for creating, uploading, and configuring the email templates that are used to send transactional emails.

## Notification types

Notifications can be configured to inform customers via email when specific events occur as part of the order and customer lifecycle. To configure notifications, you must map an email template to a notification type by creating a Commerce email notification profile. For information about how to set up email notification profiles, see [Set up an email notification profile](email-notification-profiles.md).

Dynamics 365 Commerce supports the following notification types.

### Order created

The *order created* notification type is triggered when a new sales order is created in Commerce headquarters.

> [!NOTE]
> The order created notification type isn't triggered for cash-and-carry transactions that occur at a point of sale (POS) terminal. In this case, an emailed and/or printed receipt is generated instead. For more information, see [Send email receipts from Store Commerce](email-receipts.md).

### Order confirmed

The *order confirmed* notification type is triggered when an order confirmation document is generated for a sales order from Commerce headquarters.

### Picking completed

The *picking completed* notification type is triggered when a picking list for an order is marked as completed in Commerce headquarters.

> [!NOTE]
> The picking completed notification type isn't triggered when an item is marked as picked at a POS terminal.

### Packing completed

The *packing completed* notification type is triggered when a packing slip document is generated for an order in Commerce headquarters at a POS terminal.

The packing completed notification type supports the following additional email placeholders to facilitate "order ready for pickup" and order lookup functionality from transactional emails.

| Placeholder name    | Purpose |
| ------------------- | ------- |
| `pickupstorename`     | The name of the store where the order is available for pickup. |
| `pickupstoreaddress`  | The address of the store where the order is available for pickup. |
| `pickupstoreopenfrom` | The opening hour of the pickup store. |
| `pickupstoreopento` | The closing hour of the pickup store. |
| `pickupchannelid`     | The store channel ID of the pickup store. |
| `packingslipid`      | The ID of the packing slip for the order that will be picked up. |
| `confirmationid`      | The order confirmation ID of the order that will be picked up. (This ID is sometimes referred to as the channel reference ID.) |

For more information about the customer check-in and order lookup features, see [Set up geo detection and redirection](geo-detection-redirection.md) and [Enable order lookup for guest checkouts](order-lookup-guest.md).

### Order ready for pickup

The *order ready for pickup* notification type is triggered when an order is marked as packed, and the mode of delivery is set to **Customer pickup** on one or more order lines.

> [!NOTE]
> The order ready for pickup notification type has been deprecated in favor of the packing completed notification type. This notification type is customized by mode of delivery.

### Order shipped

The *order shipped* notification type is triggered when an order that has a non-store-pickup mode of delivery is invoiced.

> [!NOTE]
> The order shipped notification type has been deprecated in favor of the order invoiced notification type. This notification type is customized by mode of delivery.

### Order invoiced

The *order invoiced* notification type is triggered when an order is invoiced in POS or Commerce headquarters.

### Issue gift card

The *issue gift card* notification type is triggered when a sales order that contains a product of the gift card type is invoiced.

> [!NOTE]
> The issue gift card notification email is sent to the gift card recipient. The gift card recipient is specified in Commerce headquarters, on an individual sales order line on the **Packing** tab under **Line details**. It can be specified either manually or programmatically.

The issue gift card notification type supports the following additional placeholders.

| Placeholder name      | Purpose |
| --------------------- | ------- |
| `giftcardnumber`        | The gift card number, for products of the gift card type. |
| `availablebalance` | The remaining balance on the gift card. |
| `giftcardmessage`       | The gift card message, for products of the gift card type. |
| `giftcardpin`         | The personal identification number (PIN) of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| `giftcardexpiration`    | The expiration date of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| `giftcardrecipientname` | The name of the gift card recipient, for products of the gift card type. |
| `giftcardbuyername`     | The name of the gift card buyer, for products of the gift card type. |

For more information about gift cards, see [E-commerce digital gift cards](digital-gift-cards.md) and [Support for external gift cards](dev-itpro/gift-card.md).

### Order cancellation

The *order cancellation* notification type is triggered when an order is canceled in Commerce headquarters.

### Customer created

The *customer created* notification type is triggered when a new customer entity is created in Commerce headquarters. 

To enable customer created notifications, in Commerce headquarters go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters \> General**. In the **Email notification profile** drop-down list, select an email notification profile that contains the customer created notification type. 

By default, customer created events are uploaded to headquarters with the **Synchronize customers and channel requests** batch job. If you want to use a real-time service call to send these events, set the email ID of the customer created template to **newCust**. However, this is not recommended because real-time service calls are "fire and forget" calls and do not have the fallback or retry logic that batch jobs provide.

> [!NOTE] 
> When you enable customer created notifications, customers that are created in all channels within the legal entity will receive a customer created email. Currently, customer created notifications can't be limited to a single channel.  

When invoked through the batch job, the customer created notification type supports the following placeholder.

| Placeholder name | Description                                                      |
| ---------------- | ------------------------------------------------------------ |
| customername     | The first and last name of the customer who created an account. |

When invoked through a real time service call, the customer created notification type supports the following placeholders.

| Placeholder name | Description                                                      |
| ---------------- | ------------------------------------------------------------ |
| Name             | The first and last name of the customer who created an account. |
| Email            | The email address of the customer who created an account.    |
| Phone            | The phone number of the customer who created an account.      |
| Url              | The URL provided by the customer when they created the account. |

### B2B prospect approved

The *B2B prospect approved* notification type is triggered when a prospect's onboarding request is approved in Commerce headquarters. For more information about how to approve or reject B2B prospects, see [Set up the administrator user for a new business partner](b2b/manage-b2b-users.md#set-up-the-administrator-user-for-a-new-business-partner). 

The B2B prospect approved notification type supports the following additional placeholders.

| Placeholder name | Purpose                                                      |
| ---------------- | ------------------------------------------------------------ |
| `firstname`       | The first name of the B2B prospect as it's entered in the application. |
| `lastname`         | The last name of the B2B prospect as it's entered in the application. |
| `company`          | The name of the applicant's company as it's entered in the application. |
| `email`            | The prospect's email address as it's entered in the application.   |
| `zipcode`          | The ZIP/postal code of the prospect's primary address. |
| `comments`         | The comment that the prospect entered in the application. |
| `storename`        | The name of the channel where the prospect was created. |
| `storeurl`         | Empty by default. A custom extension must be created to use this placeholder. |

### B2B prospect rejected

The *B2B prospect rejected* notification type is triggered when a prospect's onboarding request is rejected in Commerce headquarters. For more information about how to approve or reject B2B prospects, see [Set up the administrator user for a new business partner](b2b/manage-b2b-users.md#set-up-the-administrator-user-for-a-new-business-partner). 

The B2B prospect rejected notification type supports the following additional placeholders.

| Placeholder name | Purpose                                                      |
| ---------------- | ------------------------------------------------------------ |
| `firstname`        | The first name of the B2B prospect as it's entered in the application. |
| `lastname`         | The last name of the B2B prospect as it's entered in the application. |
| `company`          | The name of the applicant's company as it's entered in the application. |

## Create an email template

Before you can map a specific transactional event to an email template, you must create the template.

To create an email template, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Organization email templates** or **Organization administration \> Setup \> Organization email templates**.
1. Select **New**.
1. Under **General**, set the following fields:

    - **Email ID** – The email ID is the unique identifier for a template. It's the value that is shown when you select a template to map to an event.
    - **Email description** – You can use this optional field to provide a description of the template. The value that you enter appears only in Commerce headquarters.
    - **Sender name** – The name that you enter appears in the "from" field of most email clients.
    - **Sender email** – Enter the email address that should be used for emails that are sent by using this template.
    - **Default language code** – This field specifies the localized version of the email that is sent by default, if the channel that invokes this template doesn't specify a language.

1. Under **Email message content**, select **New**.
1. In the **Language** field, enter the language for the email template. You can add more languages and localized templates later.
1. In the **Subject** field, enter the email subject that should appear in the subject field of the email.
1. Select **Edit** to upload your email template.

## Create an email message body by using HTML

The message body of your email is composed in HTML. You can use any layout, styling, and branding that HTML and inline Cascading Style Sheets (CSS) allow for. You can also use images, if you host them on a publicly available web endpoint. To add an image, enter the image's URL in the **src** attribute of the HTML **&lt;img&gt;** tag.

> [!NOTE]
> Email clients impose layout and style limitations that might require adjustments to the HTML and CSS that you use for the message body. We recommend that you familiarize yourself with the best practices for creating HTML that the most popular email clients will support.

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

| Placeholder name     | Purpose                                                      |
| -------------------- | ------------------------------------------------------------ |
| `customername`         | The name of the customer who placed the order.               |
| `customeraddress`      | The address of the customer.                                 |
| `customeremailaddress` | The email address that the customer entered at checkout.     |
| `salesid`              | The sales ID of the order.                                   |
| `orderconfirmationid`  | The cross-channel ID that was generated at order creation.   |
| `channelid`            | The ID of the retail or online channel that the order was placed through. |
| `deliveryname`         | The name that is specified for the delivery address.         |
| `deliveryaddress`      | The delivery address for shipped orders.                     |
| `deliverydate`         | The delivery date.                                           |
| `shipdate`             | The ship date.                                               |
| `modeofdelivery`       | The delivery mode of the order.                              |
| `ordernetamount`       | The total amount for the order, minus the total tax.         |
| `discount`            | The total discount for the order.                            |
| `charges`              | The total charges for the order.                             |
| `tax`                  | The total tax for the order.                                 |
| `total`                | The total amount for the order.                              |
| `storename`            | The name of the store where the order was placed.            |
| `storeaddress`         | The address of the store that placed the order.              |
| `storeopenfrom`        | The opening time of the store that placed the order.         |
| `storeopento`          | The closing time of the store that placed the order.         |
| `pickupstorename`      | The name of the store where the order will be picked up.\*   |
| `pickupstoreaddress`   | The address of the store where the order will be picked up.\* |
| `pickupopenstorefrom`  | The opening time of the store where the order will be picked up.\* |
| `pickupopenstoreto`    | The closing time of the store where the order will be picked up.\* |
| `pickupchannelid`     | The channel ID of the store that is specified for a pickup mode of delivery.\* |
| `packingslipid`        | The ID of the packing slip that was generated when lines in an order were packed.\* |

\* These placeholders return data only when they are used for the **Order ready for pickup** notification type. 

### Order line placeholders (sales line level)

The following placeholders retrieve and show data for individual products (lines) in the sales order.

| Placeholder name               | Purpose |
|--------------------------------|-------------------|
| `productid`                      | <p>The ID of the product. This ID accounts for variants.</p><p><strong>Note:</strong> This placeholder has been deprecated in favor of `lineproductrecid`.</p> |
| `lineproductrecid`               | The ID of the product. This ID accounts for variants. It uniquely identifies an item at the variant level. |
| `lineitemid`                     | The product-level ID of the product. (This ID doesn't account for variants.) |
| `lineproductvariantid`           | The ID of the product variant. |
| `lineproductname`                | The name of the product. |
| `lineproductdescription`         | The description of the product. |
| `linequantity`                   | The number of units that were ordered for the line, plus the unit of measure (for example, **ea**, or **pair**). |
| `lineunit`                       | The unit of measure for the line. |
| `linequantity_withoutunit`       | The number of units that were ordered for the line, without the unit of measure. |
| `linequantitypicked`             | When the **PickOrder** event is used, the number of units that were picked. Otherwise, **0** (zero). |
| `linequantitypicked_withoutunit` | When the **PickOrder** event is used, the number of units that were picked, without the unit of measure. Otherwise, **0** (zero). |
| `linequantitypacked`             | When the **PackOrder** and **Order ready for pickup** events are used, the number of units that were packed. Otherwise, **0** (zero). |
| `linequantitypacked_withoutuom`  | When the **PackOrder** and **Order ready for pickup** events are used, the number of units that were packed, without the unit of measure. Otherwise, **0** (zero). |
| `linequantityshipped`            | Always **0**, except when specific events are used, as described in the next row. |
| `linequantityshipped_withoutuom` | When the **ShipOrder** event is used, the number of units that were picked, without the unit of measure. Otherwise, **0** (zero). |
| `lineprice`                      | The price of a single unit. |
| `linenetamount`                  | The price of the line after the number of units and discount are applied. |
| `linediscount`                   | The discount for an individual unit. |
| `lineshipdate`                   | The ship date for the line. |
| `linedeliverydate`               | The delivery date for the line. |
| `linedeliverymode`               | The delivery mode for the line. |
| `linedeliveryaddress`            | The delivery address for the line. |
| `linepickupdate`                 | The pickup date that the customer specified, for orders that use a pickup mode of delivery. |
| `linepickuptimeslot`             | The pickup time range that the customer specified, for orders that use a pickup mode of delivery. |
| `giftcardnumber`                 | The gift card number, for products of the gift card type. |
| `giftcardbalance`                | The gift card balance, for products of the gift card type. |
| `giftcardmessage`                | The gift card message, for products of the gift card type. |
| `giftcardpin`                    | The PIN of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| `giftcardexpiration`             | The expiration date of the gift card, for products of the gift card type. (This placeholder is specific to external gift cards.) |
| `giftcardrecipientname`          | The name of the gift card recipient, for products of the gift card type. |
| `giftcardbuyername`              | The name of the gift card buyer, for products of the gift card type. |

### Format of order line placeholders in the email message body

When you create the HTML for the individual order lines in the email message body, surround the repeating block of HTML and placeholders for the lines with the following placeholders. Notice that the placeholders are inside HTML comment tags.

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

- The **%message%** placeholder is used to insert the text of the receipt into the email. To ensure that the receipt body is correctly rendered, surround the **%message%** placeholder with HTML **&lt;pre&gt;** and **&lt;/pre&gt;** tags.
- The **%receiptid%** placeholder can be used to show a QR code or bar code that represents the receipt ID. (QR codes and bar codes are dynamically generated and served by a third-party service.) For more information about how to show a QR code or bar code in an emailed receipt, see [Add a QR code or bar code to transactional and receipt emails](add-qr-code-barcode-email.md).

## Upload the email HTML

After you've created and tested the HTML for your message body, it must be uploaded to Commerce headquarters. Currently, email HTML can't be exported. Therefore, you must maintain the master copy of your HTML outside Commerce headquarters.

To upload a new or edited email template HTML, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Organization email templates**.
1. Select the row for the language that you want to add or replace HTML for. Alternatively, select **New** to create a row for a new language.
1. Select **Edit**.
1. In the dialog box that appears, select **Browse**. Browse to the HTML document that you want to upload, select it, and then select **Open**.
1. Select **Upload**.
1. After your email HTML appears in the preview window, select **OK**.
1. Make sure that the **Has body** checkbox is selected for the row.

If you've already configured Commerce headquarters to send email, your new or updated email will be sent to all customers who perform a transaction that invokes the event that is mapped to the template.

For more information about how to configure emails in Dynamics 365 Commerce, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md).

## Additional resources 

[Set up an email notification profile](email-notification-profiles.md)

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md)

[Set up email receipts](/dynamicsax-2012/appuser-itpro/set-up-email-receipts)

[Send email receipts from Store Commerce](email-receipts.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
