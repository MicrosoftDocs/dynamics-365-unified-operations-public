---
# required metadata

title: Make the chart of accounts delimiter unique
description: This topic explains how you cannot have the same delimiter for the chart of accounts and dimension values. You must change delimiter values after upgrade. 
author: panolte
ms.date: 09/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 265364
ms.assetid: c61391e4-c4bf-4f09-bd18-8107a1bf055e
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.0

---

# Make the chart of accounts delimiter unique

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics AX 2012, you could use the same delimiter for your chart of accounts and dimension values. In current versions of Finance and Operations, you cannot have the same delimiter for the chart of accounts and dimension values. If there is a duplicate delimiter, you can change it after upgrade. 

## Update delimiter
If there is a conflict with the chart of accounts, the chart of accounts delimiter and the project/subproject ID format can be changed. No other dimension delimiters can be changed. 
- You can change the chart of accounts delimiter after upgrade in **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**. 
- If the only conflict is with the project/subproject ID format, you can change that value in **Project management and accounting parameters** > **General** > **Modify subproject format**. 

## How to determine if your environment requires updated delimiters 
If delimiters in your upgraded environment are conflicting, you may experience instability when entering values in a segmented entry control or dimension entry control. This means that you will need to always use lookups or a flyout menu when entering account and dimension combinations.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
