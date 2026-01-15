---
# required metadata

title: Call center catalogs
description: Learn about call center–specific functionality for catalogs in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/15/2026
ms.topic: how-to
ms.search.form: RetailMCRChannelDetailPage, RetailCatalogDetails
ms.reviewer: v-griffinc
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
---

# Call center catalogs

[!include [banner](includes/banner.md)]

This article describes the call center–specific functionality linked to the catalog capabilities in Microsoft Dynamics 365 Commerce.

You can use the catalog features found in Commerce for multiple purposes. Initially, Microsoft created the catalog features to support partner e-commerce integrations. Catalog setup allowed companies to create a grouping of products and attributes that they could publish externally for consumption by a partner e-commerce solution.

When Microsoft added call center channel support, it expanded the catalog concept to add capabilities for supporting and managing features related to traditional direct-to-consumer marketing catalogs. A direct-to-consumer company often produces printed catalogs, which it mails to one or more segments of customers. These catalogs typically have specific promotions or offers that the company only honors if the customer provides a catalog identification code at the time of order creation.

Direct-to-consumer marketing companies focus on tracking the response to these catalogs to ensure that the costs to produce and mail them are justified. To track the response, a code is traditionally printed on the back of the catalog. The call center requests this code and applies it when the catalog recipient calls to place an order by phone, or when the code is entered when the customer places an order online. While different industry terms identify this catalog tracking code (including key code, promo code, catalog code, source code), Commerce refers to the code as the **Source code ID**.

## Basic catalog setup

Go to **Retail and Commerce** \> **Catalogs and assortments** \> **All catalogs** to configure your catalog.

When you create a new catalog, link the catalog to one or more channels. Do this step in the **Commerce channels** FastTab on the **Catalog setup** form. Select **Add** and select one or more channels. You can only use items linked to your selected channel [assortments](/dynamics365/unified-operations/retail/assortments) when creating the catalog.

To add products to a catalog, choose a navigation hierarchy. The navigation hierarchy supports the category structure for the catalog. Pick from one of the navigation hierarchies linked to the channels you selected on the **Commerce channels** FastTab of the **Catalog** page. If you didn't previously link a navigation channel to a channel, go to **Retail and Commerce** \> **Channel setup** \> **Channel categories and product attributes** to link a navigation hierarchy default to each of your channels.

On the **Catalogs** menu tab, on the **Catalog setup** page, select **Add products** to configure the products to add to the catalog, or select a node in the navigation hierarchy. Selecting a node changes the screen presentation and allows you to add products directly to a category within the catalog.

Select the top node of the catalog hierarchy to return to the main catalog header view. Configure effective and expiration dates as necessary on the **General** FastTab.

Before you can use the catalog, you must publish it. Select **Validate catalog** on the **Catalogs** menu to process a validation. This required action validates that the required setup is accurate. Select **View results** to see the details of the validation. If errors are found, correct the data and run validation again until the validation passes.

After validation is confirmed, select **Workflow** on the menu to start the approval workflow. Select **Submit** on the **Workflow** menu to execute the process. Configure the steps and authorized users for the workflow from **Retail and Commerce** \> **Headquarters setup** \> **Commerce workflows**. The workflow defines the steps needed to get the catalog into an **Approved** status. When the catalog is in an **Approved** status, you can select the **Publish** option on the **Catalogs** menu to complete the process. After the catalog is in a **Published** status, it can be used in call center order entry and send catalog processes.

## Use catalogs to drive sales order pricing and promotions

Define a catalog to use with a call center so you can configure specific prices and promotions for that catalog. Customers ordering from this catalog receive these prices and promotions in call center order entry if you apply the catalog's **Source code ID** to the order header or lines.

To configure catalog-specific prices, select the **Price groups** option from the **Catalogs** tab to link one or more price groups to the catalog. All trade agreements, price adjustment journals, and advanced discounts (threshold, quantity, mix and match) that are linked to the same price group apply when customers order from this catalog.

On the **Source codes** FastTab, select **Add** to add one or more **Source code ID** identifiers to this catalog. Apply this code during call center order entry to the sales order header and lines. Use this code to link the sales order to the catalog and ultimately to the price groups and any special prices and promotions that you configure.

## Use the source ID to track costs and response rates

When you define the **Source code ID**, you can optionally link this ID to a **Target market ID**. Define the **Target market ID** in **Retail and Commerce** \> **Customers** \> **Target market**. The target market is a list of customers and prospects that belong to a user-defined segment. Linking the customer or prospect data to the source code ID provides better visibility into the recipients of the catalog. If a customer is linked to a target market and that target market is linked to an active source code ID and catalog, call center users can see what catalogs a customer received by selecting the **Source codes** menu option on the **Customers** menu tab on the **Customer service** page. During order entry, call center users can also see the specific catalogs a customer was sent in the **Source** drop-down list on the sales order header. Changing the filter from **All** to **Targeted** allows the user to see the specific active catalogs the customer was sent. This information is helpful in situations where the customer forgets their catalog or can't locate or read the catalog code when they're calling in to create a sales order.

