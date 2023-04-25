---
title: Account management pages and modules
description: This article covers account management pages and modules in Microsoft Dynamics 365 Commerce.
author: v-chgri
ms.date: 04/07/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.industry: 
---

# Account management pages and modules

[!include [banner](includes/banner.md)]

This article covers account management pages and modules in Microsoft Dynamics 365 Commerce.

Account management refers to a group of pages that is used to manage user account–related information in Dynamics 365 Commerce. Account management pages include the account management landing page, user profile page, user address page, order history page, order details page, loyalty page, and wish list page.

### Account management landing page

The account management landing page uses the following modules:

- **Container** - All account management landing page modules should be placed within a container. 
- **Account welcome tile** – This module is used to provide a welcome message on the account management page. It includes properties for the heading.
- **Account generic tile** - This module can be used to provide headings and links to account management pages, such as the "Order history" or "My profile" pages. The generic tile module can be used to configure a tile for any page. In Fabrikam, this module is used for "Order history" and "My profile" page links on the account management landing page.
- **Account wishlist tile** – This module is used to provide a summary of the items on the customer's wish list. For example, it might state, "You have 10 items in your wish list." It includes properties for the heading and the "View details" link. The "View details" link should be configured to redirect to the wish list page. 
- **Account address tile** – This module is used to provide a summary of the user's addresses. For example, it might state, "You have 2 addresses added to your account." It includes properties for the heading and the "View details" link. The "View details" link should be configured to redirect to the user address page.
- **Account loyalty tile** – This module is used to display and link to loyalty program information. This tile has two states: one state shows links to join a loyalty program if the user is not a member already. The other state shows links to view the loyalty details page when the user is already a member. Properties include the heading, the "Sign-up" link, and the "View loyalty" link. The "View loyalty" link should be configured to redirect to the loyalty page. The "Sign-up" link should be configured to redirect to a page where users can join the loyalty program. 

### Order history page

The order history page uses the order history module to show all the recent orders that the user has placed. The orders are retrieved for the time range that is defined in the **Days of customer history** configuration of the online functionality profile.

### Order details page

The order details page provides detailed information for each order and is accessed from the order history page. It uses the order details module, which requires the sales ID or transaction ID to retrieve the order details.

### My profile page

The My profile page shows the user's account profile details using the account profile module. The page shows the email address associated with the user's account, as well as preferences set up for the account. If setting up custom customer attributes, an "Additional Information" section will also display those attributes. Users can edit their name, preferences, or additional information (if available).

### User address page

The user address page shows the list of addresses that are associated with the user account. The user either provided these addresses during checkout or added them directly on  this page. The user address module is used add and edit addresses, set the primary address, and render existing addresses on the page.

### Wish list page

The wish list page shows the items that have been added to the customer's wish list. It uses the wish list module to render wish list items.

### Loyalty page

The loyalty page lets customers view their loyalty details if they are already loyalty program members. They can also view the points that they have earned and redeemed in recent transactions. The page uses the loyalty details module to showcase the loyalty details. 

To join loyalty program, a marketing page can be created with loyalty sign up and loyalty terms modules. If the user is not a member of a loyalty program, these modules will enable the user to sign up.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Container module](add-container-module.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Checkout module](add-checkout-module.md)

[Order confirmation module](order-confirmation-module.md)

[Header module](author-header-module.md)

[Footer module](author-footer-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
