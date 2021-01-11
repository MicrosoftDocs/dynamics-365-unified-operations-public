---
# required metadata

title: B2B e-commerce site setup
description: This topic describes how to set up a B2B e-commerce site in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 01/11/2021
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


# B2B e-commerce site setup

[!include [banner](includes/banner.md)]

B2B e-commerce sites provides some key capabilities that optimize the
workflow for a B2B user. In this document, we will walk through the new
modules and site settings that need to be configured to enable the B2B
specific scenarios.

## Prerequisites

-   To setup a B2B e-commerce site, the features must be
    enabled/configured in Headquarters as defined in the feature
    documentation.

-   The core experiences for product discovery, product details page,
    cart, checkout etc., are powered by the same modules that are used in
    a B2C site. A site author should be familiar with all the modules
    that are supported by Dynamics 365 Commerce. Refer to [Module
    library](https://docs.microsoft.com/dynamics365/commerce/starter-kit-overview)
    for more details.

-   This document also assumes the site author understands the basics of
    Commerce [Site
    Builder](https://docs.microsoft.com/dynamics365/commerce/authoring-home-overview),
    [Templates](https://docs.microsoft.com/dynamics365/commerce/templates-layouts-overview),
    [Fragments](https://docs.microsoft.com/dynamics365/commerce/work-with-fragments),
    [Pages](https://docs.microsoft.com/dynamics365/commerce/add-new-page),
    etc., to be able to enable the B2B features in their e-commerce site.

## Site Settings

Site level settings can be accessed in Site Builder under Site
Settings/Extensions. For B2B scenarios, there are two new Site settings
that are added:

1. **Customer Account Payment** - Customer account payment allows the
    user to pay for an order using a customer account. This setting can
    be supported for B2B, B2C, All customers or disabled via this
    setting. If your B2B site supports Customer accounts, you should
    choose "Enabled for B2B customers"

2. **Enable order quantity limits** – When making large orders, the
    order quantity feature allows you to set limits on the number of
    items that can be ordered for each product/category etc. This
    feature can be configured in Headquarters. On e-commerce it can be
    enabled for all, disabled or enabled for B2B or B2C only.

Note: When upgrading to latest SSK, you will need to follow additional
steps to ensure these Site Settings are available in your environment.
These steps are called out under "Update appsettings.json" section
called out
[here](https://docs.microsoft.com/dynamics365/commerce/e-commerce-extensibility/sdk-updates).

## Become a Business Partner

To become a Business Partner, a user needs to first submit a business
partner request. To sign-up for a partner account, we need to setup a
partner account. On submitting the request, the user should see a
confirmation message that the request is submitted. In addition, the
link to partner request should be made available on the B2B home page
for user to easily discover and initiate the process.

### Business Partner Request

The request to become a business partner is initiated using the
**Partner Sign-up** module. This module allows you to collect the user
information necessary for the sign-up process. In addition, we also use
the **Business account address** module to capture the business user's
address.

Below are the steps needed to configure this page.

1.  In Site Builder, setup a template that allows Partner Sign-up,
    BreadCrumb, Header, Footer, Content Block, Text block, Breadcrumb,
    Product collection modules. Lets call this "Sign-up" template.

2.  In Site Builder, create a page "Business Partner Request" using
    "Sign-up" template

3.  In the Page Header slot, add the header fragment that is
    pre-configured with the site header.

4.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

5.  In the page Main slot, add a Container. Set Width to Fill Container.

6.  To the Container, add a Breadcrumb module. Configure the Breadcrumb
    with respective secondary links. In the e.g. shown below, we are
    using Account Home/ Current page

7.  To the Container add the **Partner Sign-up** module, below the
    Breadcrumb. In the module property panel, define the heading as
    "Become a business partner".

8.  Select the Partner-signup module in the module outline and Add
    module. Choose **Business account address**.

9.  To the Container, add a Text block module below the Partner-Signup
    module. Here you can define some terms and conditions for the
    sign-up process.

10. Save, Preview and Publish

11. Publish the Url for this new page.

Below is an image showing the Site builder page configuration and the
page hosting these modules.

### Request confirmation

Once a business partner request is submitted, we want to show a
confirmation to the user acknowledging their submission. For this we
will create a confirmation page and link the Partner request page to
this confirmation page.

1.  In Site Builder, create a page "Partner Request Confirmation " using
    "Sign-up" template

2.  In the Page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the page Main slot, add a Container. Set Container Width to Fill
    Container.

5.  To the Container, add a [**Content
    block**](https://docs.microsoft.com/dynamics365/commerce/add-hero-module).
    In the module property panel, provide heading as "Request
    submitted". Add a paragraph "Your request has been submitted".
    Provide a link "Back to shopping" that is wired to the home page for
    the user to continue shopping.

6.  Add another container and add [**Product
    Collection**](https://docs.microsoft.com/dynamics365/commerce/product-collection-module-overview)
    module. Configure this module with a recommendation or category list
    that we want to showcase on this page.

7.  Save, Preview and Publish

8.  Publish the Url for this new page.

9.  Go back to the **Business Partner Request** page created earlier.
    Edit. Select Partner request module and in the module property panel
    navigate to the "Link to the confirmation page" and configure with
    it the link to **Partner request Confirmation** page that we just
    created. Save and Publish.

### Partner Request in Homepage

Once the request sign-up and confirmation pages are created, we need to
make the sign-up accessible from the homepage. This can be achieved by
using any Content Block module on the home page.

1.  Open the homepage in Site Builder

2.  Select a Content block module. Change the Shop Now link to "Sign-up
    for a business partner" and link it to the **Business Partner
    Request** page. Change the image as applicable.

3.  Save and Publish.

## Account Management home page

Account Management home page includes all the account management
information needed for both B2B and B2C. In this section, we will define
the modules that we must configure on the Account Management home page.
To view this page, a user needs to be signed-in. In the section below,
we have covered the steps needed to configure this page in Site Builder.

1.  In Site Builder, create a template for **Account Management**
    template. This template should include all modules needed to build
    an Account Management home page – Header, Footer, Breadcrumb,
    Account Welcome Tile, Account Generic Tile, Account Address Tile,
    Account Wishlist tile, Account address tile, Account loyalty tile, .
    For B2B account manage home page add the following modules to the
    template **Account customer balance tile, Account order templates
    tile, Organization Users, Business Organization list, Customer
    Account balance, OrderTemplateLines, OrderTemplateList, Account
    Invoice tile, Invoices list, Invoice details.**

2.  Create a page using Account Management template **My** **Account.**

3.  In the Page Header slot, add the header fragment that is
    pre-configured with the site header.

4.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

5.  In the Main slot, add a Container. Set Width to Fill Container. To
    this Container add Breadcrumb and Welcome Tile. Configure the
    breadcrumb link as Home. To the Welcome Tile, add Heading as
    "Welcome"

6.  In the Main slot add another Container 2. Set Width to Fill
    Container. Set Number of Children shown to Two. In this Container
    add **Account generic tile**, define Heading as "My Profile" and
    provide a link to my profile page that is already configured. To the
    same Container add another **Account generic tile**, define Heading
    as "Order history" and provide a link to the order history page.

7.  In the Main slot add another Container3. Set Width to Fill
    Container. Set Number of Children shown to Two. In this Container
    add **Account address tile**, define Heading as "My Address" and
    provide a link to the my address page that is already configured. To
    the same Container add another **Account wishlist tile**, define
    Heading as "My Wishlist" and provide a link to the order history
    page.

8.  In the Main slot add another Container4. Set Width to Fill
    Container. Set Number of Children shown to Two. In this Container
    add **Organization users**, define Heading as "Organization Users".
    We will provide the link later once the respective page is created
    in Section of this document. To Container4 add **Account customer
    balance tile**, define Heading as "Account credit". We will provide
    the link later, once the respective page is created in Section of
    this document.

9.  In the Main slot add another Container5. Set Width to Fill
    Container. Set Number of Children shown to Two. In this Container
    add **Account order templates tile**, define Heading as "Order
    Templates". We will provide the link later once the respective page
    is created in Section of this document.

10. Save, Publish.

Note: Some of the sections added in step 8-10 will not appear in the
Site builder WYSIWIG as they require a B2B sign-in account.

At this point the home page is configured with all the tiles needed to
display B2B information

## Customer Account for payments

Customer account can be used as a payment for an order. In addition,
available balance in a customer account can be also viewed from the
user's account management page.

### Viewing Customer Balance 

To view customer balance for a signed-in B2B user, we need to first
create a customer balance page. In this section we will review the steps
needed to create this page.

1.  Create a page **Customer Balance** using the **Account Management**
    template created in section Account Management of this document.

2.  In the Page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Customer balance

6.  To this Container add a **Customer Account Balance module.** Set
    Heading as "Account Balance"

7.  Save and Publish page.

8.  Publish Url.

9.  Go to Account Management home page **My Account** that we created
    earlier.

10. Navigate to the **Account customer balance tile** module property
    panel. Here add a Link to the **Customer Balance** page that we just
    created. Save and Publish. Now the page is created and can be
    accessed from the Account Management home page by a user.

Below image shows the Site Builder page configuration and the Customer
account credit page on the e-commerce site.

### Using Customer Balance as a payment

To use customer balance as a form of payment, the **Customer Account
Payment** module is required. This module should be added to the
Checkout page as a form of payment. For details on how to configure a
Checkout page and the modules that are needed for checkout including all
payment details, refer to the [Checkout module
documentation](https://docs.microsoft.com/dynamics365/commerce/add-checkout-module).

Once you have a Checkout page configured, you need to add **Customer
Account Payment** to the payment section of this page. Then save and
publish the page. A B2B user will now be able login to the ecommerce
site and use their available customer balance amount to their order
during checkout.

In addition, under Site Builder/Extensions, ensure the Customer Account
Payment property is **Enabled for B2B customers.**

Below is an example showing the checkout page configuration in Site
builder and the checkout page on the e-commerce site using **Customer
Account Payment** module.

## Order Templates

In this section, we are going to discuss how the Order templates can be
setup on the B2B e-commerce site. Order template shows one or more
templates created by a B2B user and the products included in each
template. These pages can be setup using **Order templates list** and
**Order templates lines** module.

### Order templates list

This page shows the list of all order templates available. It allows you
to create/delete a template and add items in a template to shopping bag.
The steps for configuring this page in Site Builder are listed below:

1.  Create a page **Order templates** using the **Account Management**
    template created in section Account Management of this document.

2.  In the page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Order templates where My Account navigates back to the
    account management home page.

6.  To this Container add **Order templates list module.**

7.  Save and Publish page.

8.  Publish Url.

9.  Go to Account Management home page **My Account** that we created
    earlier.

10. Navigate to the **Account order templates tile** module property
    panel. Here add a Link to the Order templates List page that we just
    created in step \#8. Save and Publish. Now the Order templates list
    page is created and can be accessed from the Account Management home
    page by a user.

Below is an example of the Order templates page on e-commerce site and
the page configuration in Site Builder.

### Order templates lines

This page shows the details of each order template that is displayed in
the Order templates page. When a user selects the name of the template
on the order template page, it navigates to the details of each
template. Here the user can view the items in the template and edit
them.The steps for configuring this page in Site Builder are listed
below:

1.  Create a page **Order template lines** using the **Account
    Management** template created in section Account Management of this
    document.

2.  In the page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Order templates/ Order template lines. My Account navigates
    back to the account management home page. Order template navigates
    back to **Order templates** page

6.  To this Container add **Order template lines module.**

7.  Save and Publish page.

8.  Publish Url.

Below is an example of the Order template lines page on e-commerce site
and the page configuration in Site Builder.

## On-boarding business partner users

The Admin user of the business partner organization can on-board
additional users from the organization to the B2B e-commerce website by
using **Business** **Organization list** module. From this page an admin
can add/remove users, define account balance, request statements etc for
a user.

On e-commerce, we need to first configure a page with **Business**
**Organization list** module and then link this page to Account
Management home page. A user can then sign into the B2B e-commerce
website. Navigate to My Account &gt; Organization users &gt; View
details and land on the Organization users page.

The steps for configuring this page in Site Builder are listed below:

1.  Create a page **Organization Users** using the **Account
    Management** template created in section Account Management of this
    document.

2.  In the page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Organization Users where My Account navigates back to the
    account management home page.

6.  To this Container add **Business** **Organization list module.** Set
    Heading as "Organization Users"

7.  In the Business Organization list module property panel, enable
 **Table Sort** property which allows a user to sort the table. In
    addition, enable **Table pagination** which allows pagination**.**
    Set the Pagination count to say "5"

8.  Save and Publish page.

9.  Publish Url.

10. Go to Account Management home page **My Account** that we created
    earlier.

11. Navigate to the **Organization users tile** module property panel.
    Here add a Link to the **Organization Users** page that we just
    created in step \#9. Save and Publish. Now the page is created and
    can be accessed from the Account Management home page by a user.

Below is an example showing the Organization users page on the B2B
ecommerce site and Site Builder Organization Users page setup.

## Invoices

In this section, we are going to discuss how the Invoices page can be
setup on the B2B e-commerce site. The Invoice page displays the
available invoices and allows a B2B user to pay or request for invoices.
This page can be setup using **InvoicesList** and **Invoice details**
module.

### Invoice List

This page shows the list of all invoices available and allows the user
to pay or request for invoices. The steps for configuring this page in
Site Builder are listed below:

1.  Create a page **Invoices List** using the **Account Management**
    template created in section Account Management of this document.

2.  In the page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Invoices where My Account navigates back to the account
    management home page.

6.  To this Container add **InvoicesList module.** Set Heading as
    "Invoices"

7.  Save and Publish page.

8.  Publish Url.

9.  Go to Account Management home page **My Account** that we created
    earlier.

10. Navigate to the **Account invoices tile** module property panel.
    Here add a Link to the Invoices List page that we just created in
    step \#8. Save and Publish. Now the Invoice page is created and can
    be accessed from the Account Management home page by a user.

Below is an example of the Invoices List page on e-commerce site and the
page configuration in Site Builder.

### Invoice Details

This page shows the details of each invoice displayed in the Invoices
List page. When a user selects on Invoice id from the Invoices page they
will be navigated to the details. The steps for configuring this page in
Site Builder are listed below:

1.  Create a page **Invoice Details** using the **Account Management**
    template created in section Account Management of this document.

2.  In the page Header slot, add the header fragment that is
    pre-configured with the site header.

3.  In the page Footer slot, add the footer fragment that is
    pre-configured with the site footer.

4.  In the Main slot, add a Container. Set Width to Fill Container.

5.  To this Container add a Breadcrumb module with links to My
    Account/Invoices Lists/ Invoice Details. My Account navigates back
    to the account management home page. Invoice Lists navigates back to
    Invoice list page

6.  To this Container add **Invoice details module.**

7.  Save and Publish page.

8.  Publish Url.

Below is an example of the Invoice details page on e-commerce site and
the page configuration in Site Builder.
