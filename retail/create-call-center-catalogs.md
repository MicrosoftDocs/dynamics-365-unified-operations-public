---
# required metadata

title: Create a call center catalog
description: This article provides an overview of the process for creating a catalog for a call center. 
author: josaw1
manager: AnnBe
ms.date: 2015-12-03 22 - 20 - 12
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 16212
ms.assetid: c9d1b9df-82e8-4b3a-a13c-166df8b9718e
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create a call center catalog

This article provides an overview of the process for creating a catalog for a call center. 

In a call center, you can use product catalogs to identify the products that you want to offer to customers. Call centers typically use printed catalogs. The design and production of a printed catalog is handled outside Microsoft Dynamics 365 for Operations. However, you can create and store a digital form of a catalog in Retail and commerce in Dynamics 365 for Operations by using the same forms that you use to set up online retail catalogs. Before you can create a catalog, you must set up product assortments and assign the assortments to a call center. You then add products to the catalog by selecting products from these assortments. After products have been added to the catalog, and the catalog is complete, you must validate the catalog to verify the data. You must then submit the catalog for review and approval. After the catalog is approved, it can be published. When a call center catalog is created, you can take a snapshot of the catalog data at the time when the catalog is published. This snapshot functionality lets you access a particular version of the catalog even if the catalog is later changed and updated. Call center catalogs can also be set up to include the following optional features.

-   **Source codes** – Codes that are used to track the customer response to particular catalog mailings.
-   **Free products** – Products that are included in a customer's order at no additional charge. These products are automatically added to the order when the source code for the catalog is entered into the order.
-   **Scripts** – Texts that a call center worker reads to a customer when a sales order is being created. Scripts can include greetings or purchase suggestions.
-   **Upsell or cross-sell items** - Items that are displayed as a suggestion when a specific product is added to the order.

These options must be set up before the catalog is approved and published.

## Prerequisites
The following tasks must be completed before you start:

-   Set up products and product assortments.
-   Set up retail products.
-   Set up an assortment.
-   Create a call center.
-   Set up a call center.
-   Add the call center to an organization hierarchy.
-   Create or modify an organization hierarchy.

## Create a catalog
You must first create a catalog, add products to the catalog, and then review and update the attributes for the products.

## Validate the catalog
After you've finished setting up the catalog, you must validate it. The validation process verifies that the data that is required for channel attributes and product attributes is complete and valid, and that the catalog can be published.

## Submit the catalog for review and approval
After a catalog is validated, you can submit the catalog for review and approval. A catalog must be approved before it can be published. You can configure a workflow so that catalogs either are automatically approved or require manual approval.

## Optional: Add source codes, free products, and scripts
You can also add the following items to a call center catalog. These items are optional.

-   **Source codes** can be used by companies that provide printed catalogs to track the customer response to particular catalogs. Source codes are often printed on the back of a catalog and are entered into the sales order when a customer makes a purchase. To add a source code to the catalog, you must first create a target market. The target market is usually mapped to an owned or rented mailing list.
-   **Free products** are promotional items that are included free of charge with the customer's order when the catalog is referenced.
-   **Scripts** can be used to guide the worker's interactions with customers in the context of a catalog or a product within a catalog.

## Publish the catalog
By publishing a catalog for a call center, you finalize the product information in the catalog. Publication also indicates that the catalog is ready for any additional actions that you want to perform. For example, you can create a printed catalog. You can publish your catalogs manually, or you can use a batch process to publish according to a schedule. Before you can publish a catalog, the catalog must be validated and approved. To change the catalog after it's published, you can retract the catalog and then republish it.

