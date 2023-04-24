--- 
# required metadata 
 
title: Change the ownership of consignment inventory based on production demand
description: This procedure shows how to change the owner of consignment inventory from the vendor to your legal entity when there is demand for the inventory in production. 
author: yufeihuang
ms.date: 08/14/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventJournalOwnershipChange, InventJournalCreate   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Change the ownership of consignment inventory based on production demand

[!include [banner](../../includes/banner.md)]

This procedure shows how to change the owner of consignment inventory from the vendor to your legal entity when there is demand for the inventory in production. This change of ownership is done by creating and posting an inventory ownership change journal. The ownership change journal lines can be created manually or, as shown in this recording, based on existing production demand. Typically, a shop floor supervisor performs this task. You can use this procedure in the USMF demo data company or on your own data. If you're using your own data, make sure that you have the following prerequisites: an inventory journal name that has been set up for inventory ownership change, physically recorded vendor-owned on-hand items, and one or more production order lines for the material. This procedure is for a feature that was added in Dynamics 365 for Operations, version 1611.

> [!NOTE]
> Outbound consignment processes are not supported out-of-the-box and automatic ownership journal processing is not supported.

## Create an inventory ownership journal
1. Go to Inventory management > Journal entries > Items > Inventory ownership change.
2. Click New.
    * The inventory ownership change journal is used to change the owner of consignment inventory from the vendor to the current legal entity. This change of ownership is done by releasing the on-hand inventory that is owned by the vendor and then receiving that inventory in the current legal entity.  
3. In the Name field, enter or select a value.
    * You can select only inventory journal names that have a journal type of Ownership change.  
4. Click OK.
5. Click Functions.
6. Click Create journal lines from production orders.
    * You can start the change of ownership process by querying all the production lines that have demand for consumption of raw material.  
7. In the Inventory issue statuses to include field, select an option.
    * This option lets you filter by the issue status of the inventory transactions. For example, you can create journal lines for inventory that has the Picked and Reserved physical statuses.  
8. Expand the Records to include section.
    * This section lets you apply additional filtering. For example, you can select a specific raw material date.  
9. Click OK.

## Post the inventory ownership change journal
1. Click Post.
    * When the journal is posted, the vendor-owned inventory is released by using an "Ownership change" reference. The inventory is then received as on-hand by using an inventory transaction that is updated with a purchase order product receipt. Note that only transactions that are related to the posted journal are created. No expected inventory transactions are created.  
2. Click OK.
3. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]