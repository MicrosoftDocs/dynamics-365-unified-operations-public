---
title: Generate Japan consumption tax report
description: This procedure walks you through generating the Japan consumption tax report.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerConsumptionTaxCalcTrans_JP, LedgerConsumptionTaxReportTrans_JP
---
# Generate Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This procedure walks you through generating the Japan consumption tax report. This procedure was created using the demo data company JPMF.

1. Go to Tax > Declarations > Sales tax > Japanese sales tax report.
2. In the From date field, enter a date.
    * For example: 2012/1/1  
3. In the To date field, enter a date.
    * For example: 2012/12/31  
4. In the Settlement period field, type a value.
5. In the Declaration type field, select an option.
6. In the Calculation method field, select an option.
7. Select Yes in the Amendment field.
    * If you have already generated the report previously and you are generating it again, you must choose to update the existing record on the amendment.  
8. Click OK.
9. Click Edit.
10. In the Item 6 field, enter a number.
    * The data is retrieved and summarized from the transactions. You can update the editable fields for adjustment purposes.  
11. Click Save.
12. Click Update amount.
    * This recalculates the amounts.  
13. Click Finalize.
14. Click Yes.
15. Click Consumption tax report.
16. Click the Tax calculation tab.
17. Click Edit.
18. In the Item 10 field, enter a number.
19. Click Save.
20. Click Update amount.
21. Click the Additional information tab.
    * In the Additional information tab, the information is printed as configured.  
    * For example: you can change the Installment basis slider to be 'Yes' to print a yes on the final report.  
22. Click Finalize.
23. Click Yes.
24. On the Action Pane, click Consumption tax report.
    * Click Print reports to generate the final report.  

> [!NOTE]
> To calculate the consumption tax report that should be submitted from October 1, 2019, you must turn on the **Japanese sales tax report** feature in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
