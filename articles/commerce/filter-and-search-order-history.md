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

The order history with search and filters module works in the following ways:

- The module is displayed on a site user's account page, under the **Order history** section.
- Users can enter the order confirmation number, order number, or origin channel in the search box to search for orders.
- Users can filter by order date, channel origin, and order status.
- Using the sort button, users can sort orders by order placed date or order confirmed date.
- The module displays the order details in grid or list formats, with one row per order.
- Users can select order links to view order details such as items, shipping, and payment information.

## Add the order history with search and filters module to an order history page

To add an order history with search and filters module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, under **Template name**, enter the name **Order history template**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Default page** module, and then select **OK**.
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Generic container** module, and then select **OK**.
1. In the **Generic container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Order history with search and filters** module, and then select **OK**.
1. Select **Save**.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Order history page** and then select **Next**.
1. Under **Choose a template**, select **Order history template**, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**. 
1. In the **Main** slot of the **Default Page** module, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Generic container** module, and then select **OK**.
1. In the **Generic container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Order history with search and filters** module, and then select **OK**.
1. In the properties pane for the order confirmation module, select **Heading** next to the pencil symbol.
1. In the **Heading Text** field of the **Heading** dialog box, enter the heading text **Order history**, and then select **OK**.
1. Configure other properties as needed, as explained in [Configure the order history with search and filters module](#configure-the-order-history-with-search-and-filters-module).
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Configure the order history with search and filters module

You can configure the following module properties either at the template level or page level. 

- **Show channel information** - When this property is enabled, the module displays the channel information associated with each order. 
- **Number of orders per page** - Specifies the number of orders that are shown on a single order history page. 
- **Render sales order count** - When this property is enabled, the module displays the total order count. 
- **Enable grid view** - When this property is enabled, the module allows users to switch between the list or grid views when viewing their order history. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
