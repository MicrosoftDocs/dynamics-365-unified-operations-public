---
title: Importing a sales order record through DMF not picking up auto charges
description: Importing a sales order record through DMF not picking up auto charges
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagement
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Importing a sales order record through DMF not picking up auto charges

KB Number: 4612088

Importing a sales order record through DMF not picking up auto charges

## Resolution
Microsoft has investigated the reported issue. It is not a bug, but works as intended. I works in this manner.  The data entity has a SkipCreateAutoCharges field. This field controls whether or not auto charges are calculated upon import. In order to have auto charges calculated on import, set the value of the SkipCreateAutoCharges field in the imported file to No. Then auto charges will be calculated.


