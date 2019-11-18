---
# required metadata

title: Configure Commerce preview environment optional features
description: This topic describes how to configure optional features for a Microsoft Dynamics 365 Commerce preview environment.
author: psimolin
manager: annbe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Configure Commerce preview environment optional features

This topic describes how to configure optional features for a Microsoft Dynamics 365 Commerce preview environment.

## Prerequisites for optional features
If you want to evaluate the transactional email features, the following prerequisites must be met:
* You have an email server available (SMTP server), which can be used from the Azure subscription where you provision the preview environment.
* You have the server's FQDN/IP, SMTP port number, and authentication details available.

If you want to evaluate Digital Asset Management features, specifically ingest new omni-channel images, the following pre-requisites must be met:
* You need to have your **CMS tenant name** available. Instructions for finding this name are below.
### Configure image backend (optional)
##### Finding your Media base URL
*Note: Before you can complete this step, you must complete **Site Setup**.*
1. Log in to the site management tool using the URL you noted earlier.
1. Open the **Fabrikam** site.
1. Choose **Assets** from the menu on the left.
1. Select any single image asset.
1. Locate **Public URL** from the property inspector on the right. It has an URL in it.
	* Example URL: https://images-us-sb.cms.commerce.dynamics.com/cms/api/fabrikam/imageFileData/MA1nQC
1. Replace the last identifier in the URL (MA1nQC in the example URL above) with the following string: **search?fileName=**
	* Example URL after replacement: https://images-us-sb.cms.commerce.dynamics.com/cms/api/fabrikam/imageFileData/search?fileName=
	* This is your **Media base URL** - make note of it.
##### Updating the media base URL
1. Log in to the environment (HQ).
1. Using the menu on the left, go to **Modules > Retail > Channel setup > Channel profiles**.
1. Click **Edit**.
1. From the **Profile properties**, replace the property value for **Media Server Base URL** with the **Media base URL** you created earlier.
1. Select the other channel from the list on the left, under **Default** channel.
1. Under **Profile properties**, click **+ Add**.
1. For the property that was added, choose **Media Server Base URL** as property key and for property value, enter the **Media base URL** you created earlier.
1. Click **Save**.

### Configure email server (optional)
Please note that the SMTP server or email service you enter here must be accessible from within the Azure subscription you are using for the environment.
1. Log in to the environment (HQ).
1. Using the menu on the left, go to **Modules > System administration > Setup > Email > Email parameters**.
1. Click the **SMTP settings** tab.
1. In the **Outgoing mail server field**, type the FQDN or IP address of your SMTP server or email service.
1. In the **SMTP port number** field, enter the port number (default is the 25 when not using SSL).
1. In the **User name** field, type a value (if authentication is required).
1. In the **Password** field, type a value (if authentication is required).
1. Click **Save**.
1. Click **Refresh**.
1. Click the **Test email** tab.
1. In the Email provider field, choose **SMTP**.
1. In the **Send to** field, enter the email address where you want the test email to be delivered.
1. Click **Send test email**.
### Configure email templates (optional)
The email template for each transactional event that you wish to send emails for needs to be updated with a valid sender email address.
1. Using the menu on the left, go to **Modules > Organization administration > Setup > Organization email templates**.
1. Click **Show list**.
1. For each of the templates in the list:
	1. In the **Sender email** field, type the sender email address for this email template.
	1. (Optional) In the **Sender name** field, type a name that will be used as sender for this email template.
1. Click **Save**.
### Customizing email templates (optional)
You might want to customize the email templates to use different images or update the links in the template to link back to your Preview environment. The steps below explain how to download the default templates, customize them and update the templates in the system.
1. Using a browser, download [the Microsoft Dynamics 365 Commerce Preview default email templates .zip file](https://download.microsoft.com/download/d/7/b/d7b6c4d4-fe09-4922-9551-46bbb29d202d/Commerce.Preview.Default.Email.Templates.zip) containing the following HTML documents to your local computer.
	1. Order confirmation template
	1. Issue gift card template
	1. New order template
	1. Pack order template
	1. Pick order template
1. Customize the templates using a text or HTML editor. Please see a list of supported tokens below.
1. Log in to the environment (HQ).
1. Using the menu on the left, go to **Modules > Organization administration > Setup > Organization email templates**.
1. Expand the list on the left to see all the templates.
1. For each of the templates you wish to customize, perform the following steps:
	1. Select the template from the list.
	1. Under **Email message content**, select the appropriate language version from the list (default **en-us**).
	1. Under **Email message content**, click **Edit**, you should see **Upload email template** pane opening.
	1. Click **Browse** and locate the HTML file with the customized content.
	1. Click **Upload**, your template is uploaded to the system and a preview is shown.
	1. Click **OK**.
	1. (Optional) Customize the **Subject** property of the template.
	1. Click **Save**.

#### Supported tokens in the email template
These tokens will be replaced at email rendering time with the actual values that apply to the customer and their order.

**Sales order** - The following tokens apply to the overall sales order.

|Name of the token|Token|
|---|---|
|Order number|%salesid%|
|Customer's name|%customername%|
|Delivery address|%deliveryaddress%|
|Billing address|%customeraddress%|
|Order date|%shipdate%|
|Delivery mode|%modeofdelivery%|
|Discount|%discount%|
|Sales tax|%tax%|
|Order total|%total%|

**Sales line** - The following tokens are populated for each product in the order.

> [!NOTE]
> Place the **Product list - start** and **Product list - end** tokens at the beginning and end of the HTML block that repeats for every product.*

|Name of the token|Token|
|---|---|
|Product list - start|\<!--%tablebegin.salesline% -->|
|Product list - end|\<!--%tableend.salesline%-->|
|Product name|%lineproductname%|
|Description|%lineproductdescription%|
|Quantity|%linequantity%|
|Line unit price|%lineprice% (verify)|
|line item total|%linenetamount%|
|line discount|%linediscount%|
|Ship date|%lineshipdate%|
|Procurement method|%linedeliverymode%|
|delivery address|%linedeliveryaddress%|
|Sales unit of the line|%lineunit%|

## Additional resources

[Commerce preview environment overview](cpe-overview.md)
[Provision a Commerce preview environment](provisioning-guide.md)
[Configure a Commerce preview environment](cpe-post-provisioning.md)
[Commerce preview environment FAQ](cpe-faq.md)
