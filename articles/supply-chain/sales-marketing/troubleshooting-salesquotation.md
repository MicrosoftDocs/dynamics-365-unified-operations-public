---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with Sales Quotations.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SalesQuotationTable, SalesQuotationTableListPage
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
# Troubleshoot Sales Quotations 

This topic describes how to fix common issues that you might encounter while working with Sales Quotations.

##  Error “Update not allowed for field Quantity” For an ItemType = “Service”. Unable to make changes on “SalesQty” on a Sales Quotation with an item that is not stocked. 
This issue occurs when sales quantity ('SalesQty' field) on a sales quotation line that is not stocked, is tried to be set.

**Resolution**
It is not possible to set sales quantity for products that are service items. For example, if you offer a service to install an item, it cannot be recorded as a quantity as it is not a physical item but rather a service.

##

## Additional resources

[Get started with Sales Orders](get-started.md)

