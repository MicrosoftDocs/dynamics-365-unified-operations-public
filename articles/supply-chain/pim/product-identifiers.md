---
# required metadata

title: Types of product identifiers 
description: This article explains the types of product identifiers and how you can add product identifiers in your product data.
auhor: cvocph
manager: AnnBe
ms.date: 28/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductEntityIdentifierCode
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: conradv
ms.dyn365.ops.version: 7.3 
ms.search.validFrom: 2017-12-31

---

# Types of product identifiers 


[!include[banner](../includes/banner.md)]


This article explains the types of product identifiers and how you can add product identifiers in your product data.

Working with products in ERP or CRM, on the shopfloor or in a warehouse requires a good strategy to identify those products - and product variants.  

## The unique product number / product ID 

In Dynamics 365 for operations the primary identification of a product is the Product Number (the unique Product ID). This number can result of a number sequence, or can be associated manually. For product variants, the numbers can be defined through the product nomenclature template. 
In many cases, the product number is not originally created in Dynamics 365 for finance and operations, but associated in a PLM or PDM system. In this case, you would use the data entities to import the products and product variants, and Dynamics would use those numbers accordingly throughout all operations. Note that per instance (to be precise: per partition), a product number MUST be unique over all products AND product variants. You will get an error when trying to create a new product with a product number that already exists.  
This means that the product number is unique over all legal entities of a partition, what makes it simpler to identify the product throughout the supply chain.  
When implementing Dynamics 365 the product number strategy should always have special considerations. A good numbering system improves logistics flows and avoids errors. A good product identifier is not longer than 15 characters - ideally less than 10, and does not include more than 5 classifying characters. Use the search names to provide an additional name, that represents the classifications of a product for quick search.  
When using the common data service, the Product Number is also the product number of the common data service. Product variants are synchronized to the common data service (CDS) as distinct products.  


## The item number and the product dimensions 

The item number is the product identification of a specific legal entity. The item number should ideally be identical to the Product number, as different nomenclature by legal entity makes it difficult to follow a product throughout a supply chain and introduces painful relabeling and referencing processes. For combability reasons to older versions  (AX 2009 and older) we have preserved this model, but we do recommend to eliminate identifiers specific to legal entities wherever possible and use the unique product number as primary identifier.  
A product variant cannot be identified uniquely by an item number, it always requires the combination of item number and all the product dimensions defined on the product master, to identify the product variant, what can become very cumbersome  and slows down identification processes. This is another reason why we recommend to use the unique product number instead, wherever possible.  
Many forms still have the item number and product dimensions as the primary identification. There is however a possibility to use the product numbers for search. Under Sales and marketing > Setup > Search > Search parameters, you can change the search lookup to use product numbers instead of item numbers as primary search strategy. If you set Enable lookup for product search to Yes, the lookup will not only show product masters but product variants and allow you to search and filter on the product number, the product name and description and the product dimension ID's of the product variant. When selecting a variant, the related Item number and all product dimension ID's will be selected, what makes it easier to find and select the right variant.  
This setting is highly recommended, if you use product variants and the unique product number as the primary identifier of the products. The only exception might be the Fashion industry, where it the business processes often require to start with the selection of the master, before a variant is selected. You should evaluate this option carefully before implementing the numbering system.  

## Product name and descriptions 

Product name and descriptions are the human readable identifiers of a product. They can be maintained in many languages, however the client of Dynamics 365 for operations shows the all product information by default in the default company language, not in the users language. The translated product name and description are however used in all communication with customers and vendors based on the language code of the customer and vendor accounts.  
For product variants, the product name can be generated through a product nomenclature template. As a product name has no requirement to be unique, you might find multiple products with the same name.  

## Product and item search names 

Dynamics 365 for finance and operations offers a secondary search name for products and also for items (released products). This search name does not require uniqueness and can be changed after the creation of a product or product variant. It is recommended to use the search name to search products by categories. The search names allow fast search especially on sales and purchase processes.  
The search name could also contain customer or vendor product ID, or another external product ID, if the primary search criteria for a product is this external ID.  

## External product identifiers (Customer and Vendor identifiers) 

For released products, you can maintain correspondent item numbers, item names and item descriptions of customers and vendors. The references are shown on the external documents like sales and purchaser orders, packing slips and invoices. In the current version the external references not shown in the core operations forms, with the exception of the vendor product number, that is shown in the product information dialog if a default vendor is defined for the released product.  
You can maintain the external product identifiers by released product, by released product variant, by customer, by vendor or by customer and vendor group.  
In the Released products form: 
For customers, open Sell > Related information > External item description 
For vendors, open Purchase > Related information > External item description 
In this form you can associate the Customer or Vendor item number, to a released product. Note that this association needs to be done per legal entity. The following information can be captured. Unfortunately, the labels are slightly misleading, they might be changed in a future version.  

