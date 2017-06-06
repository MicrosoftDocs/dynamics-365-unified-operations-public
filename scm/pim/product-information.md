---
# required metadata

title: Formula designer
description: The product information management works with a common product definition, categorization, and identification across all legal entities as well as specific configurations of a product to fit into the business processes. 
author: cvocph 
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ?????
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
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

Product information is the backbone of supply chain and retail applications across all industries. It refers to processes and technologies that focus on centrally managing information about products, for example, across supply chains, it is crucial to have common product definitions, documentations, attributes, and identifiers. In the different modules of a business solution, product specific information and configuration are needed to manage the business processes that are related to specific products, or product families, or product categories. 
 
## Product definition
 
A product is primarily defined by a product number, a name and a description. Additional relevant data needed to describe a product or service are:
 
-	Product type: Item or Service
-	Product subtype: Distinct products or product masters
-	Definition of the product variant model
     -	Product dimensions and dimension groups
     -	Product nomenclature
     -	Product configuration models
-	Association of the product to one or multiple categories
- Definition of the product and category attributes   
- Product images
- Attachments
-	Units of measures and related conversions
-	Translations to all names and descriptions
 
## Distribution, export and import of product data
 
The product definition can be created in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. It can also be imported from Product lifecycle management (PLM), or Product data management (PDM), or Product information management (PIM) systems. When more than one instance of Finance and Operations are used, it is common to use one instance as the master of the product data for other instances. This is supported by a large set of data entities that allow to export and import product definition data from one instance to another. 
 
To support the distribution of product data to many instances of operations, Finance and ODynamics 365 offers the usage of the Common Data Service. The product definitions are exported from an instance of Dynamics 365 for operations to the Common Data Service, where they can be used to provision other business applications, for example Dynamics 365 for Sales with product data. 
 
Note that in dynamic and agile organizations, product information data change on a daily basis, and the maintenance of accurate and actual product data is a mission critical business process on its own. 
 
## Product masters and product variants
In an agile world, where products have to be adapted to customer needs fast, product definitions specify a set of products instead of a distinct products. In Microsoft Dynamics 365 for operations those generic products are called Product Masters. Product masters hold the definition and rules of how distinct products are described and behave in the  business processes. Based on these definitions, distinct products can be generated, the so called product variants. 
 
In Microsoft Dynamics 365 for finance and operations, a product master is associated to a product dimension group and a configuration technology, do specify the business rules. The product dimensions - Color, Size, Style and Configuration - are a specific set of attributes that can be used throughout the application to define and track specific behaviors of the related products, and help to search and identify the products. 
 
 ## Configuration technologies
 
There are 3 configuration technologies to choose from:
 
1.	The predefined variants are defined by predefined product dimensions. The variant definition includes the specific definition of the valid combination of dimensions, like color, style and size. Each combination results in a distinct product variant.
2.	The dimension based configuration is typically used in manufacturing scenarios allows to use the configuration dimension in the definition of the Bill of material. Once a specific configuration is selected, a the system uses the subset of the Bill of material lines that are valid for the configuration for planning and production. This concept is also called "Global BOM" as it uses one common bill of material for all configurations of a product. 
3.	The constraint based configuration is using a product configuration model to describe all possible attributes and components that are needed to describe all possible variants of a product in a single model. The constraints of combinations of attributes can be described through regular expressions or table based constraints. Configuration models and Configurators gain more and more importance in product information management and are used across all industries. 
 
The right choice of the configuration technology for a business process is very important, when planning the implementation of Dynamics 365 for operations, as a product cannot be converted from one model to another after the fact. 
 
## Product variant model definition workspace
 
This workspace gives an overview of the product masters and the state of release of the masters and related variants to specific legal entities. 
 
## Released products
 
The products that are released to a specific legal entity are called released products. Products can be released in bulk to one or many legal entities at a time. As various properties and attributes of the products may need to be added per legal entity, a workspace called **Released product maintenance** is designed to monitor and complete the recently released products in each legal entity or the suborganizations of that legal entity. 
 
### Released product maintenance workspace
You can configure the workspace from the **Configure my workspace** menu item by selecting a category hierarchy and category on which the workspace is filtered. You can also define the time fences for **Recently released products** and **Stopped released products** in days to adjust the relevant product data in the workspace.
 
The workspace consists of a summary of tiles and two lists. The open cases list shows product change cases that have products in the selected product category hierarchy that are not completed and closed. The recently released list shows products that have been released within the time fence set in the workspace configuration. For each of the items in the list, the validation is run and validation status is shown. This indicates that the required configurations for the legal entity may not be complete. From the list, you can directly access the **Released product details**, the **Product attribute maintenance**, the **Product category maintenance**, the **Default order settings**, and the **Text translations** pages to complete the required configuration of the product. 
 
### Manually creating a new released product
It is possible to manually create a released product in a single run. Obviously, it depends on the business processes of an organization and weather this function should be used. It creates a new product and releases it automatically to the current legal entity. You can cretae a new product by clicking **Released products** in the **Released product maintenance** workspace or in the **Released product** listpage. 
 
 





