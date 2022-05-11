---
# required metadata

title: Send email receipts from Modern POS (MPOS)
description: In Modern Point of Sale (MPOS), you can send receipt emails when a transaction is tendered at the point of sale (POS).  
author: jashanno
ms.date: 11/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters, SysEmailTable,
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 252934
ms.assetid: 4b9f733b-bf28-4b85-94de-4f7adf67a62c
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Send email receipts from Modern POS (MPOS)

[!include [banner](includes/banner.md)]

In Modern Point of Sale (MPOS), you can send receipt emails when a transaction is tendered at the point of sale (POS).

## Prerequisite

To send email receipts, you must configure a Simple Mail Transfer Protocol (SMTP) server.

## Set up email receipts

### Set default options for email receipts

1. Select **Retail and Commerce &gt; Headquarters setup &gt; Parameters &gt; Commerce parameters**.
1. On the **Posting** tab, on the **Email receipt** FastTab, in the **Receipt option** field, select a default option:

    - **Standard receipt** – Print receipts from the POS register.
    - **Email** – Send receipts to customers in email messages.
    - **Both** – Print receipts from the POS register, and send receipts to customers in email messages.

1. In the **Subject** field, enter the text that should appear by default on the subject line of a receipt that is sent as an email message.

### Set email receipt options for a customer

1. Go to **Retail and Commerce &gt; Customers &gt; All customers**.
1. On the **All customers** list page, select a customer, and then select **Edit**.
1. On the customer details page, on the **Commerce** FastTab, in the **Receipt option** field, select an option:

    - **Standard receipt** – The customer will receive only printed receipts. The printed receipt is generated from the POS register.
    - **Email** – The customer will receive only email receipts.
    - **Both** – The customer will receive both printed receipts and email receipts.

1. If you selected either **Email** or **Both** in the **Receipt option** field, enter the customer's email address in the **Receipt email** field.

### Set up an email receipt profile

1. Go to **Retail and Commerce &gt; Channel setup &gt; POS setup &gt; POS profiles &gt; Receipt profiles**.
1. Select **Ctrl+N** to create a receipt profile.
1. Enter values in the **Receipt profile ID** and **Description** fields.
1. On the **General** FastTab, select **Add** to add a receipt type.
1. Select **Receipt** as the receipt type, and select the receipt format to use for email receipts.

### Add an email receipt profile to the functionality profile

1. Go to **Retail and Commerce &gt; Channel setup &gt; POS setup &gt; POS profiles &gt; Functionality profiles**.
1. Select **Edit**.
1. On the **General** FastTab, in the **Receipt profile ID** field, specify an email receipt profile.

### Set up an email template for receipts

1. Go to **Organization email templates** under either **Retail and Commerce &gt; Headquarters setup &gt; Setup &gt; Organization email templates** or **Organization administration &gt; Setup &gt; Organization email templates**.
1. Select **New**.
1. Enter information in the following fields:

    - In the **Email ID** field, enter a name for the template.
    - In the **Email description** field, enter an optional description.
    - In the **Sender name** field, specify the name that should appear as the sender of the email. Customers will see this name as the **From** name on the email.
    - In the **Sender email** field, specify a valid email address. Customers will see this email address as the **From** email address on the email.

1. Under **General**, in the **Default language code** field, select a language. The receipt will be sent in this language if templates for multiple languages are configured, and the store's or customer's preferred language doesn't match any of those additional languages. 
1. In the **Email message content** pane, select **New** to create a new template instance. Enter information in the following fields:

    - In the **Language** field, specify the language this template will be localized in. Note that this only applies to emailed receipts that contain HTML with static content above and/or below the %message% placeholder.
    - In the **Subject** field, enter a title for the email receipts.
    - Select the **Has body** check box.
    - Select **Edit** to upload your template HTML. At a minimum, your template instance must contain the following code: 

    ``` xml
    <pre>
    %message%
    </pre>
    ```

    You can also add HTML to show a header, footer, logo, or any other static content that you want to include in the receipt email. For more information about how to create HTML receipt templates, see [Create a template for emailed receipts](email-templates-transactions.md#create-a-template-for-emailed-receipts). 

1. Depending on the settings that you configured, you must run the appropriate distribution schedule jobs to synchronize the changes to MPOS.

    - **1010** – Customer
    - **1070** – Channel configuration
    - **1090** – Registers
    - **1110** – Global configuration

## Insert bar codes or QR codes in emailed receipts

You can insert QR codes or bar codes that represent order IDs into transactional and receipt emails. For more information, see [Add a QR code or bar code to a receipt email](add-qr-code-barcode-email.md#add-a-qr-code-or-bar-code-to-a-receipt-email). 

## MPOS transactions

After the changes are synchronized to the store, MPOS prompts the user for an email address for each transaction (if this feature is enabled). If an email address is already on file for the customer, that address appears in the email address prompt. If a customer hasn't been named, or if an email address hasn't been entered for a named customer, enter an email address, and then select **Send**. When the transaction is finalized, the real-time service will send the customer an email that has the receipt in the body of the message, as you configured earlier.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
