---
# required metadata

title: Set up a B2B e-commerce site
description: This topic describes how to set up a B2B e-commerce site in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Set up a B2B e-commerce site

[!include [banner](../../includes/banner.md)]

This topic describes how to set up a B2B e-commerce site in Dynamics 365 Commerce.

Business-to-business (B2B) e-commerce sites provide some key capabilities that optimize the workflow for a B2B user. This topic walks through the modules and site settings that need to be configured to enable B2B-specific scenarios.

## Prerequisites

- To setup a B2B e-commerce site, specific features must be enabled and configured in Commerce headquarters as covered in this topic.
- Core experiences such as product discovery, product details page, cart, and checkout are powered by the same modules that are used for business-to-consumer (B2C) e-commerce sites. Site authors should be familiar with all of the modules supported by Dynamics 365 Commerce. For more information, see [Module library overview](../starter-kit-overview.md).
- This topic assumes that site authors understand the basics of Commerce site builder, templates, fragments, and pages to be able to enable the B2B features for e-commerce sites.

## Site-level settings

Site-level settings can be accessed in site builder under **Site Settings \> Extensions**. The following two site settings apply to B2B scenarios.

- **Enable customer account payments** - This property allows users to pay for orders using customer accounts. Available values for this property are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**. If your B2B site supports customer accounts, you should select **Enabled for B2C customers**.
- **Enable order quantity limits** – This property allows you to set limits on the number of items that can be ordered for each product or category. Available values for this property are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**.

