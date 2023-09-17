--- 
# required metadata 
 
title: Create and assign a trading partner code in the public sector
description: Create a trading partner code and assign it to a government agency that your organization does business with. 
author: twheeloc
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustGroup, CustTradingPartnerCode, CustTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and assign a trading partner code in the public sector

[!include [banner](../../includes/banner.md)]

Create a trading partner code and assign it to a government agency that your organization does business with. The customer record for the agency must exist before you can perform this task. This procedure was created using the PSUS demo company data in the public sector partition.


## Create a trading partner code
1. Go to **Accounts receivable > Setup > Trading partner codes**.
2. Click **New**.
3. In the **Trading partner code** field, type a value.
    * The trading partner codes for government agencies are defined by the United States Department of the Treasury.  
4. In the **Description** field, type the name of the agency that uses this code..
5. Click Save.

## Assign a trading partner code
1. Go to **Accounts receivable > Customers > All customers**.
2. In the list, find and select the agency to assign a trading partner code to.
3. Click to follow the link in the **Name** field.
4. Click **Edit**.
5. Expand the **Miscellaneous details** section.
6. In the **Trading partner code** field, select the trading partner code for this agency..
7. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
