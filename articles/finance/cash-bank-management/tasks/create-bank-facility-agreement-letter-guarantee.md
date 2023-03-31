--- 
# required metadata 
 
title: Create a bank facility agreement for the letter of guarantee
description: This task creates a bank facility agreement to process a letter of guarantee. 
author: angelad116
ms.date: 11/15/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a bank facility agreement for the letter of guarantee

[!include [banner](../../includes/banner.md)]

This task creates a bank facility agreement to process a letter of guarantee. This task uses the USMF demo company. 


## Create Bank facility agreement
1. Go to **Cash and bank management > Letters of guarantee > Bank facility agreements**.
2. Click **New**.
3. In the **Agreement number** field, enter the bank agreement number for the transaction.
4. In the **Bank account** field, select the bank account number for which the letter of guarantee is open. 
5. In the list, click the link in the selected row.
6. In the **Start date** field, enter a date and time.
7. In the **End date** field, enter a date and time.
8. Toggle the expansion of the General section.
9. Click **Add line**.
10. In the **Facility type** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the list, click the link in the selected row.
13. In the **Limit** field, enter the amount negotiated with the bank.
14. Click **Save**.
15. Toggle the expansion of the Letter of guarantee section.
16. In the **Calculation method** field, select an option.
    * Enter the calculation method and percentage details for the Cash margin, Issuance commission, Extension commission, Increase value commission, or Decrease value commission, as appropriate.   
17. Click **Save**.

## Extend bank facility agreement
1. Click **Extend** to open the drop dialog.
2. In the **New agreement number** field, type a value.
3. In the **End date** field, enter a date and time.
4. Click **Extend**.
5. Click **Save**.
6. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
