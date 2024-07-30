---
title: Make the chart of accounts delimiter unique
description: Learn about how you cannot have the same delimiter for the chart of accounts and dimension values. You must change delimiter values after upgrade.
author: RyanCCarlson2
ms.author: RCarlson
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8
ms.assetid: c61391e4-c4bf-4f09-bd18-8107a1bf055e
---

# Make the chart of accounts delimiter unique

[!include [banner](../../../finance/includes/banner.md)]

In Microsoft Dynamics AX 2012, you could use the same delimiter for your chart of accounts and dimension values. In current versions of finance and operations, you cannot have the same delimiter for the chart of accounts and dimension names or values. If there is a duplicate delimiter, you can change it after upgrade. 

## Update delimiter
If there is a conflict with the chart of accounts, the chart of accounts delimiter and the project/subproject ID format can be changed. No other dimension delimiters can be changed. 
- You can change the chart of accounts delimiter after upgrade in **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**. 
- If the only conflict is with the project/subproject ID format, you can change that value in **Project management and accounting parameters** > **General** > **Modify subproject format**. 

### Other considerations
Similar to project/subproject ID, any other master data records used as financial dimensions, such as vendors or customers, should not have account ID values that use the same character as the chart of accounts delimiter. 

## How to determine if your environment requires updated delimiters 
If delimiters in your upgraded environment are conflicting, you may experience instability when entering values in a segmented entry control or dimension entry control. This means that you will need to always use lookups or a flyout menu when entering account and dimension combinations.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

