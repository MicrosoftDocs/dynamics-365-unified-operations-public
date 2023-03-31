--- 
# required metadata 
 
title: Enable the payroll process for time and attendance
description: This procedure shows how to enable the payroll process for time and attendance. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: JmgPayTable, JmgPayRate, JmgPayAgreementTable, JmgPayAgreementLine, HcmWorker   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enable the payroll process for time and attendance

[!include [banner](../../includes/banner.md)]

This procedure shows how to enable the payroll process for time and attendance. The demo data company used to create this procedure is USMF.


## Create a pay type with a related pay rate
1. Time and attendance > Setup > Payroll > Pay types
2. Click New.
3. In the Pay type field, type a value.
4. In the Description field, type a value.
5. Click Save.
6. Click Rates.
    * Rates for pay types are set up for specific time intervals, and individual rates can be created for workers. It is not always necessary to create rates for pay types in time and attendance. This information may already exist in the payroll system that is used to generate wages.  
7. Click New.
8. In the list, mark the selected row.
9. In the Rate field, enter a number.
10. Click Save.

## Create a pay agreement
1. Close the page.
2. Close the page.
3. Go to Pay agreements.
    * Time and attendance > Setup > Pay agreements  
4. Click New.
5. In the Pay agreement field, type a value.
6. In the Description field, type a value.
7. Click Save.
8. Click Agreement lines.
9. Click New.
10. In the list, mark the selected row.
11. In the Profile type field, enter or select a value.
12. In the Pay type field, enter or select a value.

## Set up pay agreement for time and registration worker
1. Close the page.
2. Close the page.
3. Go to Time registration workers.
    * Time and attendance > Setup > Time registration workers  
4. In the list, click the link in the selected row.
5. Click the Employment tab.
6. Expand the Time registration section.
7. Click Edit.
8. In the Pay agreement field, enter or select a value.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]