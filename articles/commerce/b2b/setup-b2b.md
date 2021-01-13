---
# required metadata

title: Set up a B2B e-commerce site
description: This topic describes how to set up a B2B e-commerce site in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
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

- To setup a B2B e-commerce site, the features must be enabled and configured in Commerce headquarters as defined in the feature documentation.
- Core experiences such as product discovery, product details page, cart, and checkout are powered by the same modules that are used for a business-to-consumer (B2C) site. A site author should be familiar with all of the modules supported by Dynamics 365 Commerce. For more information, see [Module library overview](../starter-kit-overview.md).
- This topic assumes that site authors understand the basics of Commerce site builder, templates, fragments, and pages to be able to enable the B2B features for e-commerce sites.

## Site settings

Site-level settings can be accessed in site builder under **Site Settings \> Extensions**. For B2B scenarios, the following two site settings have been added.

- **Enable customer account payments** - The **Enable customer account payments** property allows users to pay for orders using customer accounts. Available values for this property are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**. If your B2B site supports customer accounts, you should select **Enabled for B2C customers**.
- **Enable order quantity limits** – The **Enable order quantity limits** property allows you to set limits on the number of items that can be ordered for each product or category. Available values for this property are **Enabled for B2B customers**, **Enabled for B2C customers**, **Enabled for all customers**, and **Disabled for all customers**.

