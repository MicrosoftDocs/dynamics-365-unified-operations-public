---
# required metadata

title: Product dimensions
description: There are five product dimensions -  Color, Configuration, Size, Style and Version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.
author: cvocph
manager: tfehr
ms.date: 08/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductDimension, EcoResProductDimensionGroup, EcoResProductMasterDimension, RetailEcoResColor, RetailEcoResSize, RetailEcoResStyle
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac

ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 19171
ms.assetid: 81fa3709-4ab8-4fbf-9806-359892a05985
ms.search.region: Global
ms.search.industry: Retail
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Product dimensions

[!include [banner](../includes/banner.md)]

There are four product dimensions -  Color, Configuration, Size, Style and Version. You combine product dimensions in dimension groups and assign dimension groups to product masters. The combinations of product dimensions determine how product variants are defined.

Product dimensions are characteristics that serve to identify a product variant. You can use combinations of product dimensions to define product variants. You must define at least one product dimension for a product master in order to create a product variant.

## Product variants

Product variants are also referred to as items. An item is a tangible product, which is not the same as a service. It is also possible to define a product master with the Service type. By using the Service type, you can specify product variants that include services. For example, you can specify a product master for Consultancy work and product variants for work that is performed by senior consultants and junior consultants.

## Product dimensions
The following product dimensions are available: Configuration, Color, Size, and Style. A product variant can be generated based on the product dimension values.

Product dimensions values such as Size, Color and Style can be created on the **Size**, **Color** and **Style** pages, which can be accessed from the following locations: **Product information management** &gt; **Setup** &gt; **Dimension and variant Groups** &gt; **Sizes/Colors/Styles**. Product dimension values for the Configuration dimension are typically created using either the Product configurator or the Dimension-based configurator. Product versions are usually created for the specific version as the product evolves in its lifecycle. Product dimensions can also be created and maintained on the **Product dimensions** page, which can be accessed from the following locations:
-   Click **Product information management** &gt; **Products** &gt; **Product masters**. On the **Action Pane**, click **Product dimensions**.
-   Click **Product information management** &gt; **Products** &gt; **All products and product masters**. Select a product master. On the **Action Pane**, click **Product dimensions**.
-   Click **Product information management** &gt; **Released products**. Select a product master. On the **Action Pane**, click **Product**. In the **Product master** group, click **Product dimensions**.

The number of variants that you can create for an item is limited by the number of possible product dimension combinations.

| **Tip**                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------------------------|
| When you use a product on, for example, an order line, you select the product dimensions to identify the product variant that you want to work with. |

## Example
A company sells denim jeans. The item, Jeans, uses the Color and Size product dimensions. The jeans are sold in three different colors and six different sizes. Colors: Blue, Black, Brown Sizes: XS, S, M, L, XL, XXL Not all sizes are available in all the three colors. If all combinations were available, it would create 18 different types of jeans. In this example, only the following nine product variant combinations are produced.

| Color | Size |
|-------|------|
| Blue  | XS   |
| Blue  | S    |
| Blue  | M    |
| Black | M    |
| Black | L    |
| Black | XL   |
| Brown | L    |
| Brown | XL   |
| Brown | XXL  |

## Product dimension version

Version is a product dimension that is intended to help you maintain and track multiple versions of a product throughout the supply chain. Version tracking is essential to the success of manufacturers operating in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and increased focus on product safety. 
	 
As a standard product dimension, version will behave similarly to the existing product dimensions of size, style, color and configuration, which means that you could also choose to use it for purposes other than tracking product versions.

### How to enable Product dimension version
	
	Enable feature "Product dimension version"
	Enable configuration key "Product dimension - Version"
	
	
### Areas where Version is not supported:
	
	The following areas do not have Version dimension uptake, because introducing Version would cause breaking changes on the corresponding artefacts:
		1. Cost object monthly statement
		2. Cost Object statement cache
		3. MCR Sales statistics per item
		4. Vendor catalogs
		5. EcoResProductDimensionGroupEntity 
	
	Dynamics 365 Commerce order creation and order processing (Point of Sale, Call Center and E-commerce orders) will not support Version. There is no confirmed timeline as to when Commerce orders will be enhanced to support the Version dimension.
  
	### Functional characteristics of version
	
	The product dimension version works similarly as the other product dimensions Size, Color, Style and Configuration. But due to its specific nature, the fact that is intended to maintain and track multiple versions of a product is has a slight different behavior. These are the specifics of it and the reasoning (we'd love your feedback on it!):
	
	- There is no version group: differently from size/color and style which have color group/size group/style group, a version group does not exist. The use of the groups is to predefine the values that can be applicable so that when e.g. a color group is assigned to a product, the product can take all the colors in the color group. This idea does not  make sense for version - as the versions that a product will take are not predefined when the product is created. The versions will be created during the lifecycle of the product, a new version will be created when it is considered needed. Note that usually it is a change in version (and not a new product) when the form, fit and function of the product remain the same.
	- Product variant suggestions working as it currently does: it is expected that there are no changes to the process of creating and releasing versioned products. The process would be the following: when creating a versioned product the first version (e.g. V-1) will be created as a product dimension and the variant(s) will be released. As the product changes and a new version is needed, then the new version value (V-2) will be added and the needed variants will be released. It is not expected that all the versions (V-1, V-2, V-3) are not created beforehand for the product. 


 
IMPORTANT: By enabling this, and using the version dimension in any functionalities could potentially not work as expected if there are any solutions installed that reference the Inventory dimensions. The ISV that owns the solution would be able to determine this.
	
	### Before turning on the Version dimension: 
	
	When enabling the version dimension, potentially functionality could be broken or not work as expected if you have other solutions installed, that are having any customizations involving Inventory Dimensions.
	
	Those solutions must be updated to include the Version dimension in their references to the Inventory Dimensions, in order for the Version dimension to be fully functional. 
	
	List of potential ways and patterns to look out for enabling the Version dimension in extended solutions:
	
		1. References to the Inventory dimensions:
		Look out for references to the Inventory Dimensions, i.e. where the dimensions are referenced specifically. References to InventDimId should work out of the box, but look out for references to Style or Color.
			i. API calls in extended classes
			ii. All references to specific inventory dimensions in extension code need to float the Version dimension also along with the Style, Color, Size dimensions.
			
		2. References to obsoleted API calls:
		With the introduction of the Version dimension, we have tried to minimize obsoletion of APIs as much as possible. Only certain points where it was absolutely necessary, APIs have been obsoleted in a way that they give a warning when the Version configuration key is turned on. Those are the API calls that need to be fixed in extended solutions before turning Version on. Here is the list of version specific obsoleted APIs:
			1. RetailTransactionServiceInventory::getProductRecordId
			2. EcoResProductNumberIdentifiedProductVariantEntity::find
			3. EGAISAlcoholProduction_RU::findByItemDim
			4. PCVariantConfiguration::findByProductMasterAndDimensions
			
		3. Maps
		For any Maps that have the Inventory Dimensions, corresponding relation mapping to these maps must be updated to include the Version dimension. Look out for:
			i. Tables in the extended model or table extensions where the fields include Inventory Dimensions.
		
		4. Functionality
		Most importantly, any customizations  that involve the inventory dimensions must be assessed so they can work accordingly in conjunction with the Version dimension.
		
		5. Retail functionality
		Version dimension floats through retail code on standard, however it is not supported at this time by Commerce.  This follows a similar approach as the Config dimension right now in Commerce.   



