--- 
# required metadata 
 
title: Enable the JBA payment file format (Japan)
description: In Japan, the Japanese Bankers Association (JBA) has specified a file format for electronic fund transfers (EFT). 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/16/2016
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
# Enable the JBA payment file format (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the Japanese Bankers Association (JBA) has specified a file format for electronic fund transfers (EFT). 



This procedure walks you through importing the JBA payment model and enabling the JBA payment file for vendor methods of payment. 



This procedure was created using the demo data company JPMF.


## Import the JBA payment model
1. Go to Organization administration > Workspaces > Electronic reporting.
2. Click Repositories.
3. Click Open.
4. In the tree, select 'Payment model\JBA Payment model\JBA Payment file (JP)'.
5. Click Import.
6. Click Yes.

## Use the JBA payment file in the vendor method of payment
1. Go to Accounts payable > Payment setup > Methods of payment.
2. Click Edit.
3. Expand or collapse the File formats section.
4. Select the Generic electronic reporting check box.
5. In the Export format configuration field, click the drop-down button to open the lookup.
6. In the list, select JBA Payment file (JP).
7. Click Save.

