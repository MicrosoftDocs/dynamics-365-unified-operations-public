---
title: Automatic transmission of NF-e fiscal documents (Brazil)
description: Use the following procedure to set up email parameters to automatically send a Nota Fiscal eletrônica (NF-e) to a vendor or customer after the NF-e is approved or canceled, or if you generate a correction letter.
author: AdamTrukawka
ms.date: 06/26/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
ms.search.industry: Manufacturing;Distribution;Service industries
---
# Automatic transmission of NF-e fiscal documents (Brazil)

[!include [banner](../../includes/banner.md)]

Use the following procedure to set up email parameters to automatically send a Nota Fiscal eletrônica (NF-e) to a vendor or customer after the NF-e is approved or canceled, or if you generate a correction letter. You can set up a batch group and email templates for an NF-e. You must create separate email templates for an approved NF-e, a canceled NF-e, and a correction letter. You can then create a batch process to send the NF-e by email. This task uses the BRMF demo company.

1. Go to System administration > Setup > Batch group.
2. Click New.
3. In the Group field, type a value.
4. In the Description field, type a value.
5. Click Save.
6. Close the page.
7. Go to System administration > Periodic tasks > Email processing > Batch.
8. Expand the Run in the background section.
9. Select Yes in the Batch processing field.
10. In the Batch group field, enter or select a value.
11. Click Recurrence.
12. Select the No end date option.
13. In the Count field, enter a number.
14. In the Time zone field, select an option.
15. Click OK.
16. Click OK.
17. Go to Organization administration > Setup > Email templates.
18. Click New.
19. In the Email ID field, type a value.
20. In the Sender email field, type a value.
21. In the Sender name field, type a value.
22. In the Default language code field, enter or select a value.
23. In the Lines or header field, select an option.
24. In the Batch group field, enter or select a value.
25. In the Email description field, type a value.
26. In the Lines or header field, select an option.
27. Click Save.
28. In the list, mark the selected row.
29. In the Subject field, type a value.
30. In the Language field, enter or select a value.
31. Click Edit.
32. In the WritableContent field, type a value.
33. Click OK.
34. Click Save.
35. Close the page.
36. Close the page.
37. Go to Organization administration > Organizations > Fiscal establishments > Fiscal establishments.
38. Use the Quick Filter to find records. For example, filter on the Fiscal establishment ID field with a value of 'Matriz'.
39. Expand the NF-e and NFC-e federal section.
40. Click Edit.
41. In the Approved NF-e field, enter or select a value.
42. Select Yes in the Attach the DANFE as PDF file to  email field.
43. Click Save.
44. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
