---
# required metadata

title: Set up an online store channel
description: This article provides information about online store channels and how to set them up in Dynamics 365 Commerce.
author: kfend
manager: AnnBe
ms.date: 03/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailChannelManagementWorkspace, RetailOnlineStoreList
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16161
ms.assetid: 646d560c-f856-4701-b4ca-44e357ef09b8
ms.search.region: Global
ms.search.industry: Retail
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up an online store channel

[!include [banner](includes/banner.md)]

This article provides information about online store channels and how to set them up in Dynamics 365 Commerce.

Commerce supports multiple retail channels. These channels include online stores, call centers, and retail stores (also known as brick-and-mortar stores). Online stores give an online presence to a retailer, so that customers can purchase products from the retailer's online store in addition to its retail stores. If customers purchase products from the online store, those products can be shipped to them, or the customers can pick the products up at a local store. 

You create an online store in the Commerce client. This online store is then published to a third-party online store that is integrated with Commerce. The third-party online store serves as the storefront (UI) for the online store, and gives you a choice of customer management system (CMS) and UI capabilities. Several integrations of this type are available. 

The properties that you define for the online store control the behavior of the online store. For example, you define the navigation category hierarchy and assign it to the online store. When you publish the online store to the third-party online store, the navigation category hierarchy appears in the online version of the store. Shoppers then use the navigation category hierarchy to browse the online store and search for products. 

To create an online store, you must set up the components that enable transactions to be processed for the store. For example, you must add assortments, apply attributes, and set up payment methods and shipping methods. You can also define prices, promotions, discounts, trade agreements, and shipping terms that are specific to the online store. 

After you publish the online store to the third-party online store, you can create product catalogs for the online store. The products in the catalog become product listings in the online store. When a shopper purchases products from the online store, the available inventory is updated and synchronized in the client. Additionally, sales orders are generated for the purchases, and are sent to the client for order fulfillment and processing.

## Set up an online store

To set up an online store, you must complete the following tasks.

1. Create the online store.
2. Add the online store to the appropriate organization hierarchies.
3. Add assortments that include the products that are available in the online store.
4. Assign or create price groups for the online store.
5. Set up the modes of delivery that are available for the online store.
6. Assign the payment methods that are accepted by the online store.
7. If you allow shoppers to order products online and then pick them up at a local store, assign store locator groups to the online store.
8. Assign attributes for channels, products, and sales orders to the online store. Channel attributes apply to the whole online store, product attributes apply to the products that are offered in the online store, and sales order attributes apply to the sales orders that are generated from the online store.
9. Map attributes to define the properties that determine how those attributes behave in the online store. For example, attributes can be defined as required or searchable.
10. Publish the online store to generate the store structure on your choice of third-party online store.

    > [!IMPORTANT]
    > Before you publish the online store, you must set up a distribution location for it.

## Commerce channel navigation hierarchies

Before you create an online store, you must define the commerce channel navigation hierarchy that you want to use for it. The channel navigation hierarchy represents the category hierarchy that is displayed in the online store after the store is published. When you publish product catalogs to the online store, the products in the catalog are mapped to the categories in the channel navigation hierarchy. Shoppers then use the hierarchy to navigate in the online store.

## Organization hierarchies

Organization hierarchies are used to structure commerce channels and to represent the relationships between the organizations that make up your business. When you set up online stores, you can add them to an organization hierarchy. The stores then share the data that is used for assortments, replenishment, and reporting. 

When you create an organization hierarchy, you assign a purpose to it. The purpose indicates how the hierarchy is used in the business structure. You can create one organization hierarchy for your store operations, and use that hierarchy for assortments, replenishment, and reporting. 

Alternatively, you can create a separate organization hierarchy for each purpose. You can also create multiple hierarchies that have the same purpose, and assign a separate channel to each one. If you plan to publish product catalogs to the online store, you should, at a minimum, add the online store to an organization hierarchy for assortments. The products in a catalog are selected from the assortments that are assigned to the online store. When the catalog is published, the publishing process compares the effective dates for the assortment that is assigned to the online store with the products that are included in the catalog to determine which products to make available in the online store.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Create an e-Commerce site](create-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
