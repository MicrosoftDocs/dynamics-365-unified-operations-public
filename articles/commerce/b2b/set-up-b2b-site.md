---
title: Set up a B2B e-commerce site
description: This article describes how to set up a business-to-business (B2B) e-commerce site in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14
ms.search.industry: retail
ms.search.form: RetailOperations
---

# Set up a B2B e-commerce site

[!include [banner](../../includes/banner.md)]

Business-to-business (B2B) e-commerce sites provide some key capabilities that optimize the workflow for a B2B user. This article describes how to set up a B2B e-commerce site in Microsoft Dynamics 365 Commerce. It goes through the modules and site settings that must be configured to enable B2B-specific scenarios.

## Prerequisites

- To setup a B2B e-commerce site, you must enable and configure specific features in Commerce headquarters, as described in this article.
- Core experiences, such as product discovery, product details pages, the cart, and checkout are powered by the same modules that are used for business-to-consumer (B2C) e-commerce sites. Site authors should be familiar with all the modules that Dynamics 365 Commerce supports. For more information, see [Module library overview](../starter-kit-overview.md).
- This article assumes that site authors understand the basics of Commerce site builder, templates, fragments, and pages, so that they can enable the B2B features for e-commerce sites.

## Site-level settings

You can access site-level settings in site builder, at **Site Settings \> Extensions**. The following two site-level settings apply to B2B scenarios:

- **Enable customer account payments** – This property enables users to pay for orders by using customer accounts. The available values are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**. If your B2B site supports customer accounts, you should select **Enabled for B2B customers**.
- **Enable order quantity limits** – This property lets you set limits on the number of items that can be ordered for each product or category. The available values are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**.

