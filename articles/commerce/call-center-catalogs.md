---
# required metadata

title: Call center catalogs
description: This article describes the call center–specific functionality for catalogs in Dynamics 365 Commerce.
author: josaw1
ms.date: 05/15/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailMCRChannelDetailPage, RetailCatalogDetails
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Call center catalogs

[!include [banner](includes/banner.md)]

This article describes the call center–specific functionality linked to the catalog capabilities in Dynamics 365 Commerce.

The catalog features found in Commerce can be used for multiple purposes. Initially the catalog features were created to support third-party e-Commerce integrations. Catalog setup allowed companies to create a grouping of products and attributes that could be published externally for consumption by a third-party e-Commerce solution.

When call center channel support was added, the catalog concept was expanded to add additional capabilities for supporting and managing features related to traditional direct-to-consumer marketing catalogs. A direct-to-consumer company will often produce printed catalogs, which are then mailed to one or more segments of customers. These catalogs will typically have specific promotions or offers that will only be honored if the customer provides a catalog identification code at the time of order creation.

Direct-to-consumer marketing companies are very focused on tracking the response to these catalogs to ensure that the costs to produce and mail them are justified. To track the response, a code is traditionally printed on the back of the catalog and this code is then requested and applied when the catalog recipient calls to place an order by phone (or now more traditionally the code may be entered when the customer places an order online). While there are different industry terms that have been used to identify this catalog tracking code (including key code, promo code, catalog code, source code), we refer to the code in Commerce as the **Source code ID**.

## Basic catalog setup

Go to **Retail and Commerce** \> **Catalogs and assortments** \> **All catalogs** to configure your catalog.

When you create a new catalog, you must first link the catalog to one or more channels. This is done in the **Commerce channels** FastTab on the **Catalog setup** form. Click **Add** and select one or more channels. Only items linked to your selected channel [assortments](/dynamics365/unified-operations/retail/assortments) can be used when creating the catalog.

To add products to a catalog, a navigation hierarchy must be chosen. The navigation hierarchy will support the category structure for the catalog. You must pick from one of the navigation hierarchies linked to the channels selected on the **Commerce channels** FastTab of the **Catalog** page. If a navigation channel was not linked to a channel previously, go to **Retail and Commerce** \> **Channel setup** \> **Channel categories and product attributes** to link a navigation hierarchy default to each of your channels.

On the **Catalogs** menu tab, on the **Catalog setup** page, click **Add products** to configure the products to add to the catalog, or select a node in the navigation hierarchy (selecting a node will change the screen presentation and allow you to add products directly to a category within the catalog).

Click the top node of the catalog hierarchy to return to the main catalog header view. Configure effective and expiration dates as necessary on the **General** FastTab.

Before the catalog is available to use, it must be published. Click **Validate catalog** on the **Catalogs** menu to process a validation. This is required action and will validate that the required setup is accurate. Click **View results** to see the details of the validation. If errors are found, you must correct the data and run validation again until the validation has passed.

After validation is confirmed, click **Workflow** on the menu to start the approval workflow. Click **Submit** on the **Workflow** menu to execute the process. Configure the steps and authorized users for the workflow from **Retail and Commerce** \> **Headquarters setup** \> **Commerce workflows**. The workflow will define the steps needed to get the catalog into an **Approved** status. When the catalog is in an **Approved** status, you can click the **Publish** option on the **Catalogs** menu to complete the process. After the catalog is in a **Published** status, it can be used in call center order entry and send catalog processes.

## Use catalogs to drive sales order pricing and promotions

A core reason for defining a catalog to use with a call center is to be able to configure specific prices and promotions for that catalog. Customers ordering from this catalog will receive these prices and promotions in call center order entry if the catalog's **Source code ID** is applied to the order header or lines.

To configure catalog-specific prices, select the **Price groups** option from the **Catalogs** tab to link one or more price groups to the catalog. All trade agreements, price adjustment journals, and advanced discounts (threshold, quantity, mix and match) that have been linked to the same price group will be applied when customers order from this catalog.

On the **Source codes** FastTab, click **Add** to add one or more **Source code ID** identifiers to this catalog. This is the code that will be applied during call center order entry to the sales order header (and lines). This code is used to link the sales order to the catalog and ultimately to the price groups and any special prices and promotions that have been configured.

## Use the source ID to track costs and response rates

When defining the **Source code ID**, you can optionally link this ID to a **Target market ID**. The **Target market ID** can be defined in **Retail and Commerce** \> **Customers** \> **Target market**. The target market is a list of customers and/or prospects that belong to a user-defined segment. Linking the customer or prospect data to the source code ID allows for better visibility into the recipients of the catalog. If a customer is linked to a target market and that target market is linked to an active source code ID/catalog, call center users will be able to see what catalogs a customer has received by selecting the **Source codes** menu option on the **Customers** menu tab on the **Customer service** page. During order entry, call center users can also see the specific catalogs a customer was sent in the **Source** drop-down list on the sales order header. Changing the filter from **All** to **Targeted** will allow the user to see the specific active catalogs the customer was sent. This is helpful in situations where the customer may have forgotten their catalog or can't locate or read the catalog code when they are calling in to create a sales order.

