--- 
# required metadata 
 
title: Journalize posted journal entries
description: This procedure shows how to journalize posted journal entries. 
author: aprilolson
ms.date: 08/09/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerParameters, SysQueryForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Journalize posted journal entries

[!include [banner](../../includes/banner.md)]

The journalize process in the general ledger provides users a way to group and report on posted voucher entries for your general ledger. The result of the processing based on the criteria you provice generates a list of vouchers with a unique sequence number and the general ledger **journal number** as reference.

The below steps show how to journalize posted journal entries. This procedure uses the USMF demo data company.

1. In the **Navigation pane**, go to **Modules > General ledger > Ledger setup > General ledger parameters**.
2. The **Extended ledger journal** field can be set to Yes or No. If Yes, the report output will be different.
3. Select whether the period can be closed if the journalizing process hasn't been run. If this option is set to Yes, the period cannot be closed until the journalizing process has been completed for that period.  
4. Close the page.
5. In the **Navigation pane**, go to **Modules > General ledger > Periodic tasks > Journalizing**.
6. Click **Filter**.
7. Highlight the row with the filter criteria that you want to define.
8. In the **Criteria** field, enter or select the filter criteria..
9. Click **OK** to close the filter page.
10. Click **OK** to start the journalizing process. A report will be generated after the process is complete.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
