---
title: Store selector module
description: Learn about the store selector module and how to add it to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 10/26/2026
ms.topic: how-to
audience: Application User
ms.author: asharchw
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2020-02-10
ms.custom: 
  - bap-template
---

# Store selector module

[!INCLUDE [banner](includes/banner.md)]

This article describes the store selector module and how to add it to site pages in Microsoft Dynamics 365 Commerce.

Customers can use the store selector module to pick up a product in a selected store after an online purchase. In Commerce version 10.0.13, the store selector module also includes capabilities that showcase a **Find a Store** page that shows nearby stores.

The store selector module lets users enter a location (city, state, address, and so on) to search for stores within a search radius. When the module opens, it uses the customer's browser location to find stores (if consent is provided).

## Store selector module usage

- Use a store selector module on a product details page (PDP) to select a store for pickup.
- Use a store selector module on a cart page to select a store for pickup.
- Use a store selector module on a standalone page that shows all available stores.

> [!NOTE]
> For B2B sites that use cross-legal-entity inventory lookup, use the warehouse and store locator module in the header and PDP buy box. The warehouse and store locator displays stores and warehouses across configured legal entities. For more information, see [Warehouse and store locator module](warehouse-store-locator-module.md).

## Fulfillment group setup in Commerce headquarters

For the store selector to display available stores, set up the fulfillment group in Commerce headquarters. For more information, see [Set up fulfillment groups](customer-orders-overview.md#set-up-fulfillment-groups).

Also, define the latitude and longitude of the retail store in headquarters for each store in the fulfillment group.

To enter the latitude and longitude values for a retail store in Commerce headquarters, follow these steps:

1. In Commerce headquarters, go to **Organization administration** > **Organizations**  > **Operating unit**.
1. Search by the operating unit number in the left pane.
1. On the **Addresses** FastTab, select **More options** > **Advanced**.

    :::image type="content" source="./media/Store-address.png" alt-text="Example of store details in headquarters." lightbox="media/store-address.png":::

1. On the Action Pane, select **Edit**.
1. On the **General** FastTab, enter values for **Latitude** and **Longitude**.

    :::image type="content" source="./media/Store-latitude-longitude.png" alt-text="Example of latitude and longitude setup for a store in headquarters." lightbox="./media/Store-latitude-longitude.png":::

1. On the Action Pane, select **Save**.
1. Run the 1070 **Channel configuration** distribution schedule job.

### Hide a store from the store selector module

Some stores in a fulfillment group might not be valid pickup locations. To ensure that only valid pickup locations appear as options in the store selector module, follow these steps in Commerce headquarters.

1. In Commerce headquarters, go to **Retail and Commerce** > **Commerce setup** > **Fulfillment groups** > **All stores**.
1. On the Action Pane, select **Edit**.
1. Under **Setup**, for every store that isn't a valid pickup location, clear the **Is Pickup Location** checkbox.
1. On the Action Pane, select **Save**.
1. Run the 1070 **Channel configuration** distribution schedule job.

> [!IMPORTANT]
>
> - Bing Maps for Enterprise is deprecated and is scheduled to be retired. If you have an enterprise license for Bing Maps for Enterprise, you can continue to use it until June 30, 2028. If you have a free or basic license for Bing Maps for Enterprise, you can continue to use it until June 30, 2025.
> - Until the Azure Maps modules becomes available in Commerce version 10.0.45, you can manually enable Azure Maps by following the steps provided in the [Dynamics365Commerce.Solutions GitHub repository](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.54/src/OnlineSDK/Extensibility%20Samples/AzureMaps).

## Azure Maps integration

The store selector module is integrated with the [Azure Maps REST application programming interfaces (APIs)](/azure/azure-maps/how-to-use-ts-rest-sdk) to use Azure Maps's Fuzzy Search features. You need an Azure Maps API key and must add it to the shared parameters page in Commerce headquarters. The integration with the Autosuggest API is used to show search suggestions when users enter locations in the search field.

For the Azure Maps REST SDK, you must ensure that the following URLs are allowed per your site's content security policy (CSP). You set up this configuration in Commerce site builder by adding allowed URLs to various CSP directives for the site (for example, **img-src**). For more information, see [Content security policy](dev-itpro/manage-csp.md).

- Add "blob:" to the **child-src** directive.
- Add `https://atlas.microsoft.com/` and `https://js.monitor.azure.com/` to the **connect-src** directive.
- Add `https://atlas.microsoft.com/` to the **font-src** directive.
- Add `https://atlas.microsoft.com/` to the **script-src** directive.
- Add `https://atlas.microsoft.com/` to the **style-src** directive.

## Pickup in store mode

The store selector module supports a **Pick up in store** mode that shows a list of stores where a product is available for pickup. It also shows store hours and product inventory for each store in the list. The store selector module requires the context of a product to render product availability and to let the user add the product to the cart, if the product's delivery mode is set to **pickup** at the selected store. For more information, see [Inventory settings](inventory-settings.md).

Add the store selector module to a buy box module on a product detail page (PDP) to show stores where a product is available for pickup. You can also add it to a cart module. In this case, the store selector module shows pickup options for each line item in the cart. You can also add the store selector module to other pages or modules through extensions and customizations.

For this scenario to work, configure products to use the **pickup** delivery mode. Otherwise, the module doesn't appear on the product pages. For more information about how to configure the delivery mode, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

The following image shows an example of a store selector module used on a product detail page.

:::image type="content" source="./media/BOPIS.PNG" alt-text="Example of a store selector module used on a PDP." lightbox="./media/BOPIS.PNG":::

> [!NOTE]
> In Commerce version 10.0.16 and later, you can enable a feature that allows an organization to define multiple pickup modes of delivery options for customers. If you enable this feature, the store selector module and other Commerce modules are enhanced to allow the shopper to choose from potentially multiple pickup delivery options if configured. To learn more about this feature, see [this documentation](./multiple-pickup-modes.md).

## Find stores mode

The store selector module also supports a **Find stores** mode. Use this mode to create a store locations page that shows available stores and their information. In this mode, the store selector module works without product context and can be used as a standalone module on any site page. If you turn on the relevant settings for the module, users can select a store as their preferred store. When a store is selected as a user's preferred store, the store ID is maintained in the browser cookie. Therefore, the user must accept a cookie consent message.

The following illustration shows an example of a store selector module that is used together with an Azure Maps module on a store locations page.

:::image type="content" source="./media/store-locator-azure.PNG" alt-text="Example of a store selector module and Azure Maps module on a store locations page." lightbox="./media/store-locator-azure.PNG":::

## Render a map

You can use the store selector module together with the Azure Maps module to show the store locations on a map. For more information, see [Azure Maps module](azure-maps-module.md).

## Store selector module properties

| Property name | Value | Description |
| ------------- | ----- | ----------- |
| Heading | Text | The heading for the module. |
| Mode | **Find stores** or **Pick up in store** | **Find stores** mode shows available stores. **Pick up in store** mode lets users select a store for pickup. |
| Style | **Dialog** or **Inline** | The module can be rendered either inline or in a dialog box. |
| Set as preferred store | **True** or **False** | When you set this property to **True**, users can set a preferred store. This feature requires that users accept a cookie consent message. |
| Show all stores | **True** or **False** | When you set this property to **True**, users can bypass the **Search radius** property and view all stores. |
| Autosuggest options: Max results | Number | This property defines the maximum number of autosuggest results that the Azure Maps Fuzzy Search API can show. |
| Search radius | Number | This property defines the search radius for stores, in miles. If you don't specify a value, the default search radius is 50 miles. |
| Terms of service | URL |  This property specifies the terms of service URL that's required to use the Azure Maps service. |

## Site settings

The store selector module respects the [Add product to cart settings](add-cart-settings.md). After an item is added to the cart from the store selector module, site users see the appropriate configured workflows.

## Add a store selector module to a page

For **Pickup in store** mode, you can use the module only on product detail pages (PDPs) and cart pages. Set the mode to **Pickup in store** in the module's property pane.

- For information on how to add a store selector module to a buy box module, see [Buy box module](add-buy-box.md).
- For information on how to add a store selector module to a cart module, see [Cart module](add-cart-module.md).

To configure the store selector module to show available stores for a store locations page, follow these steps:

1. In Commerce headquarters, go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, under **Template name**, enter **Marketing template**, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Store locations**, and then select **Next**.
1. Under **Choose a template**, select the **Marketing template** that you created, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container with 2 columns** module, and then select **OK**.
1. In the module's properties pane, set the **Width** value to **Fill Container**.
1. Set the **X-Small view port column configuration** value to **100%**.
1. Set the **Small view port column configuration** value to **100%**.
1. Set the **Medium view port column configuration** value to **33% 67%**.
1. Set the **Large view port column configuration** value to **33% 67%**.
1. In the **Container with 2 columns** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Store selector** module, and then select **OK**.
1. In the module's properties pane, set the **Mode** value to **Find stores**.
1. Set the **Search radius** value in miles.
1. Set other properties, such as **Set as preferred store**, **Show all stores**, and **Enable auto suggestion**, as you require.
1. In the **Container with 2 columns** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Azure Maps** module, and then select **OK**.
1. In the module's properties pane, set any additional properties as you require.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Related information

- [Module library overview](starter-kit-overview.md)
- [Buy box module](add-buy-box.md)
- [Cart module](add-cart-module.md)
- [Quick tour of PDP](quick-tour-pdp.md)
- [Quick tour of cart and checkout](quick-tour-cart-checkout.md)
- [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)
- [Manage Azure Maps for your organization](./dev-itpro/manage-azure-maps.md)
- [Azure Maps REST SDK](/azure/azure-maps/how-to-use-ts-rest-sdk)
- [Azure Maps module](azure-maps-module.md)
- [Warehouse and store locator module](warehouse-store-locator-module.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