You can link multiple source code IDs to a catalog. You often need this feature when a company wants to track the response rate by different segments. The company gives a unique catalog code to different customer segments, which allows for tracking the response rate, down to the segment level, within a particular catalog event.

Select a particular **Source code ID** record and select the **Details** option on the **Source codes** FastTab to provide additional fields where you can capture sales projections, mailing costs, and mailing dates. This data is helpful for doing detailed analysis on the effectiveness of the catalog. Users can return to this page over time and use the **Source code analysis** and **Compare promotions** buttons to trigger analytical reports based on current sales data and compare costs and budget to actuals.

## Configure catalog-specific order and item scripts

When a call center user creates a sales order, they can use on-screen scripts. These text-based scripts might provide additional information that the user should say to the customer, or they might be internal notes and reminders that the call center user should review and react to as they create the sales order.

It's often helpful to have different sets of scripts for different catalogs. On the **Scripts** FastTab, link predefined scripts to a catalog. Use the **Timing** field to determine if the script appears at the beginning of the order (as soon as the source code ID is entered on the order header), or at the end of the order (in the sales order summary form).

When users select a node in the catalog's hierarchy and working with the data on the **Products** FastTab, they can also link scripts that are specific to catalogs or items by using the **Scripts** action.

## Configure catalog-specific up-sell and cross-sell items

You can link up-sell and cross-sell suggestions to an item from the products setup, but in some cases, a company might want to promote special up-sell and cross-sell items to customers ordering a specific product from a specific catalog. On the **Products** FastTab, select an item and select **Up-sell/cross-sell items** to configure products to be up-sold or cross-sold to customers who purchase the selected item from the catalog. During call center order entry, catalog-specific up-sell and cross-sell items appear on the screen instead of standard up-sell and cross-sell products that you might configure for that item through the usual product configuration.

Up-sell and cross-sell items can also take advantage of the script features to show specific messages that a user sees when the up-sell or cross-sell item is displayed during order entry. Scripts tied to up-sell and cross-sell products configured specifically for a catalog product only appear when that catalog's source code is applied in call center order entry.

## Catalog page analysis

On the **Catalogs** tab, you can configure **Catalog pages**. This feature allows you to define specific pages and page types for the printed catalog and their associated costs.

When configuring the products in the catalog, use the **Product page layout** action to define the specific pages, percentage of page, and position of page details for the item. Configuring this data enables users to take advantage of the **Catalog area analysis report**. Users can access this report by going to **Retail and Commerce** \> **Call center reports** \> **Catalog area analysis**. It analyzes sales placed against the catalog (sales orders where the source ID for the catalog was tied to the order header or line) and their associated percent of page and costs to give a traditional direct marketing **Square inch analysis** report.

## Catalog requests

As you configure and publish catalogs in Commerce, use the **Send catalog** feature. This feature is available on the **Customer search** and **Customer service** pages. After users select a customer record through **Customer search** or while viewing a selected customer's account from **Customer service**, they can select the **Send catalog** option. The option opens a dialog box that allows the user to choose from a list of any published and active catalogs. A user can select a catalog and a quantity, and a particular source code ID to send. When they select **Send**, the request is stored. You can manage the request by printing the **Catalog requests** report. By navigating to **Retail and Commerce** \> **Call center reports** \> **Catalog requests report**, you can access this report. It lists all the catalog requests, including the customer name and address details of the customer who requested the catalog. You can use this report internally or transmit the data to a partner supporting external processes for physically sending the catalog to the customer.

## Additional features

On the **Catalogs** tab, you can also configure a **Payment schedule** and **Free products**. If the source code ID linked to the catalog is applied during call center order entry, the customer is eligible for free products, or the use of the specific catalog payment schedules as defined. If you need to limit the customer to only being able to select from payment schedules linked to their catalog and not all active payment schedules in the system, select the **Only allow catalog plans** check box for one or more of the source code IDs defined to enforce that limitation.

## Additional notes

Currently, when you apply a source code ID to a sales order in call center, it drives prices, promotions, scripts, and up-sell/cross-sells that are catalog specific. The system doesn't prohibit or prevent a product that isn't in the catalog from being ordered on the sales order. If you order an item that's not part of the catalog, the system first uses the **Price group** that is defined on the call center channel (**Retail and Commerce** \> **Channels** \> **Call centers** \> **All call centers**) for item price or promotions. If no specific channel price is found, the base selling price of the item is used.


[!INCLUDE[footer-include](../includes/footer-banner.md)]