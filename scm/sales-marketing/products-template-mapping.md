---
# required metadata

title: Template mapping for products
description: This topic discusses the templates and underlying tasks that are used to synchronize products from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition to Microsoft Dynamics 365 for Sales.
author: ChristianRytt
manager: AnnBe
ms.date: 07/3/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.search.scope: Core, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ChristianRytt
ms.dyn365.ops.intro: July 2017 update 
ms.search.validFrom: 2017-07-8

---

# Products

[!include[banner](../includes/banner.md)]

This topic discusses the templates and underlying tasks that are used to synchronize products from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition to Microsoft Dynamics 365 for Sales.

## Template and task

The following templates and underlying tasks are used to synchronize products from Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (Finance and Operations) to Microsoft Dynamics 365 for Sales (Sales).

-   Name of template: Products (Fin and Ops to Sales)

-   Name of task in project: Products

Sync tasks required prior to Product sync: None

## Entity set

| **Finance and Operations** | **CDS** | **Sales**  |
|----------------------------|---------|------------|
| Sellable released products | Product | Products   |

## Entity flow

Products are managed in Finance and Operations and synchronized to Sales. The data entity **Sellable released products** in Operations only exports products that are sellable, which means that products have the information required to be used on a sales order. The same rules apply when a product is validated with the **Validate** function on the **Released product** page.

The **Product number** is used as key, meaning that product variants are synchronized to CDS and Sales with individual **Product IDs** per **Product variant**.

## Prospect to cash solution for Sales

In Sales, a new field on the products **Is Externally Maintained** is added to indicate that a given product is maintained externally. The value is set to **Yes** by default during import to Sales.

-   **Is Externally Maintained = Yes**: Product originates from Finance and Operations and will not be editable in Sales.

-   **Is Externally Maintained = No**: Product is entered directly in Sales.

-   **Is Externally Maintained = Blank**: Product exists in Sales prior to enabling the Prospect to cash solution.

The **Is Externally Maintained** information is used to ensure that only **Quotes** and **Sales orders** with **Externally maintained products** will sync to Finance and Operations.  
 
**Externally maintained products** are automatically added to the first valid **Price list** with the same currency. Note that the list is organized alphabetically by **Name**. The product sales price from Finance and Operations is used as price on the **Price list**. This means that it is required to have a **Price list** in Sales for each **Product sales currency** in Finance and Operations. Currency on the released sellable products is set to the accounting currency in the legal entity, from which the product is exported.

> [!NOTE]
> Product sync will not succeed without a **Price list** with the matching currency.

## Preconditions and mapping setup

-   Before you run the very first sync, you must populate the **Distinct product table** for existing products in Finance and Operations. Existing products will not be synchronized until this job is completed.

    -   In Finance and Operations, use Search to search for **Populate distinct product table**.

    -   Click the **Populate distinct product table** to run the job. This job only needs to be run once.

-   Ensure that the needed **ValueMap** for selling **Unit of measure (**UOM) in Finance and Operations exists in the **Source -\> CDS mapping SalesUnitSymbol / DefaultSellingUnitOfMeasure**.

-   Ensure that **Decimals supported** for UOM match your requirements in **CDS -\> Destination**. If you require different values per UOM, this can be done with **ValueMap** from Unit, for example, [Each : 0] & [Pound : 2].

    -   Template value is defaulted to 0.

-   Update the **CDS Organization ID Organization_OrganizationId** in **Source -\> CDS**.

    -   Template value is defaulted to ORG001.

-   Update **ValueMap** for **Unit group** (**defaultuomscheduleid.name**) in **CDS -\> Destination** to match the **Unit groups** in Sales.

    -   Template value is defaulted to **Default unit**.

-   Ensure that all products selling UOMs from Finance and Operations exist in Sales with the **CDS picklists** value.

-   Ensure that **Price lists** exist in Sales for each product sales currency in Finance and Operations.

-   Products can be created in Sales with status **Draft** or **Active**. This is controlled in **System settings** under **Sales** in Sales.

    -   Products created with draft status need to be activated before they can be added to **Quote** or **Sales order**.

>    

## Template mapping in Data integrator




![Machine generated alternative text: SOURCE ENTITY Sellable released products CDS ENTITY Product Destination ource \> CD Search SOURCE FIELD CDS \> MAP TYPE [Z ProductNumber [ProductNumber] [Z ProductName [ProductName] [Z ProductDescription [ProductDescription] [Z ProductType [ProductType] [Z SalesUnitSymbol [SalesUnitSymbol] SalesPrice [SalesPrice] [Z CurrencyCode [CurrencyCode] UnitCost [UnitCost] [Z CurrencyCode [CurrencyCode] [Z IsStockedProduct [IsStockedProduct] None DESTINATION ENTITY products DESTINATION FIELD [Z Productld [Product ID] Name [Name] [Z Description [Description] ProductType [Product type] DefaultSellingQuantity_lJOM [Unit of Measure of SellingUnitPrice [Selling unit price] SellingUnitPrice_CurrencyCode [Currency of StandardCostAmount [Standard cost amount] StandardCostAmount_CurrencyCode [Currency of IsStocked [Is stocked] [Z Organization_Organizationld [Organization ID] ](media/22c1d8a6496d190fa72b081a511dce79.png)

![Machine generated alternative text: SOURCE ENTITY Sellable released products Source \> CDS Search SOURCE FIELD CDS ENTITY Product Destinatio MAP TYPE SellingUnitPrice_CurrencyCode [Currency of [Z Description [Description] Name [Name] [Z Productld [Product ID] ProductType [Product type] DefaultSellingQuantity_lJOM [Unit of Measure of None SellingUnitPrice [Selling unit price] StandardCostAmount [Standard cost amount] IsStocked [Is stocked] None None DESTINATION ENTITY products DESTINATION FIELD [Z transactioncurrencyid.isocurrencycode [Currency (Currency Code)] [Z description [Description] [Z name [Name] [Z productnumber [Product ID] producttypecode [Product Type] [Z defaultuomid.name [Default IJnit (Name)] [Z defaultuomscheduleid.name [Unit Group (Name)] price [List Price] currentcost [Current Cost] isstockitem [Stock Item] quantitydecimal [Decimals Supported] msdynce_ismaintainedexternally [Is Maintained Externally] ](media/72292e8c28b64880d28810097e3a1f14.png)
