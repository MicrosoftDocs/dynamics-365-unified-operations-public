---
title: Location directive is not working for net weight or volume based setups
description: Location directive is not working for net weight or volume based setups
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WHSLocDirTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Location directive is not working for net weight or volume based setups

KB Number: 4613090

A location will not get found when e.g. adding a condition for the "Items.Net weight" field in the 'Location Directive Actions' query when joining: "Locations > Warehouse items > Items".


## Resolution
Microsoft has evaluated this issue and determined not to fix this issue as a hot-fix.

Assuming the expected logic for this case is to have the capability to join to the 'Warehouse item number (WHSInventTable)' entity from the 'Locations' and not to the 'Warehouse items' (either default receipt, default issue, or picking location) relationship.

Because the WHSInventTable table does not include a location value this is not possible.

To achieve the business requirement of joining to the "Items.Net weight" you should define this condition on the top query for the 'Location Directives' where it is possible to join with the item number.


