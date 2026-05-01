---
title: Publish an online store catalog
description: This article provides an overview of how catalogs are published from the Commerce module to a Microsoft Dynamics 365 Commerce online store.
author: josaw1
ms.date: 02/19/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-28
ms.custom: 
  - bap-template
---

# Publish an online store catalog

[!include [banner](../includes/banner.md)]

This article provides an overview of how to publish catalogs from the Commerce module to a Microsoft Dynamics 365 Commerce online store.

## Publish an online store catalog

A product catalog lets you identify the products that you want to offer in your online stores. When you create a catalog, you specify the online stores where you want to offer the products. You add products and enhance the product offerings by adding merchandising details. After you approve the catalog, you publish it to make products available in the online store. Before you can publish a product catalog, you must complete the following setup tasks:

1. Set up products, and configure hierarchies, assortments, and variants.
1. Set up product catalogs, and configure attribute groups and workflow.

After you complete these steps, you're ready to publish the online store catalog. When you publish, the following steps occur:

1. The Commerce system reads the product tables in the Commerce database.
1. Async Server synchronizes all products in the channel database.
1. The CRT/Publishing Connector creates a listing, which is an instance of a product for a channel at a given point in time. For example, you have a product that is named "jeans," and this product has a variant that is named "red." In this case, the system creates a listing for "red jeans."
1. The system determines whether you added any new attributes for the listing. If you add a new attribute (for example, if the "red jeans" listing includes a new attribute that is named **texture**, and you mark this attribute as **Included** at the channel level), the system creates a custom site column for that attribute. The system also creates a new rule for the list item and completes the process in SharePoint by creating a new row for the "red jeans" listing.
1. The CRT records the publishing status for the listing.
1. Async Server synchronizes the publishing status of the listing with all other publishing statuses. The status is either **Published** or **Error**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
