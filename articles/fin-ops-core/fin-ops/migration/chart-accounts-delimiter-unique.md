---
title: Make the chart of accounts delimiter unique
description: Learn about how you cannot have the same delimiter for the chart of accounts and dimension values. You must change delimiter values after upgrade.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/10/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8
ms.assetid: c61391e4-c4bf-4f09-bd18-8107a1bf055e
---

# Make the chart of accounts delimiter unique

[!include [banner](../../../finance/includes/banner.md)]

In Microsoft Dynamics AX 2012, you could use the same delimiter for your chart of accounts and dimension values. In current versions of Dynamics 365 finance and operations, you can't use the same delimiter for the chart of accounts and dimension names or values.

>[!NOTE]
>If an imported dimension value contains the segment delimiter, the system automatically escapes it by using a backslash. For example, if the delimiter is "-" and a customer account number is "1000-01", the system imports it as "1000\\-01".

To use the current delimiter character within dimension values, change the chart of accounts delimiter.

## Update delimiter

If there's a conflict with the chart of accounts, change the chart of accounts delimiter and the project or subproject ID format. You can't change any other dimension delimiters.

- Change the chart of accounts delimiter after upgrade in **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter**.
- If the only conflict is with the project or subproject ID format, change that value in **Project management and accounting parameters** > **General** > **Modify subproject format**.

### Other considerations

Similar to project or subproject ID, any other master data records used as financial dimensions, such as vendors or customers, shouldn't have account ID values that use the same character as the chart of accounts delimiter.

Subproject delimiters automatically update to match the delimiter of their parent project.

## How to determine if your environment requires updated delimiters

If delimiters in your upgraded environment conflict, you might experience instability when entering values in a segmented entry control or dimension entry control. This instability means that you always need to use lookups or a flyout menu when entering account and dimension combinations.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
