--- 
# required metadata 
 
title: Create online channels and define channel attributes
description: This procedure walks through creating a new online channel and adding it to the organization hierarchy. 
author: jashanno
manager: AnnBe 
ms.date: 03/02/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create online channels and define channel attributes

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through creating a new online channel and adding it to the organization hierarchy. You must create the organization hierarchy before you can create a new online channel. This procedure uses the USRT demo data company.


## Create a new online channel
1. Go to Retail and commerce > Channels > Online stores.
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
7. Click Retail channel.
8. Click OK.
9. Click Publish to open the drop dialog.
10. In the Effective date field, enter a date and time.
11. Click Publish.

