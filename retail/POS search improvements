---
# required metadata

title: Product search and customer search improvements in POS
description: This topic provides the overview of product and customer search improvements done in Dynamics 365 for Retail. 
author: shalabhjain
manager: AnnBe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
# ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Retail April 2017 update

---

# Overview of product and customer search in Point of Sale

The Modern Point of Sale (aka MPOS) and Cloud Point of Sale (aka CPOS) enable the store employees to quickly search for products and customers by providing an easy to use search functionality. The search bar is always present at the top of MPOS/CPOS for the employees to quickly find the products and customers. The employees can search for products in the assortments and catalogs associated to the current store and also within the assortments and catalogs of any other store within the company, thus enabling the cashiers to sell and return the products outside of the store assortment. Similarly, employees can search for customers associated to the current store or any other store within the company. Additionally, the employees can search for customers associated to a different company within the parent organization.

# Product search 

By default the product search is performed on the store assortment (aka 'local product search'), but the employees can easily switch to any other catalog associated to the current store or search within a different store. This is also referred as 'Remote product search'. To change the catalog, select the categories menu and then select the "Change catalog" button at the top of the slider (refer the below image). Select any of the available catalogs to browse and then the system will search the selected catalog for products. 

From the "Change catalog" screen, the employees can also easily select any other store or search across all the stores for products.

![Change catalog](./media/Changecatalog.png "Change catalog image").
 
 The local product search searches within the following product properties:
 	1. Product number
	2. Product name
	3. Description
	4. Dimensions
	5. Barcode 
	6. Search name (This has been added as a part of recent enhancement to be released in spring 2017 release)

## Enhancements in the local product search

As a part of 2017 April monthly cadence, we have further enhanced the product search experience to make it more user friendly. The enhancements are listed below:

1. We have added product and customer dropdowns to the search bar which enables the employees to select either 'Product' or 'Customer' before performing the search. The default selection is 'Products' so the products will be searched by default. Refer image 3 for more details.
2. For multi keyword searches (aka search terms) the retailers will have an option to configure in AX if the POS search results should include the results that 'Match any search term' or 'Match all search terms'. This setting is available in the POS functionality profile under a new group named "Product search" . The default value is set as 'Match any search term' and is also a recommended setting. This results in all the products which fully or partially match one or more search terms and the results are automatically sorted in ascending order of products with most keyword matches (full or partial).

    The setting 'Match all search terms' only returns those products which match ALL the search terms (full or partial). This setting is helpful when the product names are lengthy and the employees want to only see the limited products in the search result, however, this search has two limitations
      1. The search is performed on individual product properties i.e. only those products will be returned which have all the searched keywords in at least one of the product properties
      2. Dimensions are not searched using this search setting
      
3. The retailers can turn on the capability for the store employees to see search suggestions while typing product names. This configuration is added to the POS functionality profile under a group named "Product search" and the configuration is named "Show search suggestions while typing". This can assist the employees to quickly find the product they are looking for instead of typing the whole name manually.
4. The product search algorithm now also searches for the searched terms in the "Search name" property of the product.

![Product suggestions](./media/Productsuggestions.png "Product suggestions image").

# Customer search

Customer search is used to find customers for various purposes e.g. viewing customer's wish list, viewing the purchase history, adding them to transaction etc. In the case of multiple keyword search the customer search algorithm returns all the customers that match any of the searched keywords. However, the customers which match the most keywords are displayed at the top of the results. This behavior is analogous to how the other search engines display the results i.e. first show the results that match the most followed by the ones that partially meet the search keywords. Lastly, this helps the cashiers in scenarios where they are searching with multiple keywords and one of the keyword has a spelling mistake. Still the system will be able to show the desired customer in the result set because one or more keywords match the customer details.

By default the customer search is performed on the customer address books associated with the store (aka local customer search). However, the employees can also search for customers globally i.e. across the stores of the company and across all the other legal entities (aka remote customer search). To search globally, the employees can press the 'Filter results' button and select "Search all stores" option (refer the below image) . This will include not only the customers but all types of parties i.e. workers, vendors, contacts, competitors etc. which are a part of any address book in the HQ. The remote customer search has a limitation that it needs minimum 4 characters to be entered for the search to return the results.

In the remote search, the customers from the other legal entities are displayed without the Customer ID because there is no customer id created for this party in the current company. However, once the employee opens the customer details page then the system automatically generates the customer id for the party and also associates the store's customer address books with this customer as well. So henceforth, this customer will be visible in the local store search

![Global customer search](./media/Globalcustomersearch.png "Global customer search image").

## Enhancements in local customer search

As a part of 2017 April monthly cadence, we have further enhanced the local customer search to help the employees quickly find the customers by their phone numbers, with or without typing the special characters such as 'space', 'hyphens', 'brackets' etc. which might be added to the customer's phone number. The cashiers can store the phone number in any format e.g. include brackets, hyphens, symbols etc. but while searching, the cashiers can search the customer by typing the partial phone number of the customer. If the cashier enters the phone number with some special characters, then the cashiers can find the customers by typing the numbers that appear after the special characters as well. For e.g. if the number is added as 123-456-7890, then the cashier can search for the customer by typing 123, or 456, or 7890, or 1234567890 or partially entering the first few numbers of the phone number. 
