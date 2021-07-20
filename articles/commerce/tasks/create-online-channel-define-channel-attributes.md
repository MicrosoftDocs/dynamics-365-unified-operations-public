--- 
# required metadata 
 
title: Create online channel and define channel attributes
description: This procedure walks through creating a new online channel and adding it to the organization hierarchy. 
author: jashanno
ms.date: 06/04/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: RetailSPOnlineStoreDetailPage, SysLookupMultiSelectGrid, DimensionLookup, OMHierarchyManager, HierarchyDesigner, OMNodeSelection, HierarchyPublishAndCloseForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create online channel and define channel attributes

[!include [banner](../includes/banner.md)]

This procedure walks through creating a new online channel and adding it to the organization hierarchy. You must create the organization hierarchy before you can create a new online channel. This procedure uses the USRT demo data company.


## Create a new online channel
1. Go to Retail and Commerce > Channels > Online stores.
2. Click New.
3. In the Name field, type a value.
4. In the Warehouse field, enter or select a value.
5. In the Store time zone field, select an option.
6. In the Default customer field, enter or select a value.
7. In the Customer address book field, enter or select a value.
8. In the Terms of payment field, enter or select a value.
9. In the Method of payment field, enter or select a value.
10. In the Email notification profile field, enter or select a value.
11. Expand the Financial dimensions section.
12. In the BusinessUnit field, enter or select a value.
    * Similarly set the value for all the other default dimensions.  
13. Click Save.

## Add the online channel to organization hierarchy
1. Close the page.
2. Go to Organization administration > Organizations > Organization hierarchies.
3. In the list, find and select the desired record.
4. Click View.
5. Click Edit.
    * You can select any hierarchy node under which you want to insert the new channel.  
6. Click Insert.
7. Click Commerce channel.
8. Click OK.
9. Click Publish to open the drop dialog.
10. In the Effective date field, enter a date and time.
11. Click Publish.

## Configure orders for near real-time notification
1. Go to Retail and Commerce  > Headquarters setup > Parameters > Commerce parameters.
2. Set Use realtime service for eCommerce order creation to "Yes".
3. Run the 1070 distribution schedule to sync changes to the channel database. 




[!INCLUDE[footer-include](../../includes/footer-banner.md)]