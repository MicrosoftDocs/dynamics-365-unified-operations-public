---
# required metadata

title: Call center catalogs
description: This article describes the call center–specific functionality for catalogs in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 04/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailMCRChannelDetailPage, RetailCatalogDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16231
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Call center catalogs

[!INCLUDE [banner](includes/banner.md)]

This article describes the call center–specific functionality linked to the catalog capabilities in Microsoft Dynamics 365 for Retail.  

The catalog features found in Dynamics 365 for Retail can be used for multiple purposes.  Initially the catalog features were created to support 3rd party e-commerce integrations.  This allowed companies to create a catalog of products and attributes that could be published externally for consumption by a 3rd party ecommerce solution.  

When call center channel capability was added to Dynamics, the same catalog concept was expanded to add additional capabilities for supporting and managing the traditional direct to consumer marketing catalog concepts.   A direct to consumer company will often produce printed catalogs which are then mailed to one or more segments of customers.  These catalogs will typically have specific promotions or offers that will only be honored if the customer provides a catalog identification code at the time of order creation. 

Direct to consumer marketing companies are very focused on tracking the response to these catalogs to ensure the costs to produce and mail them are justified. To track the response, a code is traditionally printed on the back of the catalog and this code is then requested and applied when the catalog recipient calls to place an order by phone (or now more traditionally the code may be entered when the customer places an order online).   While there are different industry terms that have been used to identify this catalog tracking code (key code, promo code, catalog code, source code, etc...), we refer to the code in Dynamics 365 for Retail as the **Source Code ID**.

## Basic catalog setup

Navigate to **Retail** \> **Catalogs and assortments** \> **All catalogs** to configure your catalog.

When you create a new catalog, you must first link the catalog to one or more retail channels.  This is done in the **Retail channels** fast tab on the catalog setup form.  Use the **Add** function and select one or more retail channels.   Please note that only items linked to the selected channel(s) [assortments](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/assortments) can be used when creating the catalog.

Adding products to a catalog requires choosing a navigation hierarchy, this is to support the category structure for the catalog.  You must pick from one of the navigation hierarchies linked to the retail channels selected in the **Retail channels** fast tab of the catalog form. Navigate to **Retail** \> **Channel setup** \> **Channel categories and product attributes** to link a navigation heirarchy default to each of your retail channels.

From the **CATALOGS** menu tab on the catalog setup form, use the **Add products** option to configure the products to add to the catalog, or select a node in the navigation heirarchy which will change the screen presentation and allow for the addition of products directly to a category within the catalog.

Click the top node of the catalog hierarchy at any time to return to the main catalog header view.  Configure effective and expiration dates as necessary on the **General** fast tab.  

## Using catalogs to drive sales order pricing and promotions

A core reason for defining a catalog is to be able to configure specific prices and promotions for that catalog.  Customers ordering from this catalog will receive these prices and promotions in call center order entry if the catalog's **Source code ID** is applied to the order header or lines.

To configure catalog specific prices, use the **Price groups** option from the **CATALOGS** tab to link one or more price groups to the catalog.  All trade agreements, price adjustment journals, and retail advanced discounts (threshold, quantity, mix and match) that have been linked to the same price group will be applied when customer's order from this catalog. 

In the **Source codes** fast tab, use the **Add** action to add one or more **Source code ID** identifiers to this catalog.  This is the code that will be applied during call center order entry to the sales order header (and lines) that will link the sales order to the catalog and ultimately to the price group(s) and any special prices and promotions that have been configured.  

## Utilizing the source ID to track costs and response rates

When defining the **Source code ID**, you may optionally link this ID to a **Target market ID**.  The **Target market ID** can be defined in **Retail** \> **Customers** \> **Target market**.   The target market is a list of customers and/or prospects that belong to a user-defined segment.  Linking the customer or prospect data to the source code ID, allows for better visibility into the recipients of the catalog.  If a customer is linked to a target market and that target market is linked to an active source code ID, Dynamics users will be able to see what catalogs a customer has received by selecting the **Source codes** menu option in the **CUSTOMERS** menu tab on the **Customer service** form.   During order entry, call center users can also see the specific catalogs a customer was sent in the **Source** field drop down on the sales order header.  Changing the filter from **All** to **Targeted** will allow the user to see the specific active catalogs the customer was sent.  This is helpful in situations where the customer may have forgotten their catalog or can't locate or read the catalog code when they are calling in to create a sales order.

It is possible to link multiple **Source code ID**'s to a catalog.  This is often utilized if the company wants to track the response rate by different segments and will give a unique catalog code to different customer segments.  This allows for tracking the response rate down to the segment level within a particular catalog event.

Highlighting a particular **Source code ID** record and clicking the **Details** option in the **Source codes** fast tab will provide additional fields where sales projections, mailing costs, and mailing dates can be captured.  This data can all be helpful for doing detailed analysis on the effectiveness of the catalog.  Users can return to this form over time and use the **Source code analysis** and **Compare promotions** action buttons to trigger analytical reports based on current sales data and compare costs and budget to actuals.

## Configuring catalog specific order and item scripts 

When a call center user is creating a sales order, on-screen scripts can be shown to the user.  These text-based scripts may provide additional information that the user is to say to the customer, or it may be internal notes/reminders that the call center user should read and react to as they are creating the sales order.  

It is often helpful to have a different set of scripts for a particular catalog.  In the **Scripts** fast tab, pre-defined scripts can be linked to a catalog.  Use the **Timing** field to determine if the script will appear at the beginning of the order (as soon as the Source code ID is entered on the order header), or at the end of the order (in the sales order summary form).

When selecting a node in the catalog's hierarchy and working with the data in the **Products** fast tab, users may also link catalog/item specific scripts using the **Scripts** action.  

## Configuring catalog specific upsell and cross-sell items



## Analyzing catalog response and costs

## 


In a call center, you can use product catalogs to identify the products that you want to offer to customers. Call centers typically use printed catalogs. The design and production of a printed catalog is handled outside Dynamics 365 for Retail. However, you can create and store a digital form of a catalog by using the same pages that you use to set up online retail catalogs. Before you can create a catalog, you must set up product assortments and assign the assortments to a call center. You then add products to the catalog by selecting products from these assortments. After products have been added to the catalog, and the catalog is complete, you must validate the catalog to verify the data. You must then submit the catalog for review and approval. After the catalog is approved, it can be published. When a call center catalog is created, you can take a snapshot of the catalog data at the time that the catalog is published. This snapshot functionality lets you access a particular version of the catalog even if the catalog is later changed and updated. Call center catalogs can also be set up to include the following optional features:

-   **Source codes** – Source codes are used to track the customer response to specific catalog mailings.
-   **Free products** – Products can be included in a customer's order at no additional charge. These products are automatically added to an order when the source code for the catalog is entered into the order.
-   **Scripts** – Scripts are texts that a call center worker reads to a customer when a sales order is being created. Scripts can include greetings or purchase suggestions.
-   **Page layout** – A page layout captures the page position of products in the printed catalog. This information is used for the catalog area analysis report.




