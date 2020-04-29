--- 
# required metadata 
 
title: Register items for an advanced warehousing enabled item using an item arrival journal
description: This procedure shows you how to register items using the item arrival journal when you are using advanced warehouse management processes. 
author: ShylaThompson
manager: tfehr 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: WMSJournalTable, WMSJournalCreate, WHSLicensePlate   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Register items for an advanced warehousing enabled item using an item arrival journal

[!include [banner](../../includes/banner.md)]

This procedure shows you how to register items using the item arrival journal when you are using advanced warehouse management processes. This would usually be done by a receiving clerk. 

You can run this procedure in demo data company USMF, or on your own data. You need to have a confirmed purchase order with an open purchase order line before you start this guide. The item on the line must be stocked, and it must not use product variants, and must not have tracking dimensions. And the item needs to be associated with a warehouse management process enabled storage dimension group. The warehouse that's used must be enabled for warehouse management processes and the location that you use for receiving must be license plate controlled. If you're using USMF, you can use company account 1001, Warehouse 51, and item M9200 to create your PO. 

Make a note of the number of the purchase order that you create, and also note the item number and the site that you used for your purchase order line.


## Create an item arrival journal header
1. Go to Item arrival.
2. Click New.
3. In the Name field, type a value.
    * If you are using USMF, you can type WHS. If you're using other data, the journal whose name you choose has to have the following properties: Check picking location must be set to No, and Quarantine management must be set to No.  
4. In the Number field, type a value.
5. In the Site field, type a value.
    * Select the site that you used for your purchase order line. This will serve as a default value, which will default to all lines in the journal. If you used warehouse 51 in USMF, choose site 5.  
6. In the Warehouse field, type a value.
    * Select a valid warehouse for the site that you've selected. This will serve as a default value, which will default to all lines in the journal. If you're using the example values in USMF, select 51.  
7. In the Location field, type a value.
    * Select a valid location in the warehouse that you've selected. The location has to be associated with a location profile, which is license plate controlled. This will serve as a default value, which will default to all lines in the journal. If you're using the example values in USMF, select Bulk-008.  
8. Right-click on the drop-down arrow in the License plate field and then select View details.
9. Click New.
10. In the License plate field, type a value.
    * Make a note of the value.  
11. Click Save.
12. Close the page.
13. In the License plate field, type a value.
    * Enter the value of the license plate that you just created. This will serve as a default value, which will default to all lines in the journal.  
14. Click OK.

## Add a line
1. Click Add line.
2. In the Item number field, type a value.
    * Enter the item number that you used on the purchase order line.  
3. In the Quantity field, enter a number.
    * Enter the quantity that you want to register.  
    * The Date field determines the date on which the on-hand quantity of this item will be registered in the inventory.  
    * The lot ID will be populated by the system if it can be uniquely identified from the information provided. Otherwise you will have to add this manually. This is a mandatory field, which links this registration to a specific source document line.  

## Complete the registration
1. Click Validate.
    * This checks that the journal is ready to be posted. If the validation fails you will need to fix the errors before you can post the journal.  
2. Click OK.
    * After you clicked OK, check the message. There should be a message saying that the journal is OK.  
3. Click Post.
4. Click OK.
    * After you have clicked OK, check the message bar. There should be a message saying that the operation completed.  
5. Close the page.

