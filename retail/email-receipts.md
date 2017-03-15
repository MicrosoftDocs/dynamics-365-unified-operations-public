---
# required metadata

title: Send email receipts from Retail Modern POS
description: In Retail Modern Point of Sale (MPOS), you can send receipt emails at the time a transaction is tendered at the point of sale.  
author: josaw1
manager: AnnBe
ms.date: 2016-11-03 21 - 28 - 48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 252934
ms.assetid: 4b9f733b-bf28-4b85-94de-4f7adf67a62c
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Send email receipts from Retail Modern POS

In Retail Modern Point of Sale (MPOS), you can send receipt emails at the time a transaction is tendered at the point of sale.  

Prerequisite
------------

You must configure a SMTP server to send email receipts. For more information about email parameters, see [Email parameters page (field descriptions).](http://ax.help.dynamics.com/en/wiki/e-mail-parameters-page-field-descriptions/)

## Set up email receipts
### Set default options for email receipts

1.  Click **Retail and commerce &gt; Headquarters setup &gt; Parameters &gt; Retail parameters**.
2.  Click the **Posting** tab, and then under **Email receipt**, in the **Receipt option** field, select a default option:
    -   **Standard receipt** – Print receipts from the point of sale register.
    -   **E-mail** – Send receipts to customers in email messages.
    -   **Both** – Print receipts from the point of sale register and send receipts to customers in email messages.

3.  In the **Subject** field, enter the text that you want to appear by default in the subject line of a receipt that is sent as an email message.

### Set email receipt options for a customer

1.  Click **Retail and commerce &gt; Customers &gt; All customers**.
2.  On the **All customers** list page, select a customer, then click **Edit**.
3.  On the **Customers details** page, on the **Retail** FastTab, select an option in the **Receipt option** field:
    -   **Standard receipt** – The customer will receive only printed receipts. The printed receipt is generated from the point of sale register.
    -   **E-mail** – The customer will receive only email receipts.
    -   **Both** – The customer will receive both a printed receipt and an email receipt.

4.  In the **Receipt email** field, if you selected either **E-mail** or **Both** in the **Receipt option** field, enter the customer’s email address .

### Set up an email template for receipts

1.  Click **Organization Administration &gt; Setup &gt; E-mail Templates.**
2.  Press **CTRL**+**N** to create a new template.
3.  On the **Overview** tab, complete the following:
    -   **E-mail ID** - Enter *EmailRecpt*.
    -   **E-mail description **- Enter a description.
    -   **Default language code **- Select the  language.
    -   **Sender name **- Specify a name to appear as the sender of the email. Customers will see this name on the email as the **From** name.
    -   **Sender e-mail **- Specify a valid email address. Customers will see this email address as the **From** email address.

4.  In the lower grid, configure the following:
    -   **E-mail ID **- This should already be populated as *EmailRecpt*.
    -   **Subject **- Enter a title for the email receipts.
    -   **Language **- Specify the language.
    -   **Email **- Insert the following string: *&lt;pre&gt;%message%&lt;/pre&gt;.*
    -   If you want to have more than just the receipt in the message, click the **E-mail message** button to fill out the template for the body of the email messages to be sent. If you want the receipt to appear (in MPOS), insert the placeholder *%message%.*

This is the only placeholder that will be replaced when sending MPOS receipts. To get more placeholder options, you'll need to create customization on the MPOS side.

Depending on the settings that you configured, you'll need to run the respective distribution schedule jobs to sync the changes to MPOS.

-   **1010** – Customer
-   **1070** – Channel configuration
-   **1090** – Registers
-   **1110** – Global configuration

## MPOS transaction
After synchronizing the changes to the store, MPOS will prompt the user for an email address for each transaction (if enabled). If the customer already has an email address on file, that address will appear in the email address prompt. If a customer hasn't been named, or the named customer doesn’t have an email address, enter an email address and then click **Send**. When the transaction is finalized, the real-time service will send the customer an email with the receipt in the body of the message as configured above.