> [!NOTE]
> When upgrading to latest version of the module library, you need to follow additional steps to ensure that the site settings described above are available in your environment. For more information, see [Update the app.settings.json file](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

## Create business partner sign-up pages

To become a business partner, users must first submit a business partner request. To sign up for a business partner account, users must set up a partner account. After submitting the business partner request, users will see a confirmation message that the request has been submitted. In addition, the link to the business partner request will be available on the B2B home page for users to initiate the process.

### Create a business partner request page

The request to become a business partner is initiated using the **Partner sign up** module. This module allows you to collect the user information necessary for the sign-up process. In addition, we also use the **Business account address** module to capture the business user's address.

To set up and configure the business partner sign-up page in Commerce site builder, follow these steps.

1. Create a template that includes partner sign-up, breadcrumb, header, footer, content block, text block, and product collection modules. Enter "Sign-up" as the name for this template.
1. Create a page named "Business Partner Request" using the **Sign-up** template you created.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. Configure the module with breadcrumb links, for example **Home \> Become a business partner**.
1. In the **Container** slot, add the **Partner Sign-up** module below the **Breadcrumb** module. In the module properties pane under **Heading**, enter "Become a business partner".
1. In the **Partner sign up** slot, add a **Business account address** module.
1. In the **Container** slot, add a **Text block** module below the **Partner sign up** module. Here you can define some terms and conditions for the sign-up process.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

<!--Below is an image showing the site builder page configuration and the page hosting these modules.-->

### Create a business partner request confirmation page

Once a business partner request is submitted, a confirmation page should be displayed to the user acknowledging their submission. <!-- To do this we will create a confirmation page and link the Partner request page to this confirmation page.-->

To set up and configure the request confirmation page in Commerce site builder, follow these steps.

1. Create a page named "Partner Request Confirmation" using the "Sign-up" template.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Content block** module. In the properties panel under **Heading**, enter "Request submitted." In the **Rich Text** box, add the paragraph "Your request has been submitted". Under **Links**, enter a link to the home page withe link text "Back to shopping".
1. Add another container module and then add a **Product Collection** module to it. Configure this module with a recommendation or category list that you want to showcase on this page.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

To add a link to the request confirmation page in Commerce site builder, follow these steps.

1. Go to the "Business Partner Request" page you created earlier and select **Edit**. 
1. Select the **Partner Sign up** module slot. In the properties pane under **Link to the Sign-Up Confirmation page**, configure the link to the business partner request page you created earlier. 
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

### Add business partner request link to home page

Once the business partner request sign-up and confirmation pages are created, you need to make the sign-up page accessible with a link on the home page. This can be achieved by adding the link to any content block module on the home page.

To add a business partner request link to the home page in site builder, follow these steps.

1. Go to the home page for your site and select **Edit**.
1. Select a content block module slot. In the module properties pane under **Links**, configure a link to the business partner request page you created earlier with the link text "Sign up to be a business partner" or something similar. Add an image as appropriate.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Account management landing page

The account management landing page includes all the account management information needed for both B2B and B2C. To view this page, a user needs to be signed-in.

<!-- In this section, we will define the modules that we must configure on the Account Management home page. -->

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
1. Create a page named "My Account" using the "Account management" template.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. In the module properties pane, set the **Width** value to **Fill Container**. 
1. In the **Container** slot, add a **Breadcrumb** module. In the module properties pane, configure the breadcrumb link to the home page with link text "Home". 
1. In the **Container** slot, add a **Welcome tile** module. In the module properties pane under **Heading**, enter "Welcome."
1. In the **Main** slot, add another **Container** module ("Container 2"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 2** slot, add an **Account generic tile** module. In the module properties pane under **Heading**, enter "My Profile." Under **Links**, configure a link to the "My profile" page. 
1. In the **Container 2** slot, add another **Account generic tile** module. In the module properties pane under **Heading**, enter "Order history." Under **Links**, configure a link to the order history page.
1. In the **Main** slot, add another **Container** module ("Container 3"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 3** slot, add an **Account address tile** module. In the module properties pane under **Heading**, enter "My Address." Under **Links**, configure a link to the "My address" page. 
1. In the **Container 3** slot, add an **Account wishlist tile** module. In the module properties pane under **Heading**, enter "My Wishlist." Under **Links**, configure a link to the "My wishlist" page.
1. In the **Main** slot, add another **Container** module ("Container 4"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 4** slot, add an **Organization users** module. In the module properties pane under **Heading**, enter "Organization Users." <!--We will provide the link later once the respective page is created in Section of this document. -->
1. In the **Container 4** slot, add an **Account customer balance tile** module. In the module properties pane under **Heading**, enter "Account credit." <!--We will provide the link later, once the respective page is created in Section of this document.-->
1. In the **Main** slot, add another **Container** module ("Container 5"). In the module properties pane, set the **Width** value to **Fill Container**. Set the **Children Shown** value to **Two**. 
1. In the **Container 5** module, add an **Account order templates tile** module. In the module properties pane under **Heading**, enter "Order Templates". <!--We will provide the link later once the respective page is created in Section of this document.-->
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

> [!NOTE] 
> Some of the sections added in step 13-18 will not appear in the site builder WYSIWIG canvas as they require a signed-in B2B account.

At this point the Account management landing page is configured with all the tiles needed to display B2B information.

## Create and configure customer balance pages and modules 

Customer accounts can be used as a payment for an order. The available balance in a customer account can be viewed from a user's account management page.

### Create a customer balance page 

To view customer balance for a signed-in B2B user, you first need to create a customer balance page. 

To create a customer balance page in site builder, follow these steps.

1. Create a page **Customer Balance** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the Main slot, add a Container. Set Width to Fill Container.
1. In the **Container** slot, add a **Breadcrumb** module. >>>with links to My Account/Customer balance
1. In the **Container** slot, add a **Customer Account Balance module**. >>Set Heading as "Account Balance"
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that we created earlier.
1. Navigate to the **Account customer balance tile** module property panel. Here add a Link to the **Customer Balance** page that we just created. Save and Publish. Now the page is created and can be accessed from the Account Management home page by a user.

<!--Below image shows the site builder page configuration and the Customer account credit page on the e-commerce site.-->

### Use customer balance as a payment

To use customer balance as a form of payment, the **Customer Account Payment** module is required. This module should be added to the Checkout page as a form of payment. For details on how to configure a Checkout page and the modules that are needed for checkout including all payment details, see [Checkout module](../add-checkout-module.md).

Once you have a Checkout page configured, you need to add **Customer Account Payment** to the payment section of this page. Then save and publish the page. A B2B user will now be able login to the ecommerce site and use their available customer balance amount to their order during checkout.

In addition, under **Site Builder \> Extensions** ensure the Customer Account Payment property is **Enabled for B2B customers.**

<!--Below is an example showing the checkout page configuration in Site builder and the checkout page on the e-commerce site using **Customer Account Payment** module.-->

## Create order templates pages

In this section, we are going to discuss how the Order templates can be set up on the B2B e-commerce site. Order template shows one or more templates created by a B2B user and the products included in each template. These pages can be setup using **Order templates list** and **Order templates lines** module.

### Create an order templates list page

This page shows the list of all order templates available. It allows you to create/delete a template and add items in a template to shopping bag.

To create an order templates list page in site builder, follow these steps.

1. Create a page **Order templates** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. >> with links to My Account/Order templates where My Account navigates back to the account management home page.
1. In the **Container** slot, add an **Order templates list module**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that we created earlier.
1. Navigate to the **Account order templates tile** module property panel. Here add a Link to the Order templates List page that we just created in step \#8. Save and Publish. Now the Order templates list page is created and can be accessed from the Account Management home page by a user.

<!--Below is an example of the Order templates page on e-commerce site and the page configuration in site builder.-->

### Create an order templates lines page

This page shows the details of each order template that is displayed in the Order templates page. When a user selects the name of the template on the order template page, it navigates to the details of each template. Here the user can view the items in the template and edit them. The steps for configuring this page in site builder are listed
below:

To create an order templates lines page in site builder, follow these steps.

1. Create a page **Order template lines** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. >> with links to My Account/Order templates/ Order template lines. My Account navigates back to the account management home page. Order template navigates back to **Order templates** page
1. In the **Container** slot, add an **Order template lines module**.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

<!--Below is an example of the Order template lines page on e-commerce site and the page configuration in site builder.-->

## Onboard business partner users

The Admin user of the business partner organization can on-board additional users from the organization to the B2B e-commerce website by using **Business** **Organization list** module. From this page an admin can add/remove users, define account balance, request statements etc for a user.

On e-commerce, we need to first configure a page with **Business** **Organization list** module and then link this page to Account Management home page. A user can then sign into the B2B e-commerce website. Navigate to My Account &gt; Organization users &gt; View details and land on the Organization users page.

The steps for configuring this page  are listed below:

To create an organization users page in site builder, follow these steps.

1. Create a page **Organization Users** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. >>  with links to My Account/Organization Users where My Account navigates back to the account management home page.
1. In the **Container** slot, add a **Business Organization list** module. >>Set Heading as "Organization Users"
1. In the **Business Organization list** module property panel, enable **Table Sort** property which allows a user to sort the table. In addition, enable **Table pagination** which allows pagination**.** Set the Pagination count to say "5"
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that we created earlier.
1. Navigate to the **Organization users tile** module property panel. Here add a Link to the **Organization Users** page that we just created in step \#9. Save and Publish. Now the page is created and can be accessed from the Account Management home page by a user.

<!--Below is an example showing the Organization users page on the B2B e-commerce site and site builder Organization Users page setup.-->

## Create invoice pages

In this section, we are going to discuss how the Invoices page can be setup on the B2B e-commerce site. The Invoice page displays the available invoices and allows a B2B user to pay or request for invoices. This page can be setup using **InvoicesList** and **Invoice details** module.

### Create an invoice list page

This page shows the list of all invoices available and allows the user to pay or request for invoices. The steps for configuring this page in site builder are listed below:

1. Create a page **Invoices List** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. >> with links to My Account/Invoices where My Account navigates back to the account management home page.
1. To this Container add **InvoicesList module.** Set Heading as "Invoices"
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.
1. Go to Account Management home page **My Account** that we created earlier.
1. Navigate to the **Account invoices tile** module property panel. Here add a Link to the Invoices List page that we just created in step \#8. Save and Publish. Now the Invoice page is created and can be accessed from the Account Management home page by a user.

<!--Below is an example of the Invoices List page on e-commerce site and the page configuration in site builder.-->

### Create an invoice details page

This page shows the details of each invoice displayed in the Invoices List page. When a user selects on Invoice id from the Invoices page they will be navigated to the details. The steps for configuring this page in site builder are listed below:

1. Create a page **Invoice Details** using the **Account Management** template created in section Account Management of this document.
1. In the **Header** slot, add the header fragment that is preconfigured with the site header.
1. In the **Footer** slot, add the footer fragment that is preconfigured with the site footer.
1. In the **Main** slot, add a **Container** module. Set the **Width** to **Fill Container**.
1. In the **Container** slot, add a **Breadcrumb** module. >> with links to My Account/Invoices Lists/ Invoice Details. My Account navigates back to the account management home page. Invoice Lists navigates back to Invoice list page
1. In the **Container** slot, add an **Invoice details module.**
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Publish the URL for the page.

<!--Below is an example of the Invoice details page on e-commerce site and the page configuration in site builder.-->

## Additional resources

[Module library overview](../starter-kit-overview.md)

[Authoring page overview](../authoring-home-overview.md)

[Templates and layouts overview](../templates-layouts-overview.md)

[Work with fragments](../work-with-fragments.md)

[Add a new site page](../add-new-page.md)

[Checkout module](../add-checkout-module.md)

[Content block module](../add-hero-module.md)

[Product Collection](../product-collection-module-overview.md)