> [!NOTE]
> When upgrading to latest version of the module library, you need to follow additional steps to ensure that the site settings described above are available in your environment. For more information, see [Update the app.settings.json file](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Create business partner sign-up pages

To become a business partner, users must first submit a business partner request. The link to the business partner request page will be available on the B2B home page for users to initiate the process. After submitting a business partner request, users will see a confirmation message that the request has been submitted. 

### Create a business partner request page

The request to become a business partner is initiated using the **Partner sign up** module on a business partner request page. This module allows you to collect the user information necessary for the sign-up process. Also, the **Business account address** module to capture the business user's address.

To set up and configure the business partner request page in site builder, follow these steps.

1. Create a template that includes partner sign-up, breadcrumb, header, footer, content block, text block, and product collection modules. Enter "Sign-up" as the name for this template.
1. Create a page named "Business Partner Request" using the **Sign-up** template you created.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the home page with link text "Home"..
1. In the **Container** slot, add the **Partner Sign-up** module below the **Breadcrumb** module. In the module properties pane under **Heading**, enter "Become a business partner".
1. In the **Partner sign up** slot, add a **Business account address** module.
1. In the **Container** slot, add a **Text block** module below the **Partner sign up** module. Here you can define some terms and conditions for the sign-up process.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

### Create a business partner request confirmation page

Once a business partner request is submitted, a confirmation page should be displayed to the user acknowledging their submission. 

To set up and configure the request confirmation page in site builder, follow these steps.

1. Create a page named "Partner Request Confirmation" using the "Sign-up" template.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, add a **Content block** module. In the properties panel under **Heading**, enter "Request submitted." In the **Rich Text** box, add the text "Your request has been submitted". Under **Links**, enter a link to the home page with link text "Back to shopping".
1. Add another container module and then add a **Product Collection** module to it. Configure this module with a recommendation or category list that you want to showcase on this page.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

To add a link to the request confirmation page in site builder, follow these steps.

1. Go to the "Business Partner Request" page you created earlier and select **Edit**. 
1. Select the **Partner Sign up** module slot. In the properties pane under **Link to the Sign-Up Confirmation page**, configure the link to the business partner request page you created earlier. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Add business partner request link to home page

Once the business partner request sign-up and confirmation pages are created, you need to make the sign-up page accessible with a link on the home page. You can do this by adding the link to any content block module on the home page.

To add a business partner request link to the home page in site builder, follow these steps.

1. Go to the home page for your site and select **Edit**.
1. Select a content block module slot. In the module properties pane under **Links**, configure a link to the business partner request page you created earlier with the link text "Sign up to be a business partner" or something similar. Add an image as appropriate.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Account management landing page

The account management landing page includes all the account management information needed for both B2B and B2C e-commerce sites. Only signed-in users can view this page.

To create and configure a B2B account management landing page in site builder, follow these steps.

1. Create a template named "Account management". This template should include the following modules:
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
1. Create a page named "My Account" that uses the "Account management" template.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**. 
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the home page with link text "Home."
1. In the **Container** slot, add a **Welcome tile** module. In the module properties pane under **Heading**, enter "Welcome."
1. In the **Main** slot, add another **Container** module ("Container 2"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 2** slot, add an **Account generic tile** module. In the module properties pane under **Heading**, enter "My Profile." Under **Links**, configure a link to the "My profile" page. 
1. In the **Container 2** slot, add another **Account generic tile** module. In the module properties pane under **Heading**, enter "Order history." Under **Links**, configure a link to the order history page.
1. In the **Main** slot, add another **Container** module ("Container 3"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 3** slot, add an **Account address tile** module. In the module properties pane under **Heading**, enter "My Address." Under **Links**, configure a link to the "My address" page. 
1. In the **Container 3** slot, add an **Account wishlist tile** module. In the module properties pane under **Heading**, enter "My Wishlist." Under **Links**, configure a link to the "My wishlist" page.
1. In the **Main** slot, add another **Container** module ("Container 4"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 4** slot, add an **Organization users** module. In the module properties pane under **Heading**, enter "Organization Users." 
1. In the **Container 4** slot, add an **Account customer balance tile** module. In the module properties pane under **Heading**, enter "Account credit." 
1. In the **Main** slot, add another **Container** module ("Container 5"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 5** module, add an **Account order templates tile** module. In the module properties pane under **Heading**, enter "Order Templates". 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

> [!NOTE] 
> Some of the sections added in step 13-18 will not appear in the site builder WYSIWIG canvas as they require a signed-in B2B account.

## Create and configure customer balance pages and modules 

Customer accounts can be used to pay for an order. The available balance in a customer account can be viewed from a user's account management page.

### Create a customer balance page 

To view customer balance for a signed-in B2B user, you first need to create a customer balance page. 

To create a customer balance page in site builder, follow these steps.

1. Create a page **Customer Balance** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add another **Container** module ("Container 3"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the account management landing page with link text "My Account."
1. In the **Container** slot, add a **Customer Account Balance module**. In the module properties pane under **Heading**, enter "Account Balance."
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to account management landing page created earlier. On the **Account customer balance tile** module properties pane, aadd a link to the customer balance page. 
Save and Publish. Now the page is created and can be accessed from the Account Management home page by a user.

### Configure checkout page to use customer balance as a payment

To use customer balance as a form of payment, the **Customer Account Payment** module is required. This module should be added to the Checkout page as a form of payment. For details on how to configure a checkout page and the modules that are needed for checkout including all payment details, see [Checkout module](../add-checkout-module.md).

Once you have a checkout page configured, you need to add **Customer Account Payment** to the payment section of this page, and then save and publish the page. A B2B user will then be able sign in to the e-commerce site and apply their available customer balance amount to their order during checkout.

In addition, under **Site Builder \> Extensions** ensure the Customer Account Payment property is **Enabled for B2B customers.**

## Create order templates pages

There are two order templates pages that can be set up on a B2B e-commerce site. 

An order templates list page displays a list of all order templates available, and is set up using the **Order templates list** module. It allows you to create or delete a template and add items in a template to the cart.

An order templates lines page displays the details of each order template that is displayed on the order templates page, and is set up using the **Order templates lines** module. When a user selects the name of the template on the order template list page, the order templates lines page displays the details of that template. The user can then view and edit the items in the template.

### Create an order templates list page

To create an order templates list page in site builder, follow these steps.

1. Create a page **Order templates** using the **Account Management** template created earlier.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the account management landing page with link text "My Account."
1. In the **Container** slot, add an **Order templates list module**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that we created earlier.
1. Navigate to the **Account order templates tile** module property panel. Here add a Link to the Order templates List page that we just created in step \#8. Save and Publish. Now the Order templates list page is created and can be accessed from the account management landing page by a user.

### Create an order templates lines page

To create an order templates lines page in site builder, follow these steps.

1. Create a page **Order template lines** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure links to the account management landing page with link text "My Account."
1. In the **Container** slot, add an **Order template lines module**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

## Onboard business partner users

The administrator of a business partner organization can onboard additional users from the organization to the B2B e-commerce website from an organization users page that uses the **Business organization list** module. From the organization users page, an administrator can add or remove users, define account balances, and request statements for a user.

To create an organization users page in site builder, follow these steps.

1. Create an **Organization Users** page using the **Account Management** template created earlier.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the account management landing page with link text "My Account."
1. In the **Container** slot, add a **Business organization list** module. In the module properties pane under **Heading**, enter "Organization Users."
1. In the **Business organization list** module property pane, enable the **Table Sort** and **Table pagination** properties. Set the pagination count to "5."
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that was created earlier.
1. On the **Organization users tile** module properties pane, add a link to the organization users page. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Create invoice pages

An invoice list page displays a list of all available invoices and allows users to pay off or request invoices. The invoice list page is set up using the **InvoicesList** module.

An invoice details page displays the details of each invoice displayed on an invoices list page. When users selects an invoice ID on an invoice list page, they are navigated to an invoice details page displaying the details of that invoice. The invoice details page is set up using the **Invoice details** module.

### Create an invoice list page

To create an invoice list page in site builder, follow these steps.

1. Create a page named **Invoices List** using the **Account Management** template created earlier.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure a link to the account management landing page with link text "My Account."
1. In the **Container** slot, add an **InvoicesList** module. In the module properties pane under **Heading**, enter "Invoices."
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to the account management landing page created earlier. On the **Account invoices tile** module properties pane, add a link to the invoices list page. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Create an invoice details page

To create an invoice details page in site builder, follow these steps.

1. Create a page **Invoice Details** using the **Account Management** template created earlier.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane under **Links**, configure links to the account management landing page with link text "My Account," and to the invoice lists page with link text "Invoice Lists."
1. In the **Container** slot, add an **Invoice details module.**
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Authoring page overview](../authoring-home-overview.md)

[Templates and layouts overview](../templates-layouts-overview.md)

[Work with fragments](../work-with-fragments.md)

[Add a new site page](../add-new-page.md)

[Checkout module](../add-checkout-module.md)

[Content block module](../add-hero-module.md)

[Product Collection](../product-collection-module-overview.md)


