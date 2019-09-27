---
# required metadata

title: Account management pages
description: This topic covers account management pages in Microsoft Dynamics 365 Commerce.
author: v-chgri
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

This topic covers account management pages in Microsoft Dynamics 365 Commerce.

## Overview

Account management refers to a group of pages that is used to manage user account–related information in Dynamics 365 Commerce. Account management pages include the account management landing page, user profile page, user address page, order history page, order details page, loyalty page, and wish list page.

### Account management landing page

The account management landing page uses the following modules:

- **Content placement** – This module is a container module that holds all the modules on the account management landing page.
- **Account welcome item** – This module is used to provide a welcome message on the account management page. It includes properties for the heading and the tile size. The **Tile size** property defines the width of the module in the content placement module. Values range from **1** through **12**, where **12** represents the full width of the content placement container.
- **Account order placement item** – This module is used to provide a summary of the number of orders that have been placed by the user account. It includes properties for the heading, the tile size, and the "view details" link. The "view details" link should be configured to redirect to the order history page.
- **Account profile placement item** – This module is used to provide a summary of the user profile. It includes properties for the heading, the tile size, and the "view details" link. The "view details" link should be configured to redirect to the user profile page.
- **Account wishlist item** – This module is used to provide a summary of the items on the customer's wish list. For example, it might state, "You have 10 items in your wish list." It includes properties for the heading, the tile size, and the "view details" link. The "view details" link should be configured to redirect to the wish list page.
- **Account address item** – This module is used to provide a summary of the user's addresses. For example, it might state, "You have 2 addresses added to your account." It includes properties for the heading, the tile size, and the "view details" link. The "view details" link should be configured to redirect to the user address page.
- **Account loyalty item** – This module is used to show and link to loyalty program information. It includes properties for the heading, the tile size, the "view details" link, and the "become a member" link. The "view details" link should be configured to redirect to the loyalty page. The "become a member" link should be configured to redirect to a page where users can join the loyalty program.

### Order history page

The order history page uses the order history module to show all the recent orders that the user has placed.

### Order details page

The order details page provides detailed information for each order and is accessed from the order history page. It uses the order details module, which requires the sales ID or transaction ID to retrieve the order details.

### User profile page

The user profile page shows user account details, such as user's name and email address. It uses the user profile module. Although the email address can't be removed, it can be edited.

### User address page

The user address page shows the list of addresses that are associated with the user account. The user either provided these addresses during checkout or added them directly on  this page. The user address module is used add and edit addresses, set the primary address, and render existing addresses on the page.

### Wish list page

The wish list page shows the items that have been added to the customer's wish list. It uses the wish list module to render wish list items.

### Loyalty page

The loyalty page lets customers join a loyalty program or, if they are already loyalty program members, view their program details. They can also view the points that they have earned and redeemed in recent transactions.
