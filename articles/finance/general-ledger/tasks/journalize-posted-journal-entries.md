--- 
title: Journalize posted journal entries
description: Learn how to journalize posted journal entries, including a step-by-step process for journalizing posted journal entries using the USMF dem data company. 
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 03/09/2022
ms.custom:
ms.reviewer: kfend  
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerParameters, SysQueryForm 
ms.dyn365.ops.version: Version 7.0.0 
---

# Journalize posted journal entries

[!include [banner](../../includes/banner.md)]

The journalize process in the general ledger provides a way to group and report on posted voucher entries for your general ledger. Based on the criteria that you provide, the processing generates a list of vouchers that use a unique number sequence and that have the general ledger **Journal number** value as a reference.

Follow these steps to journalize posted journal entries. This procedure uses the **USMF** demo data company.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. In the **Extended ledger journal** field, select a value. If you select **Yes**, the report output will be different.
3. Select whether the period can be closed if the journalizing process hasn't been run. If you select **Yes**, the period can't be closed until the journalizing process has been completed for that period.
4. Close the page.
5. Go to **General ledger** \> **Periodic tasks** \> **Journalizing**, and select **Filter**.
6. Select the row for the filter criteria that you want to define.
7. In the **Criteria** field, enter or select the filter criteria.
8. Select **OK** to close the page.
9. Select **OK** to start the journalizing process. A report will be generated after the process is completed.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
