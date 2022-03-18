--- 
title: Can't set service item quantity on a sales quotation line 
description: When working with sales quotations, you can't set a sales quantity for products that are service items, because there are no physical items to be counted. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
ms.search.form: SalesQuotationTable, SalesQuotationTableListPage
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Can't change the sales quantity of a service item on a sales quotation line

## Symptoms

If you try to set a sales quantity (**SalesQty** field) for an item of the *Service* type on a sales quotation line, you will receive the following message:

> Update not allowed for field Quantity.

## Cause

This is by design. You can't set a sales quantity for products that are service items. For example, if you offer a service to install an item, it doesn't make sense to record a quantity, because there is no physical item to be counted. There is only a service.
