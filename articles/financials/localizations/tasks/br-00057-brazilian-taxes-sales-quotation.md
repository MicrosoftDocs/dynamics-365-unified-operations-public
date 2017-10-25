--- 
# required metadata 
 
title: Brazilian tax in sales quotations
description: Use this procedure to create a sales quotation that uses Brazilian taxes. 
author: sndray
manager: AnnBe 
ms.date: 06/24/2017
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
ms.search.region: Brazil
ms.search.industry: Manufacturing;Distribution;Service industries
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Brazilian tax in sales quotations

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to create a sales quotation that uses Brazilian taxes. You can create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a quotation line, you can select a CFOP code in the CFOP field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the Site field. The tax groups in the Sales tax group and Item sales tax group fields are also updated based on the tax matrix. This task uses the BRMF demo company.

1. Go to Sales and marketing > Sales quotations > All quotations.
2. Click New.
3. In the Account type field, select an option.
4. In the Customer account field, enter or select a value.
5. Click OK.
6. Click Yes.
7. In the Lines or header field, select an option.
8. Expand the Fiscal information section.
    * Use this section to enter fiscal information.  
9. Select Yes in the Final user field.
    * Select Yes if all lines from the quotation are for a final user.  If you select Yes, the Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) tax includes the Imposto Sobre Produtos Industrializados (IPI) tax and any freight charges.  
10. In the Lines or header field, select an option.
11. In the list, mark the selected row.
12. In the Item field, enter or select a value.
13. In the Quantity field, enter a number.
14. In the Site field, enter or select a value.
15. In the Warehouse field, enter or select a value.
16. In the CFOP field, enter or select a value.
17. Expand the Line details section.
18. Click the Setup tab.
19. In the Sales tax group field, enter or select a value.
20. In the Item sales tax group field, enter or select a value.
21. Click the Fiscal information tab.
22. Click Save.
23. On the Action Pane, click Quotation.
24. Click Send quotation.
25. Select Yes in the Print quotation field.
26. Click OK.
27. Close the page.
28. On the Action Pane, click Follow up.
29. Click Confirm.
30. Click Yes.
31. In the Reason field, enter or select a value.
32. Select the Print confirmation check box.
33. Click OK.
34. Close the page.
35. Close the page.
36. Close the page.

