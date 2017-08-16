---
# required metadata

title: Product search and customer search in POS
description: This topic provides an overview of product and customer search improvements in Dynamics 365 for Retail. 
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
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Retail April 2017 update

---

# Overview of product and customer search in Point of Sale

Modern Point of Sale (MPOS) and Cloud Point of Sale (CPOS) enable store employees to quickly search for products and customers by providing an easy to use search functionality. The search bar is always present at the top of MPOS/CPOS for the employees to quickly find the products and customers. The employees can search for products in the assortments and catalogs associated to the current store and also within the assortments and catalogs of any other store within the company, thus enabling the cashiers to sell and return the products outside of the store assortment. Similarly, employees can search for customers associated to the current store or any other store within the company. Additionally, the employees can search for customers associated to a different company within the parent organization.

# Product search 

By default, the product search is performed on the store assortment (local product search), but the employees can easily switch to any catalog that is associated to the current store or search within a different store. This is also referred as *remote product search*. To change the catalog, select the categories menu and then select the **Change catalog** button at the top of the slider (refer to the image). Select any of the available catalogs to browse. The system will search the selected catalog for products. 

On the **Change catalog** page, the employees can also easily select any store or search across all the stores for products.

![Change catalog](./media/Changecatalog.png "Change catalog image").
 
The local product search searches within the following product properties:
- Product number
- Product name
- Description
- Dimensions
- Barcode 
- Search name

## Enhancements in the local product search

The product search experience has been enhanced to make it more user friendly. The enhancements are listed below:

- Product and customer drop-down menus added on the search bar so employees can select either **Product** or **Customer** before performing the search. The default selection is **Product**. Refer to the image for more details.
- For multi-keyword searches (search terms), retailers will have an option to configure if the POS search results should include the results that **Match any search term** or **Match all search terms**. This setting is available in the POS functionality profile, under a new group named **Product search**. The default value is set as **Match any search term** and is also a recommended setting. This results in all the products which fully or partially match one or more search terms and the results are automatically sorted in ascending order of products with most keyword matches (full or partial).

    The setting **Match all search terms** only returns those products which match all the search terms (full or partial). This setting is helpful when the product names are lengthy and the employees want to only see the limited products in the search result, however, this search has two limitations
     - The search is performed on individual product properties, such as only those products will be returned which have all the searched keywords in at least one of the product properties
     - Dimensions are not searched using this search setting
   
- The retailers can now turn on the capability to display search suggestions while typing product names. This configuration is added to the POS functionality profile under a group named **Product search** and the configuration is named **Show search suggestions while typing**. This can assist the employees to quickly find the product they are searching, instead of typing the whole name manually.
- The product search algorithm now also searches for the searched terms in the **Search name** property of the product.

![Product suggestions](./media/Productsuggestions.png "Product suggestions image")

# Customer search

Customer search is used to find customers for various purposes, such as viewing a customer's wish list, viewing the purchase history, or adding them to a transaction. In the case of multiple keyword search, the customer search algorithm returns all the customers that match any of the searched keywords. However, the customers that match the most keywords are displayed at the top of the results. This behavior is analogous to how the other search engines display the results i.e. first show the results that match the most searched terms, followed by the ones that partially match the search keywords. Lastly, this helps the cashiers in scenarios where they are searching with multiple keywords and one of the keyword has a spelling mistake. 

By default, the customer search is performed on the customer address books associated with the store (local customer search). However, the employees can also search for customers globally i.e. across the stores of the company and across all the other legal entities (remote customer search). To search globally, the employees can click the **Filter results** button and select the **Search all stores** option (refer to the image). This will not only return the customers, but return all types of parties, such as workers, vendors, contacts, or competitors, which are a part of any address book in the HQ. 

>[!NOTE]
>The remot' customer search has a limitation that it needs minimum 4 characters to be entered for the search to return the results.

In the remote search, the customers from the other legal entities are displayed without the Customer ID, because there is no customer ID created for this party in the current company. However, when the employee opens the customer details page, then the system automatically generates the customer ID for the party and also associates the store's customer address books with this customer as well. So henceforth, this customer will be visible in the local store search.

![Global customer search](./media/Globalcustomersearch.png "Global customer search image")

## Enhancements in local customer search

The local customer search helps employees quickly find the customers by their phone numbers, with or without typing the special characters such as space, hyphens, or brackets, which might be added to the customer's phone number. The cashiers can store the phone number in any format e.g. include brackets, hyphens, symbols etc. but while searching, the cashiers can search the customer by typing the partial phone number of the customer. If the cashier enters the phone number with some special characters, then the cashiers can find the customers by typing the numbers that appear after the special characters as well. For example, if the number is added as 123-456-7890, then the cashier can search for the customer by typing 123, or 456, or 7890, or 1234567890 or by partially entering the first few numbers of the phone number. 
