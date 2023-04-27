--- 
# required metadata 
 
title: Set up sales tax authorities
description: Sales tax authorities are entities to which collected sales tax needs to be reported and paid. 
author: twheeloc
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxAuthority   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up sales tax authorities

[!include [banner](../../includes/banner.md)]

Sales tax authorities are entities to which collected sales tax needs to be reported and paid. You can pay sales taxes to the authority directly or through a vendor account that you create for the sales tax authority. If you do this, the company can use its usual payment routines to pay the sales tax authority on time. If you do not set up the tax authority as a vendor, someone must prepare a manual payment to the tax authority on the appropriate due date. This task uses the USMF demo company.

1. Go to Tax > Indirect taxes > Sales tax > Sales tax authorities.
2. Click New.
3. In the Authority field, type a value.
4. In the Name field, type a value.
5. In the Vendor account field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. Select the report layout for your country/region, if one is available. If the report layouts do not correspond to the requirements of the sales tax authority, use default layout.
9. Enter values in the Rounding form and the Round-off fields to specify how the tax total amount to be paid should be rounded. Any rounding differences will be posted to Accounts for automatic transactions set up in General ledger.
10. In the Round-off field, enter a number.
11. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]