--- 
# required metadata 
 
title: Propose fixed asset acquisitions
description: This topic describes how to acquire a fixed asset using the acquisition proposal in the Fixed assets journal. 
author: saraschi2
manager: AnnBe 
ms.date: 07/22/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetBook, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Propose fixed asset acquisitions

[!include [banner](../../includes/banner.md)]

This topic describes how to acquire a fixed asset using the acquisition proposal in the Fixed assets journal. It uses the accountant role and demo data for the USMF legal entity.

1. In the Navigation pane, go to **Modules > Fixed assets > Journal entries > Fixed assets journal**.
2. Select **New**.
3. In the **Name** field, enter or select a value.
4. In the action pane, select **Lines**.
5. Select **Proposals**.
6. Select **Acquisition proposal**.
7. Select **Filter**. Select **Reset** to clear out previous values.
8. Select the **Fixed asset number** row.
9. In the **Criteria** field, enter or select a value. Set the remaining criteria for the fixed assets that you want to acquire with this proposal.  
10. Select **OK** twice to exit out of the pane.
- Verify the transaction lines created.  
- Only fixed assets with the acquisition date and acquisition price set on the book will be included in the acquisition proposal.  
11. On the page, select the **Books** tab.
12. Select **Post**.

