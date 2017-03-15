---
# required metadata

title: Search for products and product variants during order entry
description: Use the <strong>Item number </strong>field to search for products and product variants when you manually create a sales order line or a purchase order line.  This lets you quickly find product variants when you only have the configuration string or one of the product dimensions available.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-11-02 09 - 16 - 27
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: MCRFullTextIndexField, MCRFullTextParameters, PurchTable, SalesTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 248534
ms.assetid: 99dd5ce1-0029-4f06-90e7-865e6d46d86e
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Search for products and product variants during order entry

Use the <strong>Item number </strong>field to search for products and product variants when you manually create a sales order line or a purchase order line.  This lets you quickly find product variants when you only have the configuration string or one of the product dimensions available.

Sometimes, having too much of something is not the best situation to be in, and this is especially true if you sell a number of products that are similar, and you are trying to remember item numbers or product search names in order to find the right product to put on a sales order. You can use the **Item number** field on a sales order line or a purchase order line as a search field. You can enter any part of a product name, number, or dimension and get a lookup that displays all the items that match the search word.

## How search works
When you search for products or product variants, it is important to understand how the search feature finds the products that match the text that you enter. The key search rules in delivering search results are:

-   Search results will return any matching record, disregarding the field that the search text is entered in.
-   The search text needs to be present in the matching record in its full length.
-   A match will occur even if the search text is found in the middle of a text string in the matching record. It does not have to appear in the beginning of a text string.
-   The search text is treated as a single text string even if it contains white space.

### Examples

The following examples use products and product variants to illustrate how search is handled in various scenarios. **Prerequisite:** Under **Sales and marketing &gt; Setup &gt; Search &gt; Search parameters** &gt; **Search type**, select the **Full match** option.

| Product type     | Product name    | Display product number | Item number | Configuration |
|------------------|-----------------|------------------------|-------------|---------------|
| Distinct product | SpeakerMidRange | D0001                  | D0001       | NA            |
| Product variant  | Active speaker  | D0010:::Black:         | D0010       | 000005        |
| Product variant  | Active speaker  | D0010:::White:         | D0010       | White         |

If you type 'speak' in the **Item number** field, you will get all the products above as a result in the lookup. If you type 'black' in the **Item number** field, you will get the second product as a result, because it has the text 'black' in the display product number. These two examples illustrate that the search is not only at the beginning of the field, a match will occur even if the search text is found in the middle of a text string in the matching record. If you type '05' you will only get the second product variant as a result, because it has '05' in the configuration. This illustrates that the search is across all the enabled fields on the **Search criteria** page. If you type 'speak 05' you will not get any results. This is because the search looks for the full text that is entered. The search will not try to find 'speak' and then narrow the results to those containing '05'. You can limit the number of search results by using the **Number of results** field on the **Sales and marketing &gt; Setup &gt; Search &gt; Search parameters** page. If you set this field to 0, all search results will be returned. If you set it to 10, for example, it will return a maximum 10 search results.

## Configure the product search
Before you can use the product and product variant search feature, follow these steps to configure the product search. [![3 steps to configure product search\_AXAppFall](./media/3-steps-to-configure-product-search_axappfall.png)](./media/3-steps-to-configure-product-search_axappfall.png)

### Step 1: Include all the relevant product and product variant identifiers and dimensions in the search criteria

Examples of product and product variant identifiers and dimensions that you can search by are **Product name, Item number**, **Display product number, Configuration, Color, Size, Style, Search name, etc**. Go to **Sales and marketing &gt; Setup &gt; Search &gt; Search criteria** page. The **Search criteria** page allows you to define criteria for customer, prospect, and product search. Make sure you filter the page by using product search criteria. You can do this by switching to **Product** in the page's menu. To add the display product number to the search criteria, click **New** in the page's menu. This will add a new record in the **Search criteria** grid. Open the **Field name** column lookup and chose **DisplayProductNumber**. To add the product's configuration to the search criteria, create a new record in the **Search criteria **grid and chose **configId** in the **Field name** column. In the same manner, create a record with **Field name** **InventColorId** for the color dimension, **InventSizeId** for the size dimension, and **InventStyleId** for the style dimension.

### Step 2: Populate the database table that is used for product search

In the **Search criteria** page, click the **Update search data** button. In the **Update search data** dialog box, make sure that **Source** is set to **Product**, and then click **OK**. The system will aggregate in one table all the selected search criteria specified in step 1. If you have a lot of products and product variants, this operation can be quite lengthy and you may receive a warning. We recommend that you schedule the search table population on the batch server at a time when the server is not too busy. Until the table is populated, product search will not provide the correct results. If you do not get any search results, make sure that this table is populated. The table only has to be populated when the search criteria is modified. Newly released products and variants are automatically added to the table. Deleted products and variants are automatically removed from the table.

### Step 3: Enable the lookup for product search on sales and purchase order lines

You can enable this functionality by going to **Sales and marketing &gt; Setup &gt; Search &gt; Search parameters** and setting **Enable lookup for search** to **Yes** on the **General** tab. For sales order line entry, the default behavior is to open the **Product search** page when you start typing in the **Item number** field, and then press the **Tab** key. The **Product search** page changes the context during order line creation and may be considered unnecessarily intrusive. If you prefer to get the search results in a lookup and not lose context during order line entry, you can use the search lookup instead. If you search for a product or product variant, but you don't select anything in the lookup and press the **Tab** key, the **Product search** page will display.

