--- 
# required metadata 
 
title: Setup Japan payment by endorsing a customer bill of exchange
description: This task walks you through setting up payments by endorsing a customer bills of exchange for Japan. 
author: ShylaThompson
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPosting,  CustParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Setup Japan payment by endorsing a customer bill of exchange

[!include [banner](../../includes/banner.md)]

This task walks you through setting up payments by endorsing a customer bills of exchange for Japan.



This task was recorded using the demo data company JPMF.


## Set up a posting profile for endorsing bills of exchange
1. Go to Accounts receivable > Setup > Customer posting profiles.
2. Click New.
3. In the Posting profile field, type a value.
    * For example:  enter 'New BoE'.  
4. Click Add.
5. In the Account code field, select an option.
    * For example, select "All".  
6. In the Endorse account field, specify the desired values.
7. Click Save.

## Set up bills of exchange information in accounts receivable parameters
1. Go to Accounts receivable > Setup > Accounts receivable parameters.
2. Click the Ledger and sales tax tab.
3. Expand the Bill of exchange section.
4. In the Endorse Bill of Exchange field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]