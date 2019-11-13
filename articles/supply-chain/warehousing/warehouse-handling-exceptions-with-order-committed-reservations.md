---
# required metadata

title: Exception handling of warehouse work with order-committed batch number 
description: 
author: omulvad
manager: AnnBe
ms.date: 11/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSReservationHierarchy 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2020-01-15
ms.dyn365.ops.version: 10.0.9

---

# Exception handling of warehouse work with order-committed batch number

Warehouse work for picking order-committed batch number is subject to the same standard warehouse exception handling and actions as any other regular work. Generally, the open work and/or work line can be cancelled, interrupted due to Full user location situation, short-picked, and get updated due to a movement. Likewise, the picked quantity of the already completed work can be reduced or the work can be reversed. The key rule that is applied to all of these exception handling actions is that the batch number that was reserved for the customer can never be replaced with a different one, while its storage dimension – location and license plate – may change due to manual update by the user or automatic update by the system. The latter is based on the same random storage dimension assignment as applied when automatically reserving a specific batch without specifying storage dimensions.

The following table provides an overview of how order-committed batch reservation is treated by the system depending on the user action with regards to a given exception handling flow:

| Warehouse flow | Key setup parameter | Batch quantity is available (in addition to already reserved for the current order-committed reservations or works originating from such a reservation type) | User action | Warehouse work | Order-committed batch reservation |
| --- | --- | --- | --- | --- | --- |
| Override pick location on the open work | **Allow pick location override** option (on the Worker) is enabled | Yes | Clicks **Override location** menu item on the WMA when starting on a pick work Clicks the **Suggest** button. Confirms the new location\*  \* suggested based on batch quantity availability    | Current work:
- Location on the pick line is updated to the new Location\*
\* If LP-controlled, random LP is assigned to the work inventory transaction and the worker can pick from any LP with available quantity
- If quantity is found on more than one LP on the new location – the original pick line is split into multiple lines to match each LP
 | n/a |
|   |   | No | Clicks **Override location** menu item on the WMA when starting on a pick work Enters location manually   | The Override location action is not possible and fails with an error |  n/a |
| Full button - split work line due to overflow on user location | **Allow splitting of work** option (on the mobile device menu item) is enabled | n/a | Clicks **Full** menu item on the WMA when processing a pick work Enters partial quantity of the required pick in the **Pick Qty** field to indicate the full capacity   | Current work:
- quantity is updated to the remaining to pick
New work:
- for the picked quantity is created and closed
 | n/a |
| Reduce picked quantity of completed work (from Load)   | n/a | Yes | Opens **Reduce picked quantity** page from the load line  Enters full quantity to unpick Selects &quot;Move to&quot; location/LP | Work associated with the load line:
- is cancelled
New work:
- for Inventory movement is created and closed
 | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available   |
|   |   | No | as above | as above | is re-reserved for the same batch, and location and LP (if LP-controlled) entered during unpicking   |
| Move\* item within warehouse \* only applicable to **Work creation process** type _Movement_ (not _Movement by template_) | **Allow movement of inventory with associated work** option (on the Worker) is enabled   | Yes | Starts a **Movement** on the on the WMA   Enters From/To locations | All existing work affected by the move:
- Pick location is updated to the new &#39;To&#39; Location
New work:
- for Inventory movement is created and closed
  | All existing reservations affected by the quantity movement from the given location are re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
|   |   | No | as above | as above | All existing reservations affected by the quantity movement from the given location are re-reserved for the same batch, and the new &#39;To&#39; location and LP (if LP-controlled) |
| Reverse picked quantity of completed work (from Load or Wave) | n/a | Yes | Opens **Reverse work** page Selects **Leave items at current location** option on the request page | All work (associated with load):
- is cancelled
 | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
|   |   | No | as above | All work (associated with load):
- is cancelled
 | is re-reserved for the same batch, and location and LP where quantity was left upon reversal |
|   |   | Yes | selects **Assign items to this location** option on the request page | Current work:
- is cancelled
New work:
- for Inventory movement is created and closed
 | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
|   |   | No | as above | Current work:
- is cancelled
New work:
- for Inventory movement is created and closed
 | is re-reserved for the same batch, and location and LP where quantity was assigned to upon reversal |
|   |   | Yes/No | Selects **Move items to this location** option on the request page | Reversal is not supported | n/a |
|   |   | Yes/No | Selects **Move items based on location directives** option on the request page | Reversal is not supported | n/a |
| Shortpick quantity - register quantity physically not found on location/LP while performing pick work     | **Work exception** of type _Short pick_ is set with:
- Item reallocation=None
- Adjust inventory=Yes
- Remove reservations=No
  | Yes | Clicks **Shortpick** menu item on the WMA when executing a pick work  Enters 0 for the **Pick Quantity**  Selects Reason _No reallocation_ | Current work:
