---
author: robinarh
ms.service: dynamics-ax-applications
ms.topic: include
ms.date: 11/17/2020
ms.author: rhaertle
---

## CDS purchase order line soft deleted table to msdyn_purchaseorderproducts

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
LINENUMBER |  | `msdyn_lineorder` | 
PURCHASEORDERNUMBER |  | `msdyn_purchaseorder.msdyn_name` | 
ISDELETED |  | `msdyn_issoftdeletedinscm` | 
