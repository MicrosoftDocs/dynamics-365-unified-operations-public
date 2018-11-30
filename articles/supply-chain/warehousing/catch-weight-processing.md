---
# required metadata

title: Enable catch weight product processing with warehouse management
description: This topic describes how to use work templates and location directives to determine how and where work is carried out in the warehouse.
author: perlynne
manager: AnnBe
ms.date: 11/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSCatchWeightTag, WHSCatchWeightItemHandlingPolicy
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.3

---

# Enable catch weight product processing with warehouse management

[!include [banner](../includes/banner.md)]

You can enable the catch weight product processing with warehouse management functionality with a license configuration key (**System administration > Setup > License configuration > Configuration keys > Trade > Warehouse and Transportation management > Catch weight for warehouse**).

> [!NOTE]
> Both the **Warehouse and transportation management** and the **Process distribution catch weight** license configuration keys must be enabled as well.


When the license configuration key is enabled, you can create a new released product with **Catch weight** selected and associated with a storage dimension group that has the parameter **Use warehouse management processes** selected.

Before you can use the product in Warehouse management, some basic product-specific catch weight setup must be done [Setting up and maintaining catch weight items](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/setting-up-and-maintaining-catch-weight-items).

-	Nominal weight definition between the catch weight unit (Box) and the inventory unit (Kg) as part of a unit conversion definition
-	Definition of the minimum and maximum weight tolerances as part of the catch weight unit setup
-	Use of unit sequence group where the catch weight unit must be defined as the lowest stock keeping unit.
-	Use of catch weight item handling policy


## Transaction adjustments

Because the weight of the inventory can be different from getting in until it gets issued out of a warehouse the catch weight product processing will need to perform adjustments of the inventory. 

**Example scenario**
During a **Report as finished** production process a license plate containing 8 boxes of a catch weight product gets inbound weight captured as 80.1 kg. The license plate gets stored away in the finished goods area for some time and during this period some weight gets lost in the air.
As part of a sales order picking process the same license plate gets weight captured again to the weight of 79.8 kg.
In the system we now have a weight difference as part of the physical dimension set which will be automatically adjusted by posting a transaction for the missing 0.3 kg.
Another example where automatic adjustment will happen is when having a product defined to allow the minimum weight of 8 kg and a maximum weight of 12 kg of the catch weight unit **Box**.
When then having 2 boxes with the registered weight of 16 kg, and a warehouse worker pick and weigh 1 of the boxes to 9 kg, this will result in the remaining 1 box weighing 7 kg. But because this is below the minimum weight an automatic adjustment will be done which will increase the inventory weight on-hand with 1 kg.
The setup defining the accounts used for these postings is done at:
**Cost management > Ledger integration policies setup > Posting > Inventory**
-	Catch weight loss account
-	Catch weight profit account

## Catch weight item handling policy

The catch weight item handling policy defines two primary warehouse management flows for the items; when and how to capture the weight of the items.
It is possible to define when to capture weight for sales and transfer order processing, which can be done either during: 
-	Picking: Capturing of the weight during the initial pick work lines of order work
-	Packing: Capturing of the weight during manual packing. (You must send these items to a packing station)
When the capturing of the actual weight happens at the packing station during the container packing processes, the warehouse worker will not be prompted to capture the weight during the work picking. Here the average weight of the physical inventory will be used as the weight of the picked inventory going to the packing area.
It is possible to define how to capture the weight by two main flows (with and without the use of catch weight tag tracking).
-	Yes: Item will use catch weight tags, where each tag number will represent one catch weight unit (per box) and have a weight and other information tied to it. For outbound processes the weight associated with the tag will be used. 
-	No: Item does not use catch weight tags and the inbound and outbound weighing process will be based on actual captured weight during each process.
The catch weight tag tracking process can be used for items which will not change weight during the storage period. The weight will only be captured during the inbound warehouse process. During the outbound process the catch weight tags will simple be scanned and the weight associated with the tags will be used for the outbound transactional processing.
Inbound catch weight capturing methods
When using the catch weight tag tracking process, a tag will always need to be created per catch weigh unit getting received and each tag will always need to be associated with a weight. This means that when e.g. receiving 1 pallet of 8 boxes (having box as the catch weight unit); 8 unique catch weight tags must be created, and each tag get a weight associated. Depending on the Inbound catch weight tag capturing the weight getting captured can either be distributed as an average weight for all 8 boxes or captured as unique weight for each box.
When not using catch weight tag tracking the weight can be captured for each dimension set (e.g. for each license plate and tracking dimension) or captured based on an aggregated level like for example for 5 license plates (pallets).
For the outbound weight capturing methods it is possible to define if the weighing should happen for each catch weight unit (per box) or captured based on the quantity defined to be picked (e.g. for 3 boxes). Please note that for the production line picking process the average weight will be used when using the ‘Not captured’ option.

