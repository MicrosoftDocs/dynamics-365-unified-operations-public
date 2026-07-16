---
title: Create a depreciation proposal
description: Learn how depreciation batch proposals work and explains how to propose depreciation for fixed assets, including a step-by-step process. 
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 07/09/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.dyn365.ops.version: Version 7.0.0
---

# Create a depreciation proposal

[!include [banner](../../includes/banner.md)]

This article describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. This task uses the USMF demo company and the accountant role.

## Create a depreciation proposal

1. Go to **Fixed assets > Journal entries > Create depreciation proposal**.
1. In the **Name of journal** field, select an option from the drop-down menu.
1. In the **To date** field, enter a date.

    - Select the **Summarize depreciation** option to summarize monthly depreciations into one journal line.  
    - For example, if the **To date** value is March 31, 2025, the following description is generated: **Depreciation since January 31, 2025**. The **Date** field on the proposed journal lines is then set to March 31, 2025.  
    - Use the **Filter** option to filter the depreciation proposal by asset, asset group, or other criteria.  
    - When you use the **Create acquisition or depreciation proposals for fixed assets** page, you can propose depreciation in batches. This method is recommended for larger proposals that use more system resources. If you select the batch option, you can still complete other tasks during that time. When you propose depreciation in this way, the system calculates depreciation for value models for fixed assets.  

1. Select **Create journal**.

## Review depreciation entries

1. Go to **Fixed assets > Journal entries > Fixed assets journal**.
1. In the list, find and select the desired record.
1. Select **Lines**.
1. Select **Post**.

## Depreciation performance improvements

The deprecation performance features significantly enhance the efficiency and reliability of the depreciation proposal process by optimizing the way the system handles asset transactions in memory (cached). By improving both performance and data management, these features lead to faster processing times and greater system stability.

Improvements include:  

- Improved performance batch job and task creation - By optimizing how the system creates batch jobs and tasks for depreciation proposals, this feature speeds up the process when dealing with large volumes of data. This improvement helps reduce the system load, so these tasks execute faster. The batch job’s task description uses **Depreciation task number** and **Journal number**.
- Support for fixed assets with diverse ID formats - You can record fixed assets using different ID formats, such as alphanumeric or numeric-only identifiers. This feature ensures that all fixed assets, regardless of their ID format, are correctly included in the depreciation proposal. This feature prevents any fixed assets from being overlooked due to inconsistencies in ID formatting.
- Prevention of empty journal generation - A depreciation proposal task can lead to creation of empty journals, which are documents that don't contain any actual depreciation entries. This feature ensures that only valid, populated journals are generated. This feature reduces the need for manual intervention and cleanup of unnecessary journals.
- Elimination of duplicate journals due to transient errors - In some cases, temporary or transient system errors cause multiple journals to be created for the same depreciation proposal, which leads to duplication. This feature prevents such duplicates. It ensures that the system handles errors gracefully without creating redundant records. This improvement makes the process more robust and reduces the likelihood of discrepancies in financial reporting.
- Enhanced transaction caching - The enhanced asset transactions cache improves the system's ability to store asset transaction data in memory, so it can access data quicker during the depreciation process. By reducing the need for repeated database queries, the system handles larger volumes of asset data more efficiently. This improvement significantly speeds up depreciation calculations, especially when dealing with complex asset histories. In addition, the reduced reliance on database calls lowers the overall system load, which frees up resources for other tasks. This enhancement improves the system’s responsiveness, particularly in environments with a high number of users.
- Better multientity proposal support - This feature introduces safety checks and retry capabilities to ensure the proposal can run for multilegal entities at the same time.
- Emphasis on batch mode - This feature is designed to run in batch mode. It includes a series of best practices recommended for performance gains during the batch distribution phase, in addition to added validations and stability to the process.
- Improved depreciation proposal performance - The primary benefit of this caching enhancement is the noticeable improvement in the speed and performance of generating depreciation proposals. Organizations with substantial fixed asset portfolios can now process depreciation more efficiently, which leads to quicker month-end or year-end closing activities.

These features work together to optimize the depreciation proposal process by improving both the performance and accuracy of asset depreciation tasks. The enhanced caching of asset transactions significantly reduces processing times, while the improved handling of fixed assets, prevention of empty journals, and elimination of duplication ensure a more reliable and accurate depreciation process. By implementing these improvements, organizations can streamline their depreciation processes, minimize manual intervention, and achieve more efficient operations.

> [Important!] 
The budget depreciation proposal includes assets in both **Open** and **Not yet acquired** status. The (actual) depreciation proposal includes assets in **Open** status only. Why the amounts differ: For an asset with no posted acquisition, status = **Not yet acquired**, the depreciation engine uses the asset book's proposed Acquisition price as the depreciable base. This lets the budget proposal forecast depreciation for planned assets that haven't been acquired yet. The actual depreciation run excludes those assets until they are acquired. As a result, the budget total legitimately exceeds the actual total, and the two proposals won't match.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
