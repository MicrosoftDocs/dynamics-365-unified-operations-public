---
# required metadata

title: Troubleshoot sales quotations
description: This topic describes how to fix issues that you might encounter while you work with sales quotations.
author: SmithaNataraj
manager: tfehr
ms.date: 09/16/2020
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
ms.search.validFrom: 2020-9-16
ms.dyn365.ops.version: Release 10.0.14

---
# Troubleshoot sales quotations

This topic describes how to fix issues that you might encounter while you work with sales quotations.

## I can't change the sales quantity of a sales quotation for a service item.

### Issue description

If you try to set a sales quantity (**SalesQty** field) for an item of the *Service* type on a sales quotation line, you will receive the following message: "Update not allowed for field Quantity."

### Issue resolution

You can't set a sales quantity for products that are service items. For example, if you offer a service to install an item, it doesn't make sense to record a quantity, because there is no physical item. There is only a service.

