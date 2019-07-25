# Account Management

 

Account Management is a group of pages that are used to manage user account related information. The pages include Account Management landing page, User Profile page, Address page, Order history page, Order details page, Loyalty page and Wishlist page.

## Account Management Landing Page

This page uses the following modules:

**Content Placement:** This is a container that is used for all the modules in this page. Refer to content placement for more details.

**Account Welcome item:** This module is used to provide a welcome message to the account management page. It supports a Heading. Tile size defines the width of this module within the content placement. Tile size can be values 1-12. A 12 implies full width of the content placement container.

**Account order placement item:** This module is used to provide a summary of the orders placed by this user account. It supports a Heading, Tile size and a View details link. The View details link should be configured to redirect to Order history page.. See Order History page for more details.

**Account profile placement item:** This module is used to provide a summary of the user profile. It supports Heading, Tile size and a View details link. The View details link should be configured to redirect to the User profile page. See User profile page for more details.

**Account wishlist item:** This module is used to provide a summary of the Wishlist items “E.g You have 10 items in Wishlist”.  It supports Heading, Tile size and a View details link. The View details link should be configured to redirect to the Wishlist page. 

**Account address item:** This module is used to provide a summary of the user addresses E.g. “You have 2 addresses added to your account”. It supports Heading, Tile size and a View details link. The View details link should be configured to redirect to the User Address page

**Account loyalty item:** This module is used to provide a summary of the user addresses E.g. “You have 2 addresses added to your account”. It supports Heading, Tile size, View details link and Become a Member link. The View details link should be configured to redirect to the Loyalty page. The Become a member link should be configured to redirect the user to a page that will allow them to join the loyalty program.

## Order History Page

The page shows all the recent orders placed by the user. It uses Order History module. The module supports Order details page link, which redirects to the Order details page.  It supports a Heading and Back to Shopping link

## Order Details page

The Order details page provides a more detailed information of each order. It uses the order details module which requires the order item context for retrieving the details. It is accessed from the order history page.

## User Profile page

The user profile page shows user account details such as Name, Email. Email cannot be changed but name can be edited. It uses the user profile module.

## User Addresses page

The user address page shows the list of addresses associated to the user account. These are addresses the user provided during checkout or added directly from this page. The Address module is used Add/Edit and render existing addresses on this page.

## Wishlist page

The Wishlist page, shows the items added to the user Wishlist. It uses the Wishlist module to show the items in the Wishlist.

## Loyalty page

The user can join a loyalty program or if the user is already a loyalty member they can view their program details. They can also view the points earned and redeemed in recent transactions.

 

 