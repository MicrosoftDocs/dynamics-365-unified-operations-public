--- 
# required metadata 
 
title: Set up withholding tax
description: This article explains how to set up withholding tax.   
author: twheeloc
ms.date: 05/23/2023  
ms.topic: how-to  
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxWithholdTable, TaxWithholdData, TaxWithholdGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up withholding tax

[!include [banner](../../includes/banner.md)]

This article explains how to set up withholding tax. *Withholding tax* is a tax on vendors that does not create sales tax transactions. Withholding tax that is calculated on vendor payments is a liability. Therefore, only balance sheet accounts or liability accounts are valid accounts for posting withholding tax. This task guide demonstrates how to set up withholding tax.

1. Go to **Tax > Indirect taxes > Withholding tax > Withholding tax codes**.
2. Select **New**.
3. In the **Withholding tax code** field, type a value.
4. In the **Withholding tax name** field, enter the name of the withholding tax code.
5. In the **Main account** field, select the main account for posting the withholding tax liability.
6. Select **Save**.
7. Select **Values** and mark the desired record in the list.
8. In the **Value** field, enter a percentage used for the calculation of the withholding tax.
9. Select **Save**.
10. Close the page.
11. Select **Save**.
12. Close the page.
13. Go to **Tax > Indirect taxes > Withholding tax > Withholding tax groups**.
14. Select **New**.
15. In the **Withholding tax group** field, enter the identifier of the withholding tax group.
16. In the **Description** field, enter the name of the withholding tax group.
17. In the **Withholding tax code** field, select the withholding tax code.
18. Select **Save**.
19. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