> [!NOTE]
> When you upgrade to the latest version of the module library, you must follow additional steps to ensure that the previously described site settings are available in your environment. For more information, see [Update the app.settings.json file](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Create business partner sign-up pages

To become a business partner, users must first submit a business partner request. A link to the business partner request page will be available on the B2B home page, so that users can initiate the process. After users submit a business partner request, they will receive confirmation that the request has been submitted. 

### Create a business partner request page

The **Partner sign up** module on a business partner request page is used to initiate user requests to become business partners. This module lets you collect the user information that is required for the sign-up process. Additionally, the **Business account address** module is used to capture the user's address.

To set up and configure the business partner request page in site builder, follow these steps.

1. Create a template that is named **Sign-up**. This template should include the following modules:

    - Partner sign up
    - Breadcrumb
    - Header
    - Footer
    - Content block
    - Text block
    - Product collection

1. Use the **Sign-up** template to create a page that is named **Business Partner Request**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the home page, and enter **Home** as the link text.
1. In the **Container** slot, add a **Partner sign up** module below the **Breadcrumb** module. In the module properties pane, under **Heading**, enter **Become a business partner**.
1. In the **Partner sign up** slot, add a **Business account address** module.
1. In the **Container** slot, add a **Text block** module below the **Partner sign up** module. Here, you can define some terms and conditions for the sign-up process.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

### Create a business partner request confirmation page

After a business partner request is submitted, a confirmation page should be shown to the user to acknowledge the submission. 

To set up and configure the request confirmation page in site builder, follow these steps.

1. Use the **Sign-up** template that you created earlier to create a page that is named **Partner Request Confirmation**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Content block** module. In the module properties pane, under **Heading**, enter **Request submitted**. In the **Rich Text** field, enter **Your request has been submitted**. Under **Links**, configure a link to the home page, and enter **Back to shopping** as the link text.
1. Add another **Container** module, and add a **Product Collection** module to it.
1. Configure the **Product Collection** module with the recommendation or category list that you want to showcase on the page.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

To add a link to the request confirmation page in site builder, follow these steps.

1. Go to the **Business Partner Request** page that you created earlier, and select **Edit**. 
1. Select the **Partner sign up** module slot. In the properties pane, under **Link to the Sign-Up Confirmation page**, configure the link to the business partner request page that you created earlier. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Add a business partner request link to the home page

After the business partner request sign-up and confirmation pages are created, you must make the sign-up page accessible through a link on the home page. You can complete this task by adding the link to any **Content block** module on the home page.

To add a business partner request link to the home page in site builder, follow these steps.

1. Go to the home page for your site, and select **Edit**.
1. Select a **Content block** module slot. In the module properties pane, under **Links**, configure a link to the business partner request page that you created earlier, and enter **Sign up to be a business partner** or similar text as the link text. Add an image as appropriate.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Account management landing page

The account management landing page includes all the account management information that is required for both B2B and B2C e-commerce sites. Only signed-in users can view this page.

To create and configure a B2B account management landing page in site builder, follow these steps.

1. Create a template that is named **Account management**. This template should include the following modules:

    - Header
    - Footer
    - Breadcrumb
    - Account welcome tile
    - Account generic tile
    - Account Address tile
    - Account wishlist tile
    - Account address tile
    - Account loyalty tile
    - Account customer balance tile
    - Account order templates tile
    - Organization users
    - Business organization list
    - Customer account balance
    - Order template lines
    - Order template list
    - Account invoice tile
    - Invoices list
    - Invoice details

1. Use the **Account management** template to create a page that is named **My Account**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**. 
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the home page, and enter **Home** as the link text.
1. In the **Container** slot, add a **Welcome tile** module. In the module properties pane, under **Heading**, enter **Welcome**.
1. In the **Main** slot, add another **Container** module (**Container 2**). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 2** slot, add an **Account generic tile** module. In the module properties pane, under **Heading**, enter **My Profile**. Under **Links**, configure a link to the **My profile** page. 
1. In the **Container 2** slot, add another **Account generic tile** module. In the module properties pane, under **Heading**, enter **Order history**. Under **Links**, configure a link to the order history page.
1. In the **Main** slot, add another **Container** module (**Container 3**). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 3** slot, add an **Account address tile** module. In the module properties pane, under **Heading**, enter **My Address**. Under **Links**, configure a link to the **My address** page. 
1. In the **Container 3** slot, add an **Account wishlist tile** module. In the module properties pane, under **Heading**, enter **My Wishlist**. Under **Links**, configure a link to the **My wishlist** page.
1. In the **Main** slot, add another **Container** module (**Container 4**). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 4** slot, add an **Organization users** module. In the module properties pane, under **Heading**, enter **Organization Users**. 
1. In the **Container 4** slot, add an **Account customer balance tile** module. In the module properties pane, under **Heading**, enter **Account credit**. 
1. In the **Main** slot, add another **Container** module (**Container 5**). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 5** module, add an **Account order templates tile** module. In the module properties pane, under **Heading**, enter **Order Templates**. 
1. In the **Container 5** module, add an **Account invoice tile** module. In the module properties pane, under **Heading**, enter **Invoices**. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

> [!NOTE] 
> Some of the sections that you added in step 13 through 18 won't appear on the "what you see is what you get" (WYSIWIG) canvas in site builder, because they require a signed-in B2B account.

## Create and configure customer balance pages and modules 

Customer accounts can be used to pay for orders. The available balance in a customer account can be viewed from a user's account management page.

### Create a customer balance page 

Before signed-in B2B users can view their customer balance, you must create a customer balance page. 

To create a customer balance page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Customer Balance**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add another **Container** module (**Container 3**). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text.
1. In the **Container** slot, add a **Customer Account Balance** module. In the module properties pane, under **Heading**, enter **Account Balance**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to the account management landing page (**My Account**) that you created earlier.
1. In the properties pane for the **Account customer balance tile** module, add a link to the customer balance page. 
1. Save and publish the page.

The customer balance page has now been created, and users can access it from the account management landing page.

### Configure a checkout page so that the customer balance can be used as a form of payment

The **Customer Account Payment** module is required to enable the customer balance to be used as a form of payment. This module should be added to the checkout page as a form of payment. For information about how to configure a checkout page and the modules that are required for checkout, including all payment details, see [Checkout module](../add-checkout-module.md).

After you've configured a checkout page, you must add the **Customer Account Payment** module to the payment section, and then save and publish the page. B2B users will then be able sign in to the e-commerce site and apply their available customer balance to orders during checkout.

In addition, at **Site Builder \> Extensions**, you must make sure that the **Enable customer account payments** property is set to **Enabled for B2B customers**.

## Create order template pages

Two order template pages can be set up for a B2B e-commerce site: an order templates list page and an order template lines page.

An order templates list page shows a list of all order templates that are available. It's set up by using the **Order templates list** module. The order templates list page lets you create or delete a template, and add the items in a template to the cart.

An order template lines page shows the details of the order template that is selected on an order templates list page. It's set up by using the **Order templates lines** module. When a user selects the name of a template on an order templates list page, the order template lines page appears and shows the details of the template. The user can then view and edit the items in the template.

### Create an order templates list page

To create an order templates list page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Order templates**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text.
1. In the **Container** slot, add an **Order templates list** module.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to the account management landing page (**My Account**) that you created earlier.
1. In the properties pane for the **Account order templates tile** module, under **Links**, configure a link to the order templates list page that you just created.
1. Save and publish the page.

The order templates list page has now been created, and users can access it from the account management landing page.

### Create an order template lines page

To create an order template lines page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Order template lines**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text.
1. In the **Container** slot, add an **Order template lines** module.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

## Onboard business partner users

The organization users page lets the administrator of a business partner organization onboard additional users from that organization to the B2B e-commerce site. It's set up by using the **Business organization list** module. From the organization users page, an administrator can add or remove users, define account balances, and request statements for a user.

To create an organization users page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Organization Users**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text.
1. In the **Container** slot, add a **Business organization list** module. In the module properties pane, under **Heading**, enter **Organization Users**.
1. In the **Business organization list** module properties pane, enable the **Table Sort** and **Table pagination** properties. Set the pagination count to **5**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to the account management landing page (**My Account**) that you created earlier.
1. In the properties pane for the **Organization users tile** module, under **Links**, configure a link to the organization users page that you just created. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Create invoice pages

An invoices list page shows a list of all available invoices. It's set up by using the **InvoicesList** module. From the invoice list page, users can pay off or request invoices. 

An invoice details page shows the details of the invoice that is selected on an invoices list page. It's set up by using the **Invoice details** module. When a user selects an invoice ID on an invoice list page, the invoice details page appears and shows the details of the invoice.

### Create an invoices list page

To create an invoices list page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Invoices List**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text.
1. In the **Container** slot, add an **InvoicesList** module. In the module properties pane, under **Heading**, enter **Invoices**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to the account management landing page (**My Account**) that you created earlier.
1. In the properties pane for the **Account invoices tile** module, under **Links**, configure a link to the invoices list page that you just created. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Create an invoice details page

To create an invoice details page in site builder, follow these steps.

1. Use the **Account management** template that you created earlier to create a page that is named **Invoice Details**.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, under **Links**, configure a link to the account management landing page, and enter **My Account** as the link text. Then configure a link to the invoices list page, and enter **Invoice Lists** as the link text.
1. In the **Container** slot, add an **Invoice details** module.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

## Add a quick add module to the cart page

The quick add module provides a way to quickly add multiple items to the cart by using item IDs (also known as stock keeping unit \[SKU\] IDs). The quick add module is added to a site's cart page.

To add a quick add module to a cart page in Commerce site builder, follow these steps.

1. Go to **Templates**, and select your site's cart page template.
1. Select **Edit**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Quick add** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select your site's cart page.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the  properties pane for the **Container** module, under **Width**, select **Fill Container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Quick add** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

> [!NOTE] 
> The quick add module is available as of the Commerce version 10.0.17 release. If you're updating from an older version of Commerce, you must manually update the appsettings.json file. For instructions, see [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Add a bulk purchase module to a product details page

The bulk purchase module on a product details page (PDP) provides a matrix-based experience that lets a buyer quickly add multiple variants of a product to the cart. When a site user must order multiple variants of the same product, this experience eliminates the need to select the combination of product dimensions, define the quantity, add the variant to the cart, and then repeat the process for other combinations of product dimensions.

To add the bulk purchase module to a PDP in Commerce site builder, follow these steps.

1. Go to **Templates**, and select your site's PDP template.
1. Select **Edit**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Bulk purchase** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select your site's PDP.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the properties pane for the **Container** module, under **Width**, select **Fill Container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Bulk purchase** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

> [!NOTE] 
> The bulk purchase module is available as of the Commerce version 10.0.24 release. If you're updating from an older version of Commerce, you must manually update the appsettings.json file. For instructions, see [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Additional resources

[Module library overview](../starter-kit-overview.md)

[SDK and module library updates](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file)

[Authoring page overview](../authoring-home-overview.md)

[Templates and layouts overview](../templates-layouts-overview.md)

[Work with fragments](../work-with-fragments.md)

[Add a new site page](../add-new-page.md)

[Checkout module](../add-checkout-module.md)

[Content block module](../add-hero-module.md)

[Product collection module](../product-collection-module-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
