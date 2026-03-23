---
title: Product search in the point of sale (POS)
description: Learn about improvements made to product search functionality in Microsoft Dynamics 365 Commerce. 
author: ShalabhjainMSFT
ms.date: 01/27/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-06-30
ms.custom: 
  - bap-template
---

# Product search in the point of sale (POS)

[!include [banner](includes/banner.md)]

This article provides an overview of improvements that Microsoft made to product search functionality in Microsoft Dynamics 365 Commerce.

The Store Commerce app and Store Commerce for web provide easy-to-use search functionality for products. Because the search bar is always present at the top of the Store Commerce app and Store Commerce for web windows, employees can quickly search for products.

Employees can search for products in the assortments and catalogs that are associated with the current store. They can also search in the assortments and catalogs that are associated with any other store in the company. Cashiers can sell and return products outside the store assortment.

## Product search

By default, product searches use the store assortment. This type of search is known as a *local product search*. However, employees can easily switch to any catalog that is associated with the current store, or they can search in a different store. This type of search is known as a *remote product search*. To change the catalog, select the **Categories** button on the left side of the page. At the top of the pane that appears, select the **Change catalog** button, and then select one of the available catalogs to browse it. The system searches the selected catalog for products.

On the **Change catalog** page, employees can easily select any store, or they can search for products across all stores.

:::image type="content" source="./media/Changecatalog.png" alt-text="Screenshot of changing the catalog.":::

A local product search searches in the following product properties:

- Product number
- Product name
- Description
- Dimensions
- Barcode
- Search name

### Additional local product search capabilities (conventional SQL full-text search) 

- For multiple-keyword searches (that is, for searches that use search terms), retailers can configure whether the search results include results that match *any* search term or only results that match *all* search terms. The POS functionality profile provides the setting for this functionality in a new group named **Product search**. The default setting is **Match any search term**. This setting is also the recommended setting. When you use the **Match any search term** setting, the search returns all products that fully or partially match one or more search terms. The results are automatically sorted in ascending order of products that have the most keyword matches, whether full or partial.

    The **Match all search terms** setting returns only products that match all the search terms, whether full or partial. This setting is helpful when the product names are lengthy, and employees want to see only limited products in the search results. However, this type of search has two limitations:

    - The search is done on individual product properties. For example, only products that have all the searched keywords in at least one product property are returned.
    - Dimensions aren't searched.
> [!NOTE]
> The following configurations of **Match any search term** and **Match all search terms** in POS functionality profiles apply only to **local** product searches (conventional SQL full-text search) experiences. This configuration has no effect on cloud-powered search experiences. The new search engine uses its own advanced algorithm to power search relevance for product search results. 

- Retailers can configure product search to show search suggestions as users type product names. The POS functionality profile provides a new setting for this functionality in a group named **Product search**. The setting is named **Show search suggestions while typing**. This functionality can help employees quickly find the product that they're searching for, because they don't have to type the whole name manually.
- The product search algorithm now also searches for the searched terms in the **Search name** property of the product.

:::image type="content" source="./media/Productsuggestions.png" alt-text="Screenshot of product suggestions.":::

## Additional resources

[Customer search](customer-search.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
