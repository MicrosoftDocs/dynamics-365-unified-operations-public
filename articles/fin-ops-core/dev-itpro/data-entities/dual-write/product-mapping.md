---
title: Unified product experience
description: Learn about the integration of product data between finance and operations apps and Dataverse, including a table outlining various templates.
author: t-benebo
ms.author: ramasri
ms.topic: article
ms.date: 05/24/2024
ms.reviewer: twheeloc
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2019-07-15
---

# Unified product experience

[!include [banner](../../includes/banner.md)]

When a business ecosystem is made up of Dynamics 365 applications, such as Finance, Supply Chain Management, and Sales, businesses often use these applications to source product data. This is because these apps provide a robust product infrastructure complemented with sophisticated pricing concepts and accurate on-hand inventory data. Businesses who use an external Product Lifecycle Management (PLM) system for sourcing the product data can channelize products from finance and operations apps to other Dynamics 365 apps. The unified product experience brings the integrated product data model into Dataverse, so that all application users, including Power Platform users, can take advantage of the rich product data coming from finance and operations apps.

The following image shows the product data model from Dynamics 365 Sales.

![Data model for products in CE.](media/dual-write-product-4.jpg)

The following image shows the product data model from finance and operations apps.

![Data model for products in finance and operations apps.](media/dual-write-products-5.jpg)

These two product data models are integrated into Dataverse as shown in the following image.

![Data model for products in Dynamics 365 apps.](media/dual-write-products-6.jpg)

The dual-write table maps for products are designed to flow data only one way, from finance and operations apps to Dataverse in near-real time. However, the product infrastructure is open to make it bidirectional if necessary. Although you can customize it, you do so at your own risk, because Microsoft doesn't recommend this approach.

## Templates

Product information contains all the information that's related to the product and its definition, such as the product dimensions or the tracking and storage dimensions. As the following table shows, a collection of table maps is created to sync products and related information.

