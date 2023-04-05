---
title: Set up basic tax integration profile for China
description: This procedure shows how to set up a tax integration profile, update customer settings for issuing VAT invoices, and set up VAT invoice descriptions for China.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC)
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: TaxProfileTable_CN, HcmWorkerLookUp, UnitOfMeasureLookup, CustTable, LogisticsPostalAddress, TaxGroupLookup, VATInvoiceDescTable_CN
---
# Set up basic tax integration profile for China

[!include [banner](../../includes/banner.md)]

This procedure shows how to set up a tax integration profile, update customer settings for issuing VAT invoices, and set up VAT invoice descriptions for China.

Before you can complete this procedure, you must complete the Golden tax integration import setup procedure and the Maintain golden tax export format procedure.

This procedure was created using the demo data company CNMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

1. Go to Tax > Setup > Tax integration > Tax integration profiles.
2. Click New.
3. In the Profile ID field, type a value.
4. In the Profile name field, type a value.
5. In the Sales tax code field, enter or select a value.
6. Select Yes in the Validate amount limit field.
7. In the Maximum invoice amount field, enter a number.
8. Select Yes in the Include tax field.
9. In the Default commodity field, type a value.
10. In the Invoice auditor field, enter or select a value.
11. In the Payment collector field, enter or select a value.
12. In the Format mapping field, enter or select a value.
13. Select Yes in the Non-deductible VAT invoices field.
14. Expand the Default value of description and unit section.
15. Click New.
16. In the list, mark the selected row.
17. In the Description field, type a value.
18. In the Unit field, enter or select a value.
19. Go to Accounts receivable > Customers > All customers.
20. Select a customer.
21. Click Registration IDs.
22. Click Add.
23. In the Registration type field, enter or select a value.
24. ResolveChanges the Registration type.
25. In the Registration number field, type a value.
26. Click Save.
27. Close the page.
28. Expand the Invoice and delivery section.
29. Click Edit.
30. In the Sales tax group field, enter or select a value.
31. Go to Tax > Setup > Tax integration > VAT invoice description.
32. Click New.
33. In the VAT invoice description ID field, type a value.
34. In the Description field, type a value.
35. In the Unit field, enter or select a value.
36. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
