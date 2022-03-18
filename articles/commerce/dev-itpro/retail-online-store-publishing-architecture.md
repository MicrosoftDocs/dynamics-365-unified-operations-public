---
title: Publish an online store catalog
description: This topic contains conceptual information to understand how catalogs are published from the Commerce module to an online store.
author: mugunthanm
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 2020-02-28
ms.dyn365.ops.version: AX 10.0.10
---

# Publish an online store catalog

[!include [banner](../includes/banner.md)]

This topic contains conceptual information to understand how catalogs are published from the Commerce module to an online store.

## Publish an online store catalog

A product catalog lets you identify the products that you want to offer in your online stores. When you create a catalog, you identify the online stores where the products will be offered, add products, and enhance the product offerings by adding merchandising details. After the catalog is approved, you publish it to make products available in the online store. Before you can publish a product catalog, you must complete the following setup tasks:

1. Set up products, and configure hierarchies, assortments, and variants.
2. Set up product catalogs, and configure attribute groups and workflow.

After you've completed these steps, you're ready to publish the online store catalog.

1. Finances and Operations reads the product tables in the Commerce database.
2. Async Server synchronizes all products in the channel database.
3. The CRT/Publishing Connector creates a *listing*. A listing is an instance of a product for a channel at a given point in time. For example, you have a product that is named “jeans”, and this product has a variant that is named “red”. In this case, the system creates a listing for “red jeans”.
4. The system determines whether any new attributes were added for the listing. If a new attribute were added (for example, if the “red jeans” listing includes a new attribute that is named **texture**, and this attribute is marked as **Included** at the channel level), the system creates a custom site column for that attribute. The system also creates a new rule for the list item and completes the process in SharePoint by creating a new row for the “red jeans” listing.
5. The CRT records the publishing status for the listing.
6. Async Server synchronizes the publishing status of the listing with all other publishing statuses. The status is either **Published** or **Error**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
