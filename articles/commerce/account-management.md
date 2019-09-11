---
# required metadata

title: Account management pages
description: This topic covers account management pages in Dynamics 365 Commerce.
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Account management pages

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers account management pages in Dynamics 365 Commerce.

## Overview

Account management refers to a group of pages that are used to manage user account-related information in Dynamics 365 Commerce. Account management pages include the account management landing page, user profile page, user address page, order history page, order details page, loyalty page, and wish list page.

### Account management landing page

The account management landing page uses the following modules.

**Content placement:** This is a container module that is used for all modules on the account management landing page.

**Account welcome item:** This module is used to provide a welcome message on the account management page. Its properties include heading and tile size. Tile size defines the width of the module within the content placement module. Tile size values range from 1-12, with 12 being the full width of the content placement container.

**Account order placement item:** This module is used to provide a summary of the number of orders placed by the user account. Its properties include heading, tile size, and view details link. The view details link should be configured to redirect to the order history page.

**Account profile placement item:** This module is used to provide a summary of the user profile. Its properties include heading, tile size, view details link. The view details link should be configured to redirect to the user profile page. 

**Account wishlist item:** This module is used to provide a summary of the customer's wish list items (for example, "You have 10 items in your wish list.") Its properties include heading, tile size, view details link. The view details link should be configured to redirect to the wish list page. 

**Account address item:** This module is used to provide a summary of the user's addresses (for example, "You have 2 addresses added to your account."). Its properties include heading, tile size, and view details link. The view details link should be configured to redirect to the user address page.

**Account loyalty item:** This module is used to display and link to loyalty program information. Its properties include heading, tile size, view details link, and become a member link. The view details link should be configured to redirect to the loyalty page. The become a member link should be configured to redirect the user to a page that will enable them to join the loyalty program.

### Order history page

The order history page uses the order history module to show all of the recent orders placed by the user. 

### Order details page

The order details page provides detailed information for each orde, and is accessed from the order history page. It uses the order details module which requires the sales ID or transaction ID to retrieve the order details.

### User profile page

The user profile page displays user account details such as name and email address, and uses the user profile module. The email address cannot be removed but can be edited.

### User address page

The user address page displays the list of addresses associated with the user account. These are addresses that the user provided during checkout or added directly from this page. The user address module is used add and edit addresses, set the primary address, and render existing addresses on the page.

### Wish list page

The wish list page displays the items added to the customer's wish list, and uses the wish list module to render wish list items.

### Loyalty page

The loyalty page enables customers to join a loyalty program, or to view their program details if already loyalty program members. They can also view points earned and redeemed in recent transactions.
