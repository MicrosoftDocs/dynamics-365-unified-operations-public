---
# required metadata

title: Configure optional features for a Dynamics 365 Commerce preview environment
description: This topic explains how to configure optional features for a Microsoft Dynamics 365 Commerce preview environment.
author: psimolin
manager: annbe
ms.date: 12/10/2019
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
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Configure optional features for a Dynamics 365 Commerce preview environment


[!include [banner](includes/banner.md)]

This topic explains how to configure optional features for a Microsoft Dynamics 365 Commerce preview environment.

## Prerequisites

If you want to evaluate the transactional email features, the following prerequisites must be met:

- You have an available email server (Simple Mail Transfer Protocol \[SMTP\] server) that can be used from the Microsoft Azure subscription where you provisioned the preview environment.
- You have the server's fully qualified domain name (FQDN)/IP address, SMTP port number, and authentication details available.

If you want to evaluate Digital Asset Management features by ingesting new omni-channel images, you must have the name of your content management system (CMS) tenant available. Instructions for finding this name are provided later in this topic. >>>(Q: where are the instructions?)

## Configure the image back end

### Find your media base URL

> [!NOTE]
> Before you can complete this procedure, you must complete the steps in [Set up your site in Commerce](cpe-post-provisioning.md#set-up-your-site-in-commerce).

1. Sign in to the Commerce site management tool by using the URL you made a note of when you initialized e-Commerce during provisioning (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Open the **Fabrikam** site.
1. On the menu on the left, select **Assets**.
1. Select any single image asset.
1. In the property inspector on the right, find the **Public URL** property. The value is a URL. Here is an example:

    `https://images-us-sb.cms.commerce.dynamics.com/cms/api/fabrikam/imageFileData/MA1nQC`.

1. Replace the last identifier in the URL (**MA1nQC** in the preceding example) with the string **search?fileName=**. Here is what the example URL looks like after this change is made:

    `https://images-us-sb.cms.commerce.dynamics.com/cms/api/fabrikam/imageFileData/search?fileName=`

    This URL is your media base URL. Make a note of it.

### Update the media base URL

1. Sign in to Dynamics 365 Retail.
1. Use the menu on the left to go to **Modules \> Retail \> Channel setup \> Channel profiles**.
1. Select **Edit**.
1. Under **Profile properties**, replace the value for the **Media Server Base URL** property with the media base URL that you created earlier.
1. In the list on the left, under the **Default** channel, select the other channel.
1. Under **Profile properties**, select **Add**.
1. For the property that was added, select **Media Server Base URL** as the property key. As the property value, enter the media base URL that you created earlier.
1. Select **Save**.

## Configure the email server

> [!NOTE]
> The SMTP server or email service that you enter here must be accessible from the Azure subscription that you're using for the environment.

1. Sign in to Retail.
1. Use the menu on the left to go to **Modules \> System administration \> Setup \> Email \> Email parameters**.
1. On the **SMTP settings** tab, in the **Outgoing mail server** field, enter the FQDN or IP address of your SMTP server or email service.
1. In the **SMTP port number** field, enter the port number. (If you aren't using Secure Sockets Layer \[SSL\], the default port number is **25**.)
1. If authentication is required, enter values in the **User name** and **Password** fields.
1. Select **Save**.
1. Select **Refresh**.
1. On the **Test email** tab, in the **Email provider** field, select **SMTP**.
1. In the **Send to** field, enter the email address that the test email should be delivered to.
1. Select **Send test email**.

## Configure email templates

For each transactional event that you want to send emails for, you must update the email template with a valid sender email address.

1. Sign in to Retail.
1. Use the menu on the left to go to **Modules \> Organization administration \> Setup \> Organization email templates**.
1. Select **Show list**.
1. For each template in the list, follow these steps:

    1. In the **Sender email** field, enter the sender email address.
    1. Optional: In the **Sender name** field, enter the name that should be used as the sender name.

1. Select **Save**.

## Customize email templates

You might want to customize the email templates so that they use different images. Or you might want to update the links in the templates so that they go to your preview environment. This procedure explains how to download the default templates, customize them, and update the templates in the system.

1. In a web browser, download the [Microsoft Dynamics 365 Commerce Preview default email templates zip file](https://download.microsoft.com/download/d/7/b/d7b6c4d4-fe09-4922-9551-46bbb29d202d/Commerce.Preview.Default.Email.Templates.zip) to your local computer. This file contains the following HTML documents:

    - Order confirmation template
    - Issue gift card template
    - New order template
    - Pack order template
    - Pick order template

1. Customize the templates by using a text or HTML editor. See the list of [supported tokens](#supported-tokens-in-the-email-template) later in this topic.
1. Sign in to Retail.
1. Use the menu on the left to go to **Modules \> Organization administration \> Setup \> Organization email templates**.
1. Expand the list on the left to see all the templates.
1. For each template that you want to customize, follow these steps:

    1. Select the template in the list.
    1. Under **Email message content**, select the appropriate language version in the list. (The default language is **en-us**.)
    1. Under **Email message content**, select **Edit**. The **Upload email template** pane appears.
    1. Select **Browse**, and find the HTML file that has the customized content.
    1. Select **Upload**. The template is uploaded into the system, and a preview is shown.
    1. Select **OK**.
    1. Optional: Customize the **Subject** property of the template.
    1. Select **Save**.

### Supported tokens in the email template

When the email is rendered, these tokens are replaced with actual values that apply to the customer and the customer's order.

#### Sales order

The following tokens apply to the overall sales order.

| Name of the token | Token |
|-------------------|-------|
| Order number      | %salesid% |
| Customer's name   | %customername% |
| Delivery address  | %deliveryaddress% |
| Billing address   | %customeraddress% |
| Order date        | %shipdate% |
| Delivery mode     | %modeofdelivery% |
| Discount          | %discount% |
| Sales tax         | %tax% |
| Order total       | %total% |

#### Sales line

The following tokens are replaced with values for each product in the order.

> [!NOTE]
> Put the **Product list - start** token at the beginning of the HTML block that is repeated for every product, and put the **Product list - end** token at the end of the block.

| Name of the token      | Token |
|------------------------|-------|
| Product list - start   | \<!--%tablebegin.salesline% --\> |
| Product list - end     | \<!--%tableend.salesline%--\> |
| Product name           | %lineproductname% |
| Description            | %lineproductdescription% |
| Quantity               | %linequantity% |
| Line unit price        | %lineprice% (verify) |
| line item total        | %linenetamount% |
| line discount          | %linediscount% |
| Ship date              | %lineshipdate% |
| Procurement method     | %linedeliverymode% |
| delivery address       | %linedeliveryaddress% |
| Sales unit of the line | %lineunit% |

## Additional resources

[Dynamics 365 Commerce preview environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce preview environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce preview environment](cpe-post-provisioning.md)

[Dynamics 365 Commerce preview environment FAQ](cpe-faq.md)

[Microsoft Lifecycle Services (LCS)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](https://docs.microsoft.com/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)
