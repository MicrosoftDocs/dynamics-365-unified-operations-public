---
title: Return order invoice synchronization
description: Learn about the changes that enable synchronization of return order invoices from Microsoft Dynamics 365 Finance to Dataverse environments.
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

# Return order invoice synchronization

[!include [banner](../../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article provides an overview of the changes that were implemented so that dual-write can support return order invoices. Microsoft created a new mapping to sync return order invoices from Microsoft Dynamics 365 Finance to the customer's Dataverse environment.

In previous versions of Finance, dual-write doesn't support return order invoices. When a return order invoice is created in Finance, it generates a sales order of the **Return order** type that has negative quantities. This sales order isn't synced back to the customer's Dataverse environment because the current entity is filtered on specific order types. Learn more in [Guidance for dual-write setup](../../fin-ops-core/dev-itpro/data-entities/dual-write/connection-setup.md).

In Finance version 10.0.43, two new entities are available for return order invoices: CDS return invoice headers and CDS return invoice lines. These entities support dual-write synchronization to the customer's Dataverse environment. To sync return order invoices, customers must enable the dual-write mapping for CDS return invoice headers and CDS return invoice lines.

To export invoices, customers can use the existing sales invoice headers and sales invoice lines entities in Finance. The new return order invoice entities support dual-write synchronization. This solution for return order invoices helps minimize the risk of disruption to the existing sales order process.
