---
title: Item RM can't be reserved when production order is released 
description: 'When releasing a production order, you may get the error: "Item RM could not be fully reserved." Ensure full quantity is available or reserve items manually.'
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Item RM can't be fully reserved when a production order is released

## Symptoms

If not all BOM line items are physically available when a production order is released to a warehouse, and the **Release to warehouse** policy is set to *Require full reservation*, you receive the following error message:

> Item RM could not be fully reserved. Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started. Could not release the order to warehouse because some materials could not be reserved.

## Resolution

This behavior is by design and is working as expected. The fix this issue, follow the guidance provided in the error message: "Ensure that the full quantity is available, or reserve the items manually if the Reservation field on the BOM line is set to Manual or Started."
