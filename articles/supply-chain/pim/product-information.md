---
# required metadata

title: Product information overview
description: This topic provides information about product information management. Product information management works with a shared product definition, categorization, and identifiers across all legal entities, and also specific configurations of a product, to fit into the business processes. 
author: cvocph 
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EcoResProductMaintainWorkspace, EcoResProductListPage, EcoResProductVariantMaintainWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller

ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: cvocph
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Product information overview

[!include[banner](../includes/banner.md)]

[!include[retail name](../includes/retail-name.md)]

This topic provides information about product information management. Product information management works with a shared product definition, categorization, and identifiers across all legal entities, and also specific configurations of a product, to fit into the business processes. 

Product information is the backbone of supply chain and retail applications across all industries. It refers to processes and technologies that focus on centrally managing information about products (for example, across supply chains). It's crucial that shared product definitions, documentation, attributes, and identifiers be used. In the various modules of a business solution, product-specific information and configuration are required in order to manage the business processes that are related to specific products, product families, or product categories.

## Product definition

A product is primarily defined by a product number, name, and description. However, other data is also required in order to describe a product or service:

- Product type: Item or service
- Product subtype: Distinct products or product masters
- Definition of the product variant model:

     - Product dimensions and dimension groups
     - Product nomenclature
     - Product configuration models

- Association of the product with one or more categories
- Definition of the product and category attributes
- Product images
- Attachments
- Units of measure and related conversions
- Translations for all names and descriptions

## Distribution, export, and import of product data

The product definition can be created in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. It can also be imported from product lifecycle management (PLM), product data management (PDM), or product information management (PIM) systems. When more than one instance of Finance and Operations is used, one instance is typically used as the master of the product data for all other instances. This approach is supported by a large set of data entities that enable the export and import of product definition data from one instance to another.

To support the distribution of product data to many instances, Finance and Operations lets you use the Common Data Service. The product definitions can be exported from an instance of Finance and Operations to the Common Data Service. The product definitions can then be used to provision other business applications, such as Microsoft Dynamics 365 for Sales, with product data.

Note that, in dynamic and agile organizations, product information data changes every day. Therefore, maintenance of accurate and actual product data is a critical business process on its own.

## Product masters and product variants

In an agile world, where products must be quickly adapted to customer requirements, product definitions specify a set of products instead of distinct products. In Microsoft Dynamics 365 for Finance and Operations, those generic products are known as *product masters*. Product masters hold the definition and rules that specify how distinct products are described and behave in business processes. Based on these definitions, distinct products can be generated. These distinct products are known as *product variants*.

In Finance and Operations, a product master is associated with a product dimension group and a configuration technology to specify the business rules. The product dimensions (Color, Size, Style, and Configuration) are a specific set of attributes that can be used throughout the application to define and track specific behaviors of the related products. These dimensions also help users search for and identify the products.

## Configuration technologies

You can choose among three configuration technologies:

- The predefined variants are defined by predefined product dimensions. The variant definition includes the definition of a specific valid combination of dimensions, such as Color, Style, and Size. Each combination produces a distinct product variant.
- The dimension-based configuration is typically used in manufacturing scenarios and lets you use the Configuration dimension in the definition of the bills of materials (BOMs). After a specific configuration is selected, the system uses the subset of BOM lines that are valid for that configuration for planning and production. This concept is also known as *global BOM*, because one shared BOM is used for all configurations of a product.
- The constraint-based configuration uses a product configuration model to describe all possible attributes and components that are required in order to describe all possible variants of a product in a single model. The constraints of combinations of attributes can be described through regular expressions or table-based constraints. Configuration models and configurators become more important in product information management and are used across all industries.

When you plan the implementation of Finance and Operations, it's very important that you choose the correct configuration technology for a business process. A product can't be converted from one model to another after implementation.

## Product variant model definition workspace

The **Product variant model definition** workspace gives an overview of the product masters. It also shows the status of the release of masters and related variants to specific legal entities.

## Released products

The products that are released to a specific legal entity are known as *released products*. Products can be released in bulk to one legal entity or many legal entities at a time. Because various properties and attributes of the products might have to be added per legal entity, the **Released product maintenance** workspace lets you monitor and complete the recently released products in each legal entity, or in the suborganizations of a legal entity.

### Released product maintenance workspace

You can configure the **Released product maintenance** workspace from the **Configure my workspace** menu item. Select a category hierarchy and category to filter the workspace by. To adjust the relevant product data in the workspace, you can also define, in days, the time fences for **Recently released products** and **Stopped released products**.

The workspace consists of a summary of tiles and two lists. The **Open cases** list shows product change cases that have products in the selected product category hierarchy that aren't completed and closed. The **Recently released** list shows products that have been released within the time fence that is set in the workspace configuration. For each item in the list, validation is run, and the validation status is shown. This status might indicate that the required configurations for the legal entity hasn't been completed. From the list, you can directly access the **Released product details**, **Product attribute maintenance**, **Product category maintenance**, **Default order settings**, and **Text translations** pages to complete the required configuration of the product.

### Manually creating a new released product

You can manually create a released product in a single run, depending on the organization's business processes and any rules about whether this function should be used. This function creates a new product and automatically releases it to the current legal entity. To create a new product, click **Released products** in the **Released product maintenance** workspace or on the **Released product** list page.
