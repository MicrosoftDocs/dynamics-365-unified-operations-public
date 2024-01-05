---
title: Order history with search and filters module
description: This article covers the order history with search and filters module and explains how to configure it in Microsoft Dynamics 365 Commerce.
author: ashish-msft
ms.date: 01/05/2024
ms.topic: article
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31

---

# Order history with search and filters module

[!include [banner](../includes/banner.md)]

This article covers the order history with search and filters module and explains how to configure it in Microsoft Dynamics 365 Commerce.

The order history with search and filters module enhances the user experience of your e-commerce site by allowing shoppers to quickly locate their orders using various search and filter options. This module lists order search results with information such as order number, order confirmation number, order date, channel origin, order status, and order total, and provides links to view additional order details.

![Order history with Search and filters on an ecommerce website](./media/OrderHistoryWithSearchAndFilters.png)

The ‘Order history with search and filters’ module works as follows:

- The module is displayed on the user’s account page, under the ‘Order history’ section
- The user can enter the order confirmation number, order number, or origin channel to search for orders in the search box
- The user can also apply filters by order date, channel origin, and order status in the filter panel
- The user can also sort the orders by order placed date or order confirmed date in the sort button
- The module displays the order details in a grid or list form, with one row per order
- The user can click on the link to view order details to see more information about the order, such as items, shipping, payment, and other details.

## Add order history with search and filters module to a site page

To add the module of order history with search and filters to your page, you need to make sure that your webpage template has a ‘Generic Container’ element that can contain this module. 

![Add order history with search and filters to an associated page template](./media/Template_With_OrderHistory_AllowingSearchAndFiltering.png)

Then, you can add the module of order history with search and filters into the ‘Generic Container’ element to your order history page DOM structure.
![Add order history with search and filters to your page](./media/AddModuleToPageOfOrderHistoryWithSearchAndFilters.png)

You can configure the following module properties either at a template level or at a page level - 

1. Show channel information - Allow you to show channel information associated with each order. 
2. Number of orders per page - Defines number of orders that will be shown on a single page of order history. 
3. Render sales order count - Enabling this property will show the total count of the orders. 
4. Enable grid view - Enabling this property will allow users to switch between the list or grid view when viewing order history. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
