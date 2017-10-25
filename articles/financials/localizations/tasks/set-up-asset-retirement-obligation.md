--- 
# required metadata 
 
title: Set up asset retirement obligation documents and enter ARO amount on a fixed asset (Japan)
description: For Japan, an asset retirement obligation (ARO) document identifies one type of asset retirement obligation. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up asset retirement obligation documents and enter ARO amount on a fixed asset (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, an asset retirement obligation (ARO) document identifies one type of asset retirement obligation. When you assign an ARO document to a fixed asset book, you can specify the cash flow that is expected to perform the obligation at asset retirement. 



Use this procedure to learn how to create ARO documents, assign it to a fixed asset and enter the estimated retirement cost.



In order to complete this procedure, the Fixed Assets configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Setup asset retirement obligation document
1. Go to Fixed assets > Asset retirement obligations > Asset retirement obligation documents.
2. Click New.
3. In the Document ID field, type a value.
4. In the Document date field, enter a date.
    * The document date is the default value that is used when assigning the ARO document to a fixed asset book.  
    * In the Posting frequency field, select the frequency for accruing the interest expense of the asset retirement obligation.  
5. In the Description field, type a value.
6. Click Save.

## Create a fixed asset and assign the asset retirement obligation document to it
1. Go to Fixed assets > Asset retirement obligations > Fixed assets.
2. Click New.
3. In the Fixed asset group field, select a fixed asset group to apply to the fixed asset.
4. In the Name field, enter a name for the fixed asset.
5. On the Action Pane, click Fixed asset.
6. Click Asset retirement obligation.
7. In the Book field, select the book of the fixed asset.
8. In the Document ID field, select the ID of the asset retirement document to attach to the fixed asset.

## Enter the asset retirement oblgiation amounts
1. Click Create to open the drop dialog.
2. In the Transaction date field, enter the date on which to recognize the asset retirement obligation
3. In the Estimated retirement cost adjustment field, enter the cash flow amount
4. Click OK.