It's possible to link multiple source code IDs to a catalog. This is often needed when a company wants to track the response rate by different segments. The company will give a unique catalog code to different customer segments, which allows for tracking the response rate, down to the segment level, within a particular catalog event.

Selecting a particular **Source code ID** record and clicking the **Details** option on the **Source codes** FastTab will provide additional fields where sales projections, mailing costs, and mailing dates can be captured. This data is helpful for doing detailed analysis on the effectiveness of the catalog. Users can return to this page over time and use the **Source code analysis** and **Compare promotions** buttons to trigger analytical reports based on current sales data and compare costs and budget to actuals.

## Configure catalog-specific order and item scripts

When a call center user is creating a sales order, they can use on-screen scripts. These text-based scripts may provide additional information that the user should say to the customer, or it may be internal notes/reminders that the call center user should review and react to as they are creating the sales order.

It is often helpful to have different sets of scripts for different catalogs. On the **Scripts** FastTab, pre-defined scripts can be linked to a catalog. Use the **Timing** field to determine if the script will appear at the beginning of the order (as soon as the source code ID is entered on the order header), or at the end of the order (in the sales order summary form).

When selecting a node in the catalog's hierarchy and working with the data on the **Products** FastTab, users can also link scripts that are specific to catalogs or items using the **Scripts** action.

## Configure catalog-specific up-sell and cross-sell items

Linking up-sell/cross-sell suggestions to an item can be done from the products setup, but in some cases, a company may want to promote special up-sell/cross-sell items to customers ordering a specific product from a specific catalog. On the **Products** FastTab, select an item and click **Up-sell/cross-sell items** to configure products to be up or cross-sold to customers who purchase the selected item from the catalog. During call center order entry, catalog-specific up-sell/cross-sell items will appear on the screen instead of standard up-sell/cross-sell products that may have been configured for that item through the usual product configuration.

Up-sell/cross-sell items can also take advantage of the script features to show specific messages that a user will see when the up-sell/cross-sell item is displayed during order entry. Scripts tied to up-sell/cross-sell products configured specifically for a catalog product will only appear when that catalog's source code is applied in call center order entry.

## Catalog page analysis

On the **Catalogs** tab, options are available to configure **Catalog pages**. This feature allows you to define specific pages and page types for the printed catalog and their associated costs.

When configuring the products in the catalog, use the **Product page layout** action to define the specific pages, percentage of page, and position of page details for the item. Configuring this data will allow users to take advantage of the **Catalog area analysis report**. This report is found by navigating to **Retail and Commerce** \> **Call center reports** \> **Catalog area analysis** report. This report analyzes sales placed against the catalog (sales orders where the source ID for the catalog was tied to the order header or line) and their associated percent of page and costs to give a traditional direct marketing **Square inch analysis** report.

## Catalog requests

As catalogs are configured and published in Commerce, the **Send catalog** feature can be utilized. This feature is available on the **Customer search** and **Customer service** pages. After selecting a customer record through **Customer search** or while viewing a selected customers account from **Customer service**, users may select the **Send catalog** option which will open a dialog box allowing the user to choose from a list of any published and active catalogs. A user can select a catalog and a quantity, and a particular source code ID to send. When they click the **Send** button, a request is stored which can then be managed by printing the **Catalog requests** report. This report is found by navigating to **Retail and Commerce** \> **Call center reports** \> **Catalog requests report**. It lists all the catalog requests, including the customer name and address details of the customer who requested the catalog. This report can be used internally or the data can be transmitted to a third-party supporting external processes for physically sending the catalog to the customer.

## Additional features

On the **Catalogs** tab, options for configuring a **Payment schedule** and **Free products** are also available. If the source code ID linked to the catalog is applied during call center order entry, the customer will be eligible for the free products or use of the specific catalog payment schedules as defined. If it's necessary to limit the customer to only being able to select from payment schedules linked to their catalog and not all active payment schedules in the system, the **Only allow catalog plans** check box can be selected for one or more of the source code IDs defined to enforce that limitation.

## Additional notes

Currently, when a source code ID is applied to a sales order in call center, it is used to drive prices, promotions, scripts and up-sell/cross-sell's that are catalog specific. The system will not prohibit or prevent a product that is not in the catalog from being ordered on the sales order. If an item is ordered that is not part of the catalog, the system will first use the **Price group** that is defined on the call center channel (**Retail and Commerce** \> **Channels** \> **Call centers** \> **All call centers**) for item price or promotions. If no specific channel price is found, the base selling price of the item will be used.


[!INCLUDE[footer-include](../includes/footer-banner.md)]