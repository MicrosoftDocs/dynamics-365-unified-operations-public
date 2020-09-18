---
# required metadata

title: Troubleshoot Product Information
description: This topic describes how to fix issues that you might encounter while working with Product Information.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Information
This topic describes how to fix common issues that you might encounter while working with Product Information.

##  Unable to rename a released product 
		
**Resolution**
It is not possible to rename item numbers for released products as it would lead to corrupted data. We only allow it if and only if you need to repair data corruption caused by a previous rename of the primary key of a released product, as we indicate in https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features#finance-and-operations-1000-with-platform-update-24

## Flushing Principle is not being defaulted from the product onto the BOM Line.
When adding an item to a BOM Line, the system is not defaulting the Flushing principle information previously set up in the Item, i.e. the flushing principle from the iteam does not show up on the BOM Line form.

**Resolution**
If a Flushing Principle is specified on the BOM line, then that will be the flushing principle. Otherwise, though the Flushing principle from the item does not show up on the BOM Line, the Flushing principle that is set on the Item will be used for processing if the Flushing principle is blank/not set on the BOM line.

This design cannot be changed, because it might be breaking some customizations which are assuming the current behavior.

## It is possible save duplicate barcode for different items or same item with different dimension.
Barcode uniqueness is not enforced currently. Putting this restriction on the metadata would be a breaking change - and we do have evidence that there are customers who will be broken by this change. We will consider a broader design change to enable this feature in the future.

## Error when editing Items record templates: 'The warehouse location cannot be created because the item is not stocked. To stock items, the Stocked product option on the associated item model group must be selected'
This happens when creating template for items that are not stocked, using the Options > Record info > Company accounts template button.

**Resolution**
Creating product templates require extra product-specific logic and so the generic Company accounts template button cannot be used for this purpose. One must used the following button in the Action pane: Product > New > Template > Create shared template instead.


