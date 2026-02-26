---
title: Make the chart of accounts delimiter unique
description: Learn why you can't have the same delimiter for the chart of accounts and dimension values, how account strings are interpreted, and how to resolve delimiter conflicts.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 02/26/2026
ms.reviewer: twheeloc
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8
ms.assetid: c61391e4-c4bf-4f09-bd18-8107a1bf055e
---

# Make the chart of accounts delimiter unique

[!include [banner](../../../finance/includes/banner.md)]

In Microsoft Dynamics AX 2012, you could use the same delimiter for your chart of accounts and dimension values. In current versions of finance and operations, the chart of accounts delimiter must be unique. If a delimiter is duplicated, you can change it after upgrade.

## Why the delimiter must be unique

The chart of accounts delimiter is the character (for example, a dash `-`) that separates the main account from financial dimension values when you enter a full ledger account string. If a dimension *value* also contains that same character, the system can't determine where one segment ends and the next begins.

### How the ledger account control reads account strings

On journal lines and other transaction entry forms, you enter a full ledger account combined with financial dimensions into a single control. It's important to understand how this control works:

- The control presents a **single combined string** such as `110110-001-025-ProjectA` and uses the **delimiter character to split it into individual segments**.
- The flyout that shows separate segment fields in the lookup is a visual aid to help you fill out this single string. The system still reads the final combined string, not the individual segment fields in the flyout.
- When you select or confirm a value, the control splits the combined string on every occurrence of the delimiter character to identify each segment.

This means that if a dimension value (for example, a project ID like `P-001`) contains the same character as the chart of accounts delimiter (for example, `-`), the control splits the value incorrectly. It treats `P` and `001` as separate segments instead of the single value `P-001`. This typically produces a **"Dimension value does not exist"** error.

### Why values work in some places but not others

You might notice that you can successfully enter a value that contains the delimiter character in other areas of the application, for example:

- **Master data fields** – Fields like **Account number**, **Customer account**, or **Project ID** are standalone fields. They accept free-form text and don't split on delimiter characters.
- **Default dimension tab pages** – These pages use individual entry fields, one for each dimension. Because each field handles a single dimension independently, delimiter characters in the value don't cause a conflict.

The issue occurs only in the **ledger account control** on journal lines and similar forms, where the full account-plus-dimensions string is read as a single value and split by the delimiter. This is why a value like `P-001` can be entered as a project ID or in a default dimension field, but fails when it appears in a ledger account string on a journal line.

### Readability concerns

Delimiter conflicts aren't only a system problem. Even when a person reads a ledger account string like `110110-P-001-025`, it's ambiguous. You can't easily tell whether `P-001` is a single dimension value or two separate segments. This ambiguity increases the risk of data entry errors and makes account strings harder to read, interpret, and troubleshoot.

Choosing a unique delimiter that doesn't appear in any dimension values makes account strings clear for both the system and the people who read them.

## Update the delimiter

If there's a conflict with the chart of accounts, you can change the chart of accounts delimiter and the project/subproject ID format. No other dimension delimiters can be changed.

- **Chart of accounts delimiter** – Go to **General ledger parameters** > **Chart of accounts and dimensions** > **Change delimiter** to select a new delimiter character.
- **Project/subproject ID format** – If the only conflict is the project/subproject ID format, go to **Project management and accounting parameters** > **General** > **Modify subproject format** to change the separator character used in project and subproject IDs.

### Rename existing project IDs

If you've already created projects that use a conflicting character (for example, a dash) in their IDs, changing the subproject format only affects new projects. To update existing project IDs, use the **Rename** function:

1. Go to **Project management and accounting** > **Projects** > **All projects**.
2. Select a project that contains the conflicting delimiter character in its project ID.
3. Select **Rename** to open the rename dialog.
4. Enter a new project ID that doesn't contain the chart of accounts delimiter character.
5. Repeat this process for each affected project.

> [!TIP]
> Before you rename projects, identify all projects that contain the delimiter character in their ID. Consider choosing a subproject format separator that is unlikely to conflict—for example, a period (`.`) or underscore (`_`)—and then rename existing projects accordingly.

> [!IMPORTANT]
> Renaming a project ID updates references within the project module. Review related integrations and reports to make sure they reflect the updated project IDs.

### Other considerations

Any master data records that serve as financial dimension backing entities—such as vendors, customers, or projects—shouldn't have ID values that use the same character as the chart of accounts delimiter. If you create or import master data with ID values that contain the delimiter character, those values cause the same failures in the ledger account control.

Review your master data naming conventions to make sure no ID values use the delimiter character. This preventive step avoids errors and keeps ledger account strings readable.

## How to determine if your environment requires updated delimiters

If delimiters in your upgraded environment conflict, you might experience the following symptoms:

- **"Dimension value does not exist" errors** when you enter account combinations on journal lines or other transaction entry forms.
- **Instability when entering values** in ledger account or dimension entry fields.
- **A need to always use lookups or the flyout menu** to enter account and dimension combinations, because manually typed values aren't read correctly.

If you encounter any of these symptoms, review your chart of accounts delimiter and compare it against all financial dimension values in your environment. Change the delimiter or rename the conflicting dimension values to resolve the conflict.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

