---
# required metadata

title: Create email templates for transactional events
description: This topic describes how to assemble and upload email templates.
author: stuharg
manager: annbe
ms.date: 04/07/2020
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

## Overview

Dynamics 365 Commerce provides an out-of-box solution for sending emails to customers when they place an online order, their order is ready for in-store pickup, their order ships, and other transactional events. This help topic covers the steps for assembling, uploading and configuring the email templates that send those emails. 

## Template creation

Before you can map a specific transactional event to an email template, you must first create the template. To create a new email template:

1. In Headquarters, go to **Retail and Commerce** > **Headquarters setup** > Organization email templates
1. Click **+New**
1. Under **General**, enter values for the following fields: 
    1. **Email ID**: The email ID is the unique identifier for this template and is the value that is shown when selecting a template to map to an event
    1. **Email description**: Optional field for providing a description of the template. The value you enter only appears in Headquarters
    1. **Sender name**: The value that appears in the From: field of most email clients.
    1. **Sender email**: The from and reply-to email address for emails sent with this template.
    1. **Default language code**: Specifies the localized version of the email that is sent by default, if no language is provided by the channel that invokes this template.
1. Under **Email message content**, click **+New**
1. Enter the language for the email template. You can add more languages and localized templates later.
1. Enter the email subject that will appear in the Subject field of the email
1. Click **Edit** to upload your email template HTML

## Creating an email HTML message body

The message body of your email is composed with HTML. You can create any layout, styles and branding that HTML and inline CSS allows. Images can be used as well if you host your images on a publicly available web endpoint and insert their URL into the src attribute of the HTML img tag. NOTE: Email clients impose layout and style limitations that may require adjustments to the HTML and CSS you use for the message body. We recommend that you familiarize yourself with best practices for authoring HTML that will be supported by the most popular email clients.

## Adding placeholders

Your email may contain placeholders that are replaced with customer and transaction-specific values when the email is generated. Placeholders are always surrounded by percent (%) characters (e.g. %customername%) and are inserted directly into the HTML document. 

## Order header placeholders

| **Placeholder  name** | **Description**                                              |
| --------------------- | ------------------------------------------------------------ |
| customername          | Name  of the customer who placed the order                   |
| salesid               | Sales  ID of the order                                       |
| deliveryaddress       | Delivery  address for shipped orders                         |
| customeraddress       | Address  of the customer                                     |
| deliverydate          | Delivery  date                                               |
| shipdate              | Ship  date                                                   |
| modeofdelivery        | Delivery  mode of the order                                  |
| charges               | Total  charges for the order                                 |
| tax                   | Total  tax for the order                                     |
| total                 | Total  amount for the order                                  |
| ordernetamount        | Total  amount for the order minus total tax                  |
| discount              | Total  discount for the order                                |
| storename             | Name  of the store where the order was placed                |
| storeaddress          | Address of the store that placed the order[[AR2\]](#_msocom_2) |
| storeopenfrom         | Opening  time of the store that placed the order             |
| storeopento           | Closing  time of the store that placed the order             |
| pickupstorename       | Name of the pickup store                                     |
| pickupstoreaddress    | Address of the pickup store                                  |
| pickupopenstorefrom   | Opening time of the pickup store                             |
| pickupopenstoreto     | Closing time of the pickup store                             |

## Order lines in the message body

When creating the HTML for individual lines in the message body, surround the repeating block of HTML and placeholders for individual lines with the following placeholders within HTML comment tags:

&lt;!--%tablebegin.salesline%--&gt;

Insert HTML that repeats for individual lines here

&lt;!--%tableend.salesline%--&gt;

## Order line placeholders 

The following placeholders display information for individual lines in the order. 

| **Placeholder  name**          | **Placeholder value**                                        |
| ------------------------------ | ------------------------------------------------------------ |
| productid                      | Product ID for this line                                     |
| lineproductname                | Name of the product                                          |
| lineproductdescription         | Description of the product                                   |
| linequantity                   | Number of units ordered for this line, with the unit of measure appended |
| lineunit                       | Unit of measure for this line (e.g. “ea”, “pair”, etc)       |
| linequantity_withoutunit       | Number of units ordered for this line, without the unit of measure |
| linequantitypicked             | Number of units picked when used with PickOrder event, or zero (0) otherwise |
| linequantitypicked_withoutunit | Number of units picked when used with the PickOrder event, without the unit of  measure, or zero (0) otherwise |
| linequantitypacked             | Number of units packed when used with PackOrder and Order ready  for pickup event, [[AR3\]](#_msocom_3) or  zero (0) otherwise |
| linequantitypacked_withoutuom  | Number of units packed when used with the PackOrder and Order ready for pickup event,  without the unit of measure, or zero (0) otherwise |
| linequantityshipped            | Always 0 except specific events detailed below               |
| linequantityshipped_withoutuom | Number of units picked when used with the ShipOrder event, without the unit of  measure, or zero (0) otherwise |
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
| giftcardpin                    | Gift card PIN for products of type gift card. Specific to external gift cards |
| giftcardexpiration             | Gift card expiration date for products of type gift card. Specific to external  gift cards |
| giftcardrecipientname          | Gift card recipient name for products of type gift card      |
| giftcardbuyername              | Gift card buyer name for products of type gift card          |

## Creating a template for emailed receipts

Receipts can be emailed to customers who make purchases at a retail point of sale. The steps required for creating the email template are the same as for other transactional events, with the following additions. 

1. The Email ID of the email template must be **emailRecpt**.
1. The text of the receipt is inserted into the email using the %message% placeholder. NOTE: In order to correctly render the receipt body, surround the %message% placeholder with HTML &lt;pre&gt;&lt;/pre&gt; tags. 
1. Line breaks in the HTML for the header and footer of the email are converted to HTML &lt;br /&gt; tags so that the receipt body renders correctly. In order to eliminate unwanted vertical space in your receipt emails, remove all line breaks from the HTML where vertical space is not wanted. 

For more information about how to configure email receipts, see [Set up email receipts](appuser-itpro/set-up-email-receipts)

## Upload your email HTML

After you have created and tested the HTML for your message body, it must be uploaded to Headquarters. Currently, email HTML cannot be exported, so you must maintain the master copy of our HTML outside of Dynamics Headquarters.
To upload new or edited email template HTML:

1. Select the row for the language you want to add or replace HTML for, or create a row for a new language by clicking  +New
1. Click **Edit**
1. Click **Browse**, navigate to the HTML document you wish to upload, and open it
1. Click **Upload**
1. After your email HTML appears in the preview window, click **OK**
1. Ensure that the **Has body** checkbox is checked for the row

If you have already configured Headquarters to send email, your changes will go out to customers who conduct a transaction that invokes the event that is mapped to the template.  For more information about configuring emails in Dynamics 365 Commerce, see [Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json). 

## Additional resources 

[Set up an email notification profile](email-notification-profiles)

[Configure and send email](../fin-ops-core/fin-ops/organization-administration/configure-email.md?toc=/dynamics365/commerce/toc.json)

[Set up email receipts](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-email-receipts)

[Send email receipts from Modern POS ](https://docs.microsoft.com/en-us/dynamics365/commerce/email-receipts)


