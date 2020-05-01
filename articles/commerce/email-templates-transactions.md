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

Dynamics 365 Commerce provides an out-of-box solution for sending emails that alert customers about transactional events such as an order being placed, an order being ready for pickup, or an order having been shipped. This topic covers the steps for assembling, uploading, and configuring the email templates used to send transactional emails. 

## Create an email template

Before you can map a specific transactional event to an email template, you must first create the template. 

To create a new email template, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup > Organization email templates**.
1. Select **+New**.
1. Under **General**, enter or select values for the following fields: 
    - **Email ID**: The email ID is the unique identifier for a template and is the value that is shown when selecting a template to map to an event.
    - **Email description**: This is an optional field for providing a description of the template. The value you enter only appears in Commerce headquarters.
    - **Sender name**: This is the name that appears in the "From" field of most email clients.
    - **Sender email**: This is the email address for emails sent with this template.
    - **Default language code**: This value specifies the localized version of the email that is sent by default, if no language is provided by the channel that invokes this template.
    - Under **Email message content**, select **+New**.
1. Under **Language**, enter or select the language for the email template. You can add more languages and localized templates later.
1. Under **Subject**, enter the email subject that will appear in the subject field of the email.
1. Select **Edit** to upload your email template.

## Create an email message body with HTML

The message body of your email is composed with HTML. You can use any layout, styling, and branding that HTML and inline cascading style sheets (CSS) allow. Images can also be used if you host your images on a publicly available web endpoint and insert the image URL into the **src** attribute of the HTML **&lt;img&lt;** tag. 

>[!NOTE] 
> Email clients impose layout and style limitations that may require adjustments to the HTML and CSS you use for the message body. It is recommended that you familiarize yourself with best practices for authoring HTML that will be supported by the most popular email clients.

## Add placeholders

Your email may contain placeholders that are replaced with customer and transaction-specific values when the email is generated. Placeholders are always surrounded by percent (%) characters and are inserted directly into the HTML document. 

For example:
```
<p>
    Hello %customername%,<br />
    Order number %salesid%, can be picked up from the <b>%pickupstorename%</b> store.
</p>
```
### Order placeholders (sales order level)

The following placeholders retrieve and display data that are defined at the sales order level (as opposed to the sales line level). 

| **Placeholder name**  | **Placeholder value**                                              |
| --------------------- | ------------------------------------------------------------ |
| customername          | Name of the customer who placed the order                   |
| salesid               | Sales ID of the order                                        |
| deliveryaddress       | Delivery address for shipped orders                          |
| customeraddress       | Address of the customer                                      |
| deliverydate          | Delivery date                                                |
| shipdate              | Ship date                                                    |
| modeofdelivery        | Delivery mode of the order                                   |
| charges               | Total charges for the order                                  |
| tax                   | Total tax for the order                                      |
| total                 | Total amount for the order                                   |
| ordernetamount        | Total amount for the order minus total tax                   |
| discount              | Total discount for the order                                 |
| storename             | Name of the store where the order was placed                 |
| storeaddress          | Address of the store that placed the order                   |
| storeopenfrom         | Opening time of the store that placed the order              |
| storeopento           | Closing time of the store that placed the order              |
| pickupstorename       | Name of the pickup store                                     |
| pickupstoreaddress    | Address of the pickup store                                  |
| pickupopenstorefrom   | Opening time of the pickup store                             |
| pickupopenstoreto     | Closing time of the pickup store                             |

### Order line placeholders (sales line level)

The following placeholders retrieve and display data for individual products (lines) in the sales order. 