| Finance and operations apps | Other Dynamics 365 apps | Description |
|---|---|---|
| [All products](mapping-reference.md#138) | msdyn\_globalproducts | The all products table contains all the products that are available in finance and operations apps, both released products and nonreleased products. |
| [CDS released distinct products](mapping-reference.md#213) | Product | The **Product** table contains the columns that define the product. It includes individual products (products with subtype product) and product variants. |
| [Colors](mapping-reference.md#170) | msdyn\_productcolors | |
| [Configurations](mapping-reference.md#171) | msdyn\_productconfigurations | |
| [Default order settings](mapping-reference.md#172) | msdyn\_productdefaultordersettings | |
| [DV released distinct products](mapping-reference.md#242) | Product | The **DV released distinct products** entity is a simpler version of the **CDS released distinct products** entity. It contains only variant-specific information and relies on Dataverse plugins to automatically set relevant product master information from **msdyn\_sharedproductdetails** to **Product**. It's available in the Dynamics 365 Supply Chain Extended v2.3.4.294 solution. |
| [DV released products](mapping-reference.md#243) | msdyn\_sharedproductdetails | The **DV released products** entity is a simpler version of the **Released products V2** entity. It contains product master–relevant information and relies on Dataverse plugins to automatically update relevant products from **msdyn\_sharedproductdetails** to **Product**. It's available in the Dynamics 365 Supply Chain Extended v2.3.4.294 solution. |
| [Product categories](mapping-reference.md#166) | msdyn\_productcategories | The product category table contains each product category and information about its structure and characteristics. |
| [Product category assignments](mapping-reference.md#167) | msdyn\_productcategoryassignments | The product category assignments table can be used to assign a product to a category. |
| [Product category hierarchies](mapping-reference.md#168) | msdyn\_productcategoryhierarchies | You use product hierarchies to categorize or group products. The category hierarchies are available in Dataverse through the Product category hierarchy table.|
| [Product category hierarchy roles](mapping-reference.md#169) | msdyn\_productcategoryhierarchyroles | Product hierarchies can be used for different roles in Dynamics 365 finance and operations apps. They specify which category is used in each role where the product category role table is used. |
| [Product default order settings V2](mapping-reference.md#175) | msdyn\_productspecificdefaultordersettings | |
| [Product dimension groups](mapping-reference.md#173) | msdyn\_productdimensiongroups | The product dimension group defines which product dimensions define the product. |
| [Product master colors](mapping-reference.md#187) | msdyn\_sharedproductcolors | The **Shared product color** table indicates the colors that a specific product master can have. This concept is migrated to Dataverse to keep data consistent. |
| [Product master configurations](mapping-reference.md#188) | msdyn\_sharedproductconfigurations | The **Shared product configuration** table indicates the configurations that a specific product master can have. This concept is migrated to Dataverse to keep data consistent. |
| [Product master sizes](mapping-reference.md#190) | msdyn\_sharedproductsizes | The **Shared product size** table indicates the sizes that a specific product master can have. This concept is migrated to Dataverse to keep data consistent. |
| [Product master styles](mapping-reference.md#191) | msdyn\_sharedproductstyles | The **Shared product style** table indicates the styles that a specific product master can have. This concept is migrated to Dataverse to keep data consistent. |
| [Product Number Identified Barcode](mapping-reference.md#164) | msdyn\_productbarcodes | Product bar codes are used to uniquely identify products. |
| [Product specific unit conversions](mapping-reference.md#176) | msdyn\_productspecificunitofmeasureconversions | |
| [Released products V2](mapping-reference.md#189) | msdyn\_sharedproductdetails | The **msdyn\_sharedproductdetails** table contains the columns from finance and operations apps that define the product, and that contain the product's financial and management information. |
| [Sizes](mapping-reference.md#174) | msdyn\_productsizes | |
| [Storage dimension groups](mapping-reference.md#177) | msdyn\_productstoragedimensiongroups | The product storage dimension group represents the method that's used to define the placement of the product in the warehouse. |
| [Styles](mapping-reference.md#178) | msdyn\_productstyles | |
| [Tracking dimension groups](mapping-reference.md#179) | msdyn\_producttrackingdimensiongroups | The product tracking dimension group represents the method that's used to track the product in inventory. |
| [Units](mapping-reference.md#219) | uoms | |
| [Unit conversions](mapping-reference.md#199) | msdyn\_unitofmeasureconversions | |

## Integration of products

In this model, the product represents the combination of two tables in Dataverse: **Product** and **msdyn\_sharedproductdetails**. Whereas the first table contains the definition of a product (the unique identifier for the product, the product name, and the description), the second table contains the columns that are stored at the product level. The combination of these two tables is used to define the product according to the concept of the stockkeeping unit (SKU). Each released product has its information in the mentioned tables (**Product** and **Shared Product Details**). To keep track of all products (both released and nonreleased), the **Global products** table is used.

Because the product is represented as a SKU, the concepts of distinct products, product masters, and product variants can be captured in Dataverse in the following way:

- **Products with subtype product** are products that are defined by themselves. No dimensions have to be defined. An example is a specific book. For these products, one row is created in the **Product** table, and one row is created in the **msdyn\_sharedproductdetails** table. No product family row is created.
- **Product masters** are used as generic products that hold the definition and rules that determine the behavior in business processes. Based on these definitions, distinct products that are known as product variants can be generated. For example, T-shirt is the product master, and it can have Color and Size as dimensions. Variants can be released that have different combinations of these dimensions, such a small blue T-shirt or a medium green T-shirt. In the integration, one row per variant is created in the product table. This row contains the variant-specific information, such as the different dimensions. The generic information for the product is stored in the **msdyn\_sharedproductdetails** table. (This generic information is stored in the product master.) The product master information is synced to Dataverse as soon as the released product master is created (but before variants are released).
- **Distinct products** refer to all the products with subtype product and all the product variants.

![Data model for products.](media/dual-write-product.png)

When the dual-write functionality is enabled, the products from finance and operations apps are synced to other Dynamics 365 products in a **Draft** state. The price lists are sorted alphabetically by name, and the products are added to the first price list that has the same currency that's used in the customer engagement app. In other words, the products are added to the first price list in a Dynamics 365 app that matches the currency of your legal table where the product is released in a finance and operations app. If there's no price list for the currency, a price list is automatically created, and the product is assigned to it.

The current implementation of the dual-write plugins associates the default price list with the unit to look up the currency that's associated with the finance and operations app. It finds the first price list in the customer engagement app. (Once again, the price lists are sorted alphabetically by name.) To set a default price list for a specific currency when you have multiple price lists for that currency, you must update the price list name so that it's earlier in alphabetical order than any other price lists for that same currency. If there's no price list for the currency, a new price list is created.

By default, products from finance and operations apps are synced to other Dynamics 365 apps in a **Draft** state. To sync a product in an **Active** state, so that you can use it directly in sales order quotations, you must go to **System** \> **Administration** \> **System administration** \> **System settings**, and then, on the **Sales** tab, set **Create products in active state** to **Yes**.

When products are synced, you must enter a value in the **Sales unit** field in the finance and operations app, because this field is mandatory in Dynamics 365 Sales.

The creation of product families from Dynamics 365 Sales isn't supported with the dual-write synchronization of products.

The synchronization of products is done from the finance and operations app to Dataverse. Therefore, although the values in the product table columns can be changed in Dataverse, those values are overwritten when the synchronization is triggered (that is, when a product column is modified in a finance and operations app).

### New approach for integration of products

As of Dynamics 365 Supply Chain Management version 10.0.39 and Dynamics 365 Supply Chain Extended v2.3.4.294, a new approach is introduced for product synchronization, to help improve overall performance.

The new data entities, [DV released distinct products](mapping-reference.md#242) and [DV released products](mapping-reference.md#243), contain only the information that's synced to Dataverse. Therefore, the data entities are more performant because they have fewer joins and data sources. The Dataverse plugins take care of updating the relevant product information from **msdyn\_sharedproductdetails** to **Product**.
 
As is mentioned in [Sync on-demand with the Supply Chain Management pricing engine](../../../fin-ops/data-entities/pricing-engine.md), Dynamics 365 Sales uses the Dynamics 365 Supply Chain Management pricing engine for price-related calculations. Therefore, UnitCost and SalesPrice are no longer needed or synced to Dataverse.

To start to use this new approach, verify that you use Dynamics 365 Supply Chain Management version 10.0.39 or older, and that the Dynamics 365 Supply Chain Extended v2.3.4.294 solution is installed on Microsoft Power Platform. The old dual-write maps, [CDS released distinct products](mapping-reference.md#213) and [Released products V2](mapping-reference.md#189), should be stopped, and the new maps should be started. Because the plugins are designed to work with the new maps, they're automatically triggered and run only when the new maps are activated.

If you stop the new [DV released distinct products](mapping-reference.md#242) and [DV released products](mapping-reference.md#243) maps and start the old maps, the old approach for product synchronization is used.

When you run initial synchronization, the [DV released products](mapping-reference.md#243) map should be run first, and then the [DV released distinct products](mapping-reference.md#242) should be run.

Finance and operations apps | Customer engagement apps |
---|---
[CDS released distinct products](mapping-reference.md#213) | Product |
[Released products V2](mapping-reference.md#189) | msdyn\_sharedproductdetails |
[DV released distinct products](mapping-reference.md#242) | Product |
[DV released products](mapping-reference.md#243) | msdyn\_sharedproductdetails |
[All products](mapping-reference.md#138) | msdyn\_globalproducts |

## Product dimensions

Product dimensions are characteristics that identify a product variant. The four product dimensions (Color, Size, Style, and Configuration) are also mapped to Dataverse to define the product variants. The following illustration shows the data model for the Color product dimension. The same model is applied to Size, Style, and Configuration.

![Data model for product dimensions.](media/dual-write-product-two.png)

Finance and operations apps | Customer engagement apps |
---|---
[Colors](mapping-reference.md#170) | msdyn\_productcolors
[Sizes](mapping-reference.md#174) | msdyn\_productsizes
[Styles](mapping-reference.md#178) | msdyn\_productstyles
[Configurations](mapping-reference.md#171) | msdyn\_productconfigurations

When a product has different product dimensions (for example, a product master has Size and Color as product dimensions), each distinct product (that is, each product variant) is defined as a combination of those product dimensions. For example, product number B0001 is an extra-small black T-shirt, and product number B0002 is a small black T-shirt. In this case, the existing combinations of product dimensions are defined. For example, the T-shirt from the preceding example can be extra-small and black, small and black, medium and black, or large and black, but it can't be extra-large and black. In other words, the product dimensions that a product master can take are specified, and variants can be released based on these values.

To keep track of the product dimensions that a product master can take, the following tables are created and mapped in Dataverse for each product dimension. For more information, see [Product information overview](../../../../supply-chain/pim/product-information.md).

Finance and operations apps | Customer engagement apps |
---|---
[Product master colors](mapping-reference.md#187) | msdyn\_sharedproductcolors |
[Product master configurations](mapping-reference.md#188) | msdyn\_sharedproductconfigurations |
[Product master sizes](mapping-reference.md#190) | msdyn\_sharedproductsizes |
[Product master styles](mapping-reference.md#191) | msdyn\_sharedproductstyles |
[Product Number Identified Barcode](mapping-reference.md#164) | msdyn\_productbarcodes |

## Default order settings and product-specific default order settings

Default order settings define the site and warehouse where items are sourced from or stored. They also define the minimum, maximum, multiple, and standard quantities that are used for trading or inventory management, the lead times, the stop flag, and the order promising method. This information is available in Dataverse by using the default order settings and product-specific default order settings entity. For more information about the functionality, see [Default order settings for dimensions and product variants](../../../../supply-chain/production-control/default-order-settings.md).

Finance and operations apps | Customer engagement apps |
---|---
[Default order settings](mapping-reference.md#172) | msdyn\_productdefaultordersettings |
[Product default order settings V2](mapping-reference.md#175) | msdyn\_productspecificdefaultordersettings |

## Unit of measure and unit of measure conversions

The units of measure and the respective conversion are available in the Dataverse following the data model shown in the diagram.

![Data model for unit of measure.](media/dual-write-product-three.png)

The unit of measure concept is integrated between finance and operations apps and other Dynamics 365 apps. For each unit class in a finance and operations app, a unit group is created in a Dynamics 365 app, which contains the units belonging to the unit class. A default base unit is also created for every unit group.

The following are the differences between Dynamics 365 finance and operations apps and Dynamics 365 Sales units of measure:

- In Dynamics 365 finance and operations apps, there are units of measure conversions inter-class and intra-class. It's possible to make changes to the sales unit between different classes (inter-class), provided that an existing conversion exists for the product. 
- In Dynamics 365 Sales, you can only change the unit to another unit in the same group. 
- With the standard integration provided, where a unit group is created in Dynamics 365 Sales for each unit class in Dynamics finance and operations app, then it's not possible to change the sales unit of the product in Dynamics 365 Sales to another unit in a different group. This is a restriction in Dynamics 365 Sales. This means that it's not possible to do an inter-class conversion in finance and operations apps and sync it to Dynamics 365 Sales. 
- If the scenario for doing an inter-class unit conversion in finance and operations apps and then syncing to Dynamics 365 Sales is needed, the default implementation must be changed. All the units from finance and operations apps must be synced to a single unit group in Dynamics 365 Sales that represents the finance and operations unit class. This synchronization can be achieved by customizing the dual-write mapping template for units and mapping msdyn\_externalunitclassname to a fixed value instead of UNITCLASS. 

Finance and operations apps | Customer engagement apps |
---|---
[Product specific unit conversions](mapping-reference.md#176) | msdyn\_productspecificunitofmeasureconversions |
[Units](mapping-reference.md#219) | uoms
[Unit conversions](mapping-reference.md#199) | msdyn\_unitofmeasureconversions

## Initial synchronization of units data matching between finance and operations apps and Dataverse

### Initial synchronization of units

When dual-write is enabled, units from finance and operations apps are synced to other Dynamics 365 apps. For unit groups that are synced from finance and operations apps in Dataverse, a flag is set to indicate that they're "Externally maintained."

### Matching units and unit classes/groups data from finance and operations apps and other Dynamics 365 apps

First, it's important to note that the integration key for unit is msdyn\_symbol. Therefore, this value must be unique in Dataverse or other Dynamics 365 apps. In other Dynamics 365 apps, it's the pair "Unit group ID" and "Name" that define the uniqueness of a unit, you need to consider different scenarios for matching unit data between finance and operations apps and Dataverse.

For units matching/overlapping in finance and operations apps and other Dynamics 365 apps:

+ **The unit belongs to a unit group in other Dynamics 365 apps that corresponds to the associated unit class in finance and operations apps.** In this case, the msdyn\_symbol column in other Dynamics 365 apps must be filled in with the unit symbol from finance and operations apps. Therefore, when the data is matched, the unit group is set as "Externally maintained" in other Dynamics 365 apps.
+ **The unit belongs to a unit group in other Dynamics 365 apps that doesn't correspond to the associated unit class in finance and operations apps. (There's no existing unit class in finance and operations apps for the unit class in other Dynamics 365 apps.)** In this case, the msdyn\_symbol column must be filled in with a random string. This value must be unique in other Dynamics 365 apps.

For units and unit classes in finance and operations apps not existing in other Dynamics 365 apps:

As part of dual-write, the unit groups from finance and operations apps and the corresponding units are created and synced in other Dynamics 365 apps and Dataverse, and the unit groups are set as "Externally maintained." No extra bootstrapping effort is required.

For units in other Dynamics 365 apps that don't exist in finance and operations apps:

The msdyn\_symbol column must be filled in for all units. The units can always be created in finance and operations apps in the corresponding unit class (if it exists). If the unit class doesn't exist, you must first create the unit class that matches the other Dynamics 365 apps unit group. (Note that you can create a unit class in finance and operations apps only through extension if you're extending the enum.) You can then create the unit. The unit symbol in finance and operations apps must be the msdyn\_symbol that was previously specified in other Dynamics 365 apps for the unit.

## Product policies: dimension, tracking, and storage groups

The product policies are sets of policies that are used to define products and their characteristics in inventory. The product dimension group, product tracking dimension group, and storage dimension group can be found as product policies.

Finance and operations apps | Customer engagement apps |
---|---
[Product dimension groups](mapping-reference.md#173) | msdyn\_productdimensiongroups |
[Storage dimension groups](mapping-reference.md#177) | msdyn\_productstoragedimensiongroups |
[Tracking dimension groups](mapping-reference.md#179) | msdyn\_producttrackingdimensiongroups |

## Product hierarchies

Finance and operations apps | Customer engagement apps |
---|---
[Product category assignments](mapping-reference.md#167) | msdyn\_productcategoryassignments |
[Product category hierarchies](mapping-reference.md#168) | msdyn\_productcategoryhierarchies |
[Product category hierarchy roles](mapping-reference.md#169) | msdyn\_productcategoryhierarchyroles |

## Integration key for products

To identify unique products between Dynamics 365 Finance and products in Dataverse, the integration keys are used.
For products, the **(productnumber)** is the unique key that identifies a product in Dataverse. It's composed by the concatenation of: **(company, msdyn_productnumber)**. The **company** indicates the legal entity in finance and operations apps, and **msdyn_productnumber** indicates the product number for the specific product in finance and operations apps.

For users of other Dynamics 365 apps, the product is identified in the UI with the **msdyn\_productnumber** (note that the label of the column is **Product number**). In the product page, both the company and the msydn\_productnumber are shown. However, the (productnumber) column, the unique key for a product, isn't shown.

If you build apps on Dataverse, you should pay attention to using the **productnumber** (the unique product ID) as the integration key. Don't use **msdyn\_productnumber**, because it's not unique.

## Initial synchronization of products and migration of data from Dataverse to finance and operations apps

### Initial synchronization of products

When dual-write is enabled, products from finance and operations apps are synced to Dataverse and customer engagement apps. Products that were created in Dataverse and other Dynamics 365 apps before dual-write was released aren't updated or matched with product data from finance and operations apps.

### Matching product data from finance and operations apps and other Dynamics 365 apps

If the same products are kept (overlapping/matching) in finance and operations apps and in Dataverse and other Dynamics 365 apps, when dual-write is enabled, the synchronization of products from finance and operations apps takes place, and duplicate rows appear in Dataverse for the same product.
To avoid the previous situation, if other Dynamics 365 apps have products that are overlapping/matching with finance and operations apps, then the administrator enabling dual-write must bootstrap the columns **Company** (example: "USMF") and **msdyn\_productnumber** (example: "1234:Black:S") before the synchronization of products takes place. In other words, these two columns in the product in Dataverse must be filled in with the respective company in finance and operations apps to which the product needs to be matched with and with its product number.

Then, when the synchronization is enabled and takes place, the products from finance and operations apps are synced with the matched products in Dataverse and other Dynamics 365 apps. This behavior applies to both distinct products and product variants.

### Migration of product data from other Dynamics 365 apps to finance and operations apps

If other Dynamics 365 apps have products that aren't present in finance and operations apps, the administrator can use **EcoResReleasedProductCreationV2Entity** to import those products into finance and operations apps. Then match the product data from finance and operations apps and other Dynamics 365 apps as previously described.

### Migration of a large amount of product data

Product data is designed to flow from your finance and operations apps to Dataverse. Therefore, you must import product data into your finance and operations app first, and then synchronize it to Dataverse using initial synchronization. Dual-write limits the number of records that you can import during an initial synchronization. If your number of records exceeds this limit, then split the data into batches by applying query filters to the relevant dual-write map.

For more information about filtering data for dual-write, see [Customize table and column mappings](customizing-mappings.md#filter-your-data).

For more information about the constraints of dual-write initial synchronization, see [Considerations for initial synchronization](initial-sync-guidance.md#constraints).

### Install dual-write after a finance and operations environment and a Dataverse environment (with Field Service) is deployed

The following error might appear when you install dual-write in a finance and operations environment with a Dataverse environment (including Field Service): 

> Dynamics365SupplyChainExtended GenericManagedPropertyFailure Microsoft.Crm.CrmException: The evaluation of the current component(name=Attribute, id=29245505-73df-4220-a894-b65c81616fe5) in the current operation (Create) failed during managed property evaluation of condition: Managed Property Name: iscomponentcreationenabled; Component Name: Attribute;

This is a known issue on the installation and if you receive this error, contact Microsoft Support. 

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