External item number 
Item number of the customer 
Item number of the vendor 
Description 
Name that the customer associates with the item 
Name that the vendor associates with the item 
External item text 
Item Description of the customer 
Description of the vendor 
 
If many customers or many vendors use the same item numbers, like for example a purchase association or a retail group, you can create groups of customer or groups of vendors to simplify the maintenance of the external product information.  
For customer groups, go to Sales > Setup > Items > External item description to create and maintain the groups and the related item numbers. Associate the customers to the groups in Accounts receivable > Customers > All customers - In the fast tab Sales order defaults, set the Item customer group. 
 
For vendor groups, go to Procurement and sourcing > Setup > External item description group to create and maintain the groups the related item numbers.  
Associate the vendor to the groups in Accounts payable > Vendors > All vendors - In the fast tab Purchase order defaults, set the Item Vendor group. 
 
## Barcodes 

To identify a product with a barcode scanner, the product identifier needs to fulfill the requirements of the Barcode standard that is used. This is why the barcode typically does not contain the raw product number, but a specific number generated for the use of a selected barcode technology. You can maintain multiple barcodes by barcode type. You can even associate the same barcode to multiple products and select the actual active association, that is used when scanning a barcode.  
Before defining barcodes, you can define one or multiple Barcode Setups, that help to validate that barcodes follow the required guidelines and can therefore be effectively used when printing and scanning the barcodes. You can also maintain special barcodes for specific product quantities.  
It is recommended to use the barcode definition to main GTIN or EAN numbers 
You can maintain the barcodes in the released product form opening Manage inventory > Warehouse > Bar codes 

## GTIN - The Global Trade Item Number 

