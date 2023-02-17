---
title: EUR-00015 Registration of vendor VAT ID
description: This procedure shows how to add VAT registration IDs and a tax except number to a vendor account.
author: AdamTrukawka
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: VendTable, LogisticsPostalAddress, RegNumTaxIdLookup
---
# EUR-00015 Registration of vendor VAT ID

[!include [banner](../../includes/banner.md)]

This procedure shows how to add VAT registration IDs and a tax except number to a vendor account. This process is similar for legal entities and customers. 

Before you can complete this procedure you must set up VAT IDs. This procedure applies to all European countries/regions. The procedure was created using the demo data company DEMF with a primary address in Germany. This procedure is intended for a data management administrator, accounts payable manager, or accounts receivable manager. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Accounts payable > Vendors > All vendors.
2. In the list find and select vendor DE-01001
3. Click Registration IDs.
4. Click Add.
5. Select VAT ID.
6. In the Registration number field, type a value.
    * Specify a VAT ID in Germany for the selected vendor. The ID must match the specified format of the registration type.  
7. Click the General tab.
8. In the Effective field, enter a date.
9. Click Save.
10. Click New.
11. In the Name or description field, type a value.
    * For example, enter ITA.  
12. In the Country/region field, enter or select a value.
    * For example, select ITA.  
13. Select Yes in the Primary for country field.
14. Click Save.
15. Click the Overview tab.
16. Click Add.
17. In the Registration type field, enter or select a value.
    * For example, select VAT ID.  
18. In the Registration number field, type a value.
    * For example, specify a VAT ID in Italy.  The ID must have the same format as the registration type.  
19. Click Save.
20. Close the page.
21. In the list, find and select the desired record.
    * For example, select DE-01001.  
22. In the list, click the link in the selected row.
23. Expand the Invoice and delivery section.
24. Click Edit.
25. In the Tax exempt number field, enter or select a value.
26. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