- is closed, with 0 picked quantity
 Inventory transaction of type _Counting_, Issue=_Sold_, is created to represent adjustment-out  | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
|   |   | No | as above | Shortpicking action fails with an error  Current work:
- remains open
 | n/a |
|   | **Work exception** of type _Short pick_ is set with:
- Item reallocation=None
- Adjust inventory=Yes
- Remove reservations=Yes
 | Yes | as above | Current work:
- is closed, with 0 picked quantity
 Inventory transaction of type _Counting_, Issue _Sold_, is created to represent adjustment-out | All existing reservations affected by the quantity adjustment in the shortpicked location are re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
|   |   | No | as above | Current work:
- is closed, with 0 picked quantity
 Inventory transaction of type _Counting_, Issue _Sold_, is created to represent adjustment-out | All existing reservations affected by the quantity adjustment in the shortpicked location are removed |
|   | **Work exception** of type _Short pick_ is set with:
- Item reallocation=Manual
- Adjust inventory=Yes
- Remove reservations=No/Yes
  **Allow manual item reallocation** option (on the Worker) is enabled  | Yes | Clicks **Shortpick** menu item on the WMA when executing a pick work  Enters &#39;0&#39; for the **Shortpick Quantity** Selects Reason _Short Picking with manual reallocation_ Selects location/LP from the list displayed on the screen | Current work:
- Pick line is closed, with 0 picked quantity
- Put line is cancelled
- New pick line is created with location/LP chosen by the user
- New put line is created
 Inventory transaction of type _Counting_, Issue _Sold_, is created to represent adjustment-out | n/a |
|   | **Work exception** of type _Short pick_ is set with:
- Item reallocation=Manual
- Adjust inventory=Yes
- Remove reservations=No
  **Allow manual item reallocation** option (on the Worker) is enabled | No | As above except no location/LP list is given to select from | Shortpicking action fails with an error | n/a |
|   | **Work exception** of type _Short pick_ is set with:
- Item reallocation=Manual
- Adjust inventory=Yes
- Remove reservations=Yes
  **Allow manual item reallocation** option (on the Worker) is enabled | No | As above | Current work:
- Pick line is closed, with 0 picked quantity
- Put line is cancelled
 Inventory transaction of type _Counting_, Issue _Sold_, is created to represent adjustment-out | All existing reservations affected by the quantity adjustment in the shortpicked location/LP are removed |
|   | **Work exception** of type _Short pick_ is set with:
- Item reallocation=Automatic
- Adjust inventory=Yes/No
- Remove reservations=Yes/No
 |  n/a | Clicks **Shortpick** menu item on the WMA when executing a pick work  Enters &#39;0&#39; for the **Shortpick Quantity** Selects Reason _Short Picking with automatic reallocation_ | Shortpick with automatic reallocation is not supported | Shortpick with automatic reallocation is not supported |
| Change inventory status\* \* Performed from multiple entry points. Example here is based on using **Inventory status change** action from **On-hand by location** | On the **Warehouse** record [**Warehouse** tab], the **Remove reservations and markings** [at inventory status change] is set to _Reservations_ | No | Selects specific **Location**  Selects line with specific item, location and LP (if LP-controlled)    Clicks I **nventory status change** button  Sets Inventory status to _Blocking_ | Inventory status change is not allowed for quantities reserved for work | reservation is removed   2 inventory transactions of type=_Inventory status change_ are created to represent change in inventory status dimension change Inventory transaction of type=_Inventory blocking_, Issue=_Reserved physical_, is created to represent reservation of blocked quantity   |
|   |   | Yes | as above | Inventory status change is not allowed for quantities reserved for work | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available 2 inventory transactions of type=_Inventory status change_ are created to represent change in inventory status dimension change Inventory transaction of type=_Inventory blocking_, Issue=_Reserved physical_, is created to represent reservation of blocked quantity   |
|   | On the **Warehouse** record [**Warehouse** tab], the **Remove reservations and markings** [at inventory status change] is set to _None_ | No | as above | Inventory status change is not allowed for quantities reserved for work | Inventory status change is not allowed |
|   |   | Yes | as above | Inventory status change is not allowed for quantities reserved for work | is re-reserved for the same batch, with randomly assigned location and LP (if LP-controlled) where quantity is available |
