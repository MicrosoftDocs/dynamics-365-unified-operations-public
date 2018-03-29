---
# required metadata

title: Chart of account delimiter must be unique
description: Some organizations enter journals that contain a single voucher that has more than one customer or vendor, and they also run the Accounts receivable or Accounts payable foreign currency revaluation process. This topic describes the steps that these organizations should follow when they upgrade to Microsoft Dynamics 365 for Operations version 1611.
author: ryansandness
manager: AnnBe
ms.date: 03/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 265364
ms.assetid: c61391e4-c4bf-4f09-bd18-8107a1bf055e
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.0

---

# Chart of account delimiter must be unique

[!include[banner](../includes/banner.md)]

In Microsoft Dynamics AX 2012, you could use the same delimiter for your chart of accounts and dimension values. In Dynamics 365 for Finance and Operations, you cannot have the same delimiter for the chart of accounts and a dimension values. 
> [!NOTE]
> You won't get an error, but you may experience instability when entering values in the segmented entry control or dimension entry control, and will need to always use lookups or the flyout when entering account and dimension combinations.

If there is a conflict, the Chart of accounts delimiter and the Project > Subproject format can be changed. No other dimension delimiters can be changed. 
- You can change the chart of accounts delimiter after upgrade to Finance and Operations under the **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**. 
- If the only conflict is with the project/subproject ID format, you can change that value in **Project management and accounting parameters** > **General** > **Modify subproject format**. 