| **Placeholder name**           | **Placeholder value**                                        |
| ------------------------------ | ------------------------------------------------------------ |
| productid                      | Product ID for this line                                     |
| lineproductname                | Name of the product                                          |
| lineproductdescription         | Description of the product                                   |
| linequantity                   | Number of units ordered for this line, with the unit of measure appended |
| lineunit                       | Unit of measure for this line (for example, "ea", "pair", etc.)       |
| linequantity_withoutunit       | Number of units ordered for this line, without the unit of measure |
| linequantitypicked             | Number of units picked when used with **PickOrder** event, or zero (0) otherwise |
| linequantitypicked_withoutunit | Number of units picked when used with the **PickOrder** event, without the unit of measure, or zero (0) otherwise |
| linequantitypacked             | Number of units packed when used with **PackOrder** and **Order ready for pickup** events, or zero (0) otherwise |
| linequantitypacked_withoutuom  | Number of units packed when used with the **PackOrder** and **Order ready for pickup** events, without the unit of measure, or zero (0) otherwise |
| linequantityshipped            | Always 0 except specific events detailed below               |
| linequantityshipped_withoutuom | Number of units picked when used with the **ShipOrder** event, without the unit of measure, or zero (0) otherwise |
| lineprice                      | Price of a single unit                                       |
| linenetamount                  | Price of the line, with number of units and discount applied |
| linediscount                   | Discount for an individual unit                              |
| lineshipdate                   | Ship date for this line                                      |
| linedeliverydate               | Delivery date for this line                                  |
| linedeliverymode               | Delivery mode for this line                                  |
| linedeliveryaddress            | Delivery address for this line                               |
| giftcardnumber                 | Gift card number for products of type gift card              |
| giftcardbalance                | Gift card balance for products of type gift card             |
| giftcardmessage                | Gift card message for products of type gift card             |
| giftcardpin                    | Gift card PIN for products of type gift card (specific to external gift cards) |
| giftcardexpiration             | Gift card expiration date for products of type gift card (specific to external gift cards) |
| giftcardrecipientname          | Gift card recipient name for products of type gift card      |
| giftcardbuyername              | Gift card buyer name for products of type gift card          |

### Example of order line placeholders in the message body

When creating the HTML for individual order lines in the message body, surround the repeating block of HTML and placeholders for individual lines with the following placeholders within HTML comment tags as follows.

&lt;!--%tablebegin.salesline%--&gt;

*Insert repeating block of HTML and placeholders for individual lines here.*

&lt;!--%tableend.salesline%--&gt;

For example:

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

Receipts can be emailed to customers who make purchases at a retail point of sale (POS). The steps required for creating the emailed receipt template are the same as for other transactional events, with the following modifications. 

- The email ID of the email template must be **emailRecpt**.
- The text of the receipt is inserted into the email using the **%message%** placeholder. To correctly render the receipt body, surround the **%message%** placeholder with HTML **&lt;pre&gt;&lt;/pre&gt;** tags. 
- Line breaks in the HTML for the header and footer of the email are converted to HTML **&lt;br /&gt;** tags so that the receipt body renders correctly. To eliminate unwanted vertical space in your receipt emails, remove all line breaks from the HTML where vertical space is not necessary. 

For more information about how to configure email receipts, see [Set up email receipts](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-email-receipts).

## Upload your email HTML

After you have created and tested the HTML for your message body, it needs to be uploaded to Commerce headquarters. Currently, email HTML cannot be exported, so you must maintain the master copy of your HTML outside of headquarters.

To upload a new or edited email template HTML, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup > Organization email templates**.
1. Select the row for the language you want to add or replace HTML for, or create a row for a new language by selecting **+New**.
1. Select **Edit**.
1. In the flyout menu on the right, select **Browse** to navigate to the HTML document that you wish to upload, select it, and then select **Open**.
1. Select **Upload**.
1. After your email HTML appears in the preview window, select **OK**.
1. Ensure that the **Has body** checkbox is selected for the row.

If you have already configured Commerce headquarters to send email, your changes will go out to customers who conduct a transaction that invokes the event that is mapped to the template. 

For more information about configuring emails in Dynamics 365 Commerce, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json). 

## Additional resources 

[Set up an email notification profile](email-notification-profiles)

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json)

[Set up email receipts](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-email-receipts)

[Send email receipts from Modern POS ](https://docs.microsoft.com/en-us/dynamics365/commerce/email-receipts)


