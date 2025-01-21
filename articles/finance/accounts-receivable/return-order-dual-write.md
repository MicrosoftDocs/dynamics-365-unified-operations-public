---
title: Return order invoices sync
description: This article describes how to sync return order invoices from Dynamics 365 Finance to dataverse environments.
author: twheeloc
ms.author: reetuchopra
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/04/2019
ms.reviewer: twheeloc
ms.search.region: 
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4
---

# Return orders invoice sync

[!include [banner](../../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides an overview of the changes implemented to support return order invoices with dual-write. Microsoft created new mapping to synchronize return order invoices from Microsoft Dynamics 365 Finance to the customer's Dataverse environment.

## Overview
In previous versions, return order invoices weren't supported with dual-write. When a return order invoice is created in Microsoft Dynamics 365 Finance, it generates a **Return order** type of sales order with 
negative quantities. This doesn't synchronize back to the customer's Dataverse environment due to the current entity being filtered on specific order types. 
For more information, see [Dual-write](../../fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup.md).


In Dynamics 365 Finance version 10.0.43, new entities are available for return orders invoices (CDS return invoice headers, CDS return invoice lines) that support dual-write synchronization to the customer's 
Dataverse environment. Customers need to enable the dual write mapping for CDS return invoice headers and CDS return invoice lines to synchronize the return order invoices.

To export invoices, customers can use the existing sales invoice headers and lines entities in Microsoft Dynamics 365 Finance. The new return order invoice entities support the dual-write synchronization.
This is a solution for return orders invoices and it minimizes the risk of disrupting the existing sales order process.