In eCommerce, it is crucial to speak a common language and refer to products with common identifiers. Certain industries therefore rely on a global item number system, that is facilitated by GS1. (https://www.gs1.org/id-keys/gtin) 
In Dynamics 365 for Finance and Operations you can either maintain the GTIN as Barcode (recommended) or you can maintain it through a specific form, in the released product form opening Manage inventory > Warehouse > GTIN codes. Note that unfortunately, the GTIN is maintained by legal entity, not as a global number.  
In Dynamics 365 for operations, you define packaging variants in the warehouse operations by defining specific units of measure. An item might be stored in pieces, bundles of 6, trays of 18 and full pallets. For each of these, you will define a specific unit of measure.  
As the GTIN is typically related to the packaging unit of a product, form allows you to maintain multiple GTIN's pre product and unit of measure. It is however not possible to use the same GTIN code twice for different items or product variants of a legal entity.  

## External codes 

Many entities in Dynamics 365 for operations allow to define External codes. For products and released products, external codes can be defined to identify the products. This could be used to associate statistical codes or tax codes to released products and released product variants. External codes are defined by legal entity and code type.  
There is however no standard functionality that allows to search for products by external codes. Note that external codes values must be unique by legal entity and code type, and table reference.  
  
## Data entities to import and export product identifiers 


| **Entity name**                                                            | **Imports identifiers**                                                           | **Exports identifiers**                                                                                                       | **Comments**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Products V2                                                                | Product Number  Product Search name  Product Name  Product Description            | Product Number  Product Search name  Product Name  Product Description                                                        | Depending on the settings of the entity and the Number sequence for the product number, the product number can be auto-created on import.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Product variants                                                           | Product Number  Product Search name  Product Name  Product Description            | Product Number  Product Search name  Product Name  Product Description                                                        | Depending on the product nomenclature template, the product number can be auto-created on import. You can however import any (unique) product number on import, that would not need to follow the structure of the product nomenclature templates.                                                                                                                                                                                                                                                                                                                        |
| Product translations                                                       | Product Name  Product Description                                                 | Product Name  Product Description                                                                                             | Overwrites any language. Note that when overwriting the name or description of the primary language of a legal entity, the name and description of the product as such is changed.                                                                                                                                                                                                                                                                                                                                                                                        |
| Released products V2                                                       | Item Number  Product Number  Item Search name                                     | Item number  Product number   Item Search name                                                                                | The released product entity can be a tricky one, when it comes to use the number sequences on creation of new released products. Both number sequences, Item number and Product number have an influence, however note that the item number sequence is per legal entity, while the Product number sequence is a global one. This is why it is not recommended to use the item number number sequence to be used when deploying new released products. Obviously, when using the entity to release an existing product, the Product number must be given in the entity.   |
|                                                                            |                                                                                   | Product Search name                                                                                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                                                                            |                                                                                   | Product Name                                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Released product variants                                                  | Item Number  Product dimensions  Product Number                                   | Product Number  Product Search name  Product Name  Product Description  Product Dimensions                                    | Like on the product variants, the released product variants can be used to create new products following the product nomenclature template or using own product numbers for the variant.                                                                                                                                                                                                                                                                                                                                                                                  |
| External item description for customers                                    | Customer Item Number  Customer Item Name  Customer Description  Customer account  | Customer Item Number  Customer Item Name  Customer Description  Customer account                                              | A group of Customers, for example a buyer association, can be aggregated to one Group by using the Externa item description customer groups entity                                                                                                                                                                                                                                                                                                                                                                                                                        |
| External item description for vendors                                      | Vendor Item Number  Vendor Item Name  Vendor Description  Vendor account          | Vendor Item Number  Vendor Item Name  Vendor Description  Vendor account                                                      | A group of Vendors, for example a sales association or industry organization, can be aggregated to one Group by using the Externa item description vendor groups entity                                                                                                                                                                                                                                                                                                                                                                                                   |
| Item Barcode                                                               | Barcode                                                                           | Barcode                                                                                                                       | Note that on import, you must refer to a barcode setup that is defined in the target system. The imported barcode references will be validated on import against that setup, and rejected if the barcodes are not matching to the requirements defined in the barcode setup.                                                                                                                                                                                                                                                                                              |
| External codes for released products                                       | External code                                                                     | External code  External code classes  Item Number                                                                             | External codes are by legal entity  For import, you need to refer to a defined code class. Import the code classes using the External code classes for released products entity                                                                                                                                                                                                                                                                                                                                                                                           |
| External codes for released product variants                               | External code                                                                     | External code  External code classes  Item Number  Product dimensions                                                         | External codes are by legal entity  For import, you need to refer to a defined code class. Import the code classes using the External code classes for released products entity  This entity refers to product variants by Item number and product dimensions.                                                                                                                                                                                                                                                                                                            |
| External codes for released product variants by product number identifier  | External code                                                                     | External code  External code classes  Product number                                                                          | External codes are by legal entity  For import, you need to refer to a defined code class. Import the code classes using the External code classes for released products entity  This entity refers to product variants by product number of the variant.                                                                                                                                                                                                                                                                                                                 |
|                                                                            |                                                                                   |                                                                                                                               | (From Release 8.0)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| GTIN                                                                       |                                                                                   |                                                                                                                               | At this stage, there is no specific entity to import and export GTIN numbers, we recommend to use the Item Barcode instead                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Product entity common data service identifier entity                       | N/A                                                                               | Item Number  Item Search name  Product Search name  Vendor Item number  Customer Item number  External codes  GTIN  Barcodes  | This entity consolidates all identifiers in one data model, making it easy to export all identifiers and their related types with one interface.  Use the entities Product entity identifier code entity to export the identifier codes and descriptions. Use the Product entity identifier scope entity to export additional scope information to an identifier, like party, legal entity, quantity or unit.       |



 
 
 
## Product entity identifier (Export all product identifiers) 


The product entity identifier model was created to allow to provision the common data service (CDS) version 1.0 with all identifiers, that are referenced to a product. To simplify this task, all identifiers are aggregated into one global identifier table that allows them to be exported as one model. Note, that this version of CDS has never up taken the product identifiers model, why the practical use of this entity and process is limited and most probably subject to change in the future.  
The product identifier table is a global table that is populated from all reference tables of the "Main" legal entity with a recurring batch job. You have to select a legal entity and a product category hierarchy as the definition of the global product master scope. The generation of the global identifier table will be limited to products that are released to the selected legal entity and products that are members of the product hierarchy that is selected for the Product category hierarchy role Common data service.  
This process assumes, that product master data are primarily maintained in one central legal entity (this could be a virtual legal entity, that is only used to maintain global master data).  
Configuration of the environment: 
To select the category hierarchy for CDS, open the Category hierarchy role associations form. If no hierarchy has been associated to the role Common data service, you need to create a new association, select the role Common data service and associate the category hierarchy that represents the product portfolio that should be synchronized to the common data service.  
To select the legal entity for global product master data, open the Product information management parameters and select the Product attributes tab. Select the master company where the product and item identifiers are primarily maintained.  
To define the identifier types and codes that should be exported, go to Product information management > Setup > Product identifier codes  
To generate the identifier code types, run Generate codes. This function will generate a code type entry for each type for identifier that has been found in the selected legal entity. Note that for Barcodes a code type will be generated by Barcode setup. For external codes, a code type will be generated for each external code class. You can now maintain the list of code types. You can change the Code, name and description. You can also delete code types entirely, what means that those code types will not be used to populate the global Product entity identifier tables.  
Once you are done with the definition of the product identifier code types, you can run the creation of the identifiers in the global table by starting Create product entity identifiers. You should run this in batch. This job should be set up as a periodic batch jobs to populate the table according to new entries.  
You can now use the data entities Product entity common data service identifier entity, Product entity identifier code and  Product entity identifier scope to export the identifiers for any target system

 
