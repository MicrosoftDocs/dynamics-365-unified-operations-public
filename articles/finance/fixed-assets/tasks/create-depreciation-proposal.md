---
title: Create a depreciation proposal
description: Learn how depreciation batch proposals work and explains how to propose depreciation for fixed assets, including a step-by-step process. 
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 07/02/2025
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

This article describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. Alongside the depreciation performance improvements introduced as preview features in Dynamics 365 Finance version 10.0.44. This task uses the USMF demo company and the accountant role.


## Create a depreciation proposal
1. Go to **Fixed assets > Journal entries > Create depreciation proposal**.
2. In the **Name of journal** field, select an option from the drop-down menu.
3. In the **To date** field, enter a date.

    - Select the **Summarize depreciation** option to summarize monthly depreciations into one journal line.  
    - For example, if the **To date** value is March 31, 2022, the following description is generated: **Depreciation since January 31, 2022**. The **Date** field on the proposed journal lines is then set to March 31, 2022.  
    - The depreciation proposal can be filtered by asset, asset group, or other criteria using the **Filter** option.  
    - When you use the **Create acquisition or depreciation proposals for fixed assets** page, you can propose depreciation in batches. This is recommended for larger proposals that will use more system resources. If you select the batch option, you can still complete other tasks during that time. When you propose depreciation in this way, depreciation is calculated for value models for fixed assets.  

4. Select **Create journal**.

## Review depreciation entries
1. Go to **Fixed assets > Journal entries > Fixed assets journal**.
2. In the list, find and select the desired record.
3. Select **Lines**.
4. Select **Post**.

> [!NOTE]
> In Microsoft Dynamics Finance 365 version 10.0.42, the automatic splitting of large financial journals feature doesn't include fixed asset journals. Additionally, an option has been added to the fixed asset journal header to enable transactions to be posted via batch jobs. This feature has been backported to version 10.0.39 and later versions through the appropriate update installation.

## Depreciation performance improvements (preview)

Those preview features that are introduced in Microsoft Dynamics Finance 365 version 10.0.44 significantly enhances the efficiency and reliability of the depreciation proposal process by optimizing the way asset transactions are handled in memory (cached). By improving both performance and data management, it leads to faster processing times and greater system stability. 

Improvements include:  
 - Improved performance batch job and task creation - By optimizing how batch jobs and tasks for depreciation proposals are created, the feature speeds up the process when dealing with large volumes of data. This helps reduce the system load, allowing faster execution of these tasks. The batch job’s task description will be **Depreciation task number** and **Journal number**.
 - Support for Fixed Assets with diverse ID formats - Fixed assets may be recorded using different ID formats, such as alphanumeric or numeric-only identifiers. This feature ensures that all fixed assets, regardless of their ID format, are correctly included in the depreciation proposal. This prevents any fixed assets from being overlooked due to inconsistencies in ID formatting.
 - Prevention of empty journal generation - A depreciation proposal task can lead to creation of empty journals, documents that don’t contain any actual depreciation entries. This feature ensures that only valid, populated journals are generated. This reduces the need for manual intervention and cleanup of unnecessary journals.
 - Elimination of duplicate journals due to transient errors - In some cases, temporary or transient system errors could cause multiple journals to be created for the same depreciation proposal, leading to duplication. This feature prevents such duplicates, ensuring that the errors are handled gracefully without creating redundant records. This makes the process more robust and reduces the likelihood of discrepancies in financial reporting.
 - Enhanced transaction caching - The enhanced asset transactions cache improves the system's ability to store asset transaction data in memory, allowing for quicker access during the depreciation process. By reducing the need for repeated database queries, larger volumes of asset data are handled more efficiently, significantly speeding up depreciation calculations, especially when dealing with complex asset histories. In addition, the reduced reliance on database calls lowers the overall system load, freeing up resources for other tasks. This enhancement improves the system’s responsiveness, particularly in environments with high number of users.
 - Better multi-entity proposal support - The feature introduces safety checks and retry capabilities to ensure the proposal can be run for multi-legal entities at the same time.
 - Emphasis on batch mode - This feature is designed to run in batch mode. With a series of best practices recommended for performance gains during the batch distribution phase, in addition to added validations and stability to the process.
 - Improved depreciation proposal performance - The primary benefit of this caching enhancement is the noticeable improvement in the speed and performance of generating depreciation proposals. Organizations with substantial fixed asset portfolios can now process depreciation more efficiently, leading to quicker month-end or year-end closing activities. 

These features work together to optimize the depreciation proposal process by improving both the performance and accuracy of asset depreciation tasks. The enhanced caching of asset transactions significantly reduces processing times, while the improved handling of fixed assets, prevention of empty journals, and elimination of duplication ensure a more reliable and depreciation. By implementing these improvements, organizations can streamline their depreciation processes, minimize manual intervention, and achieve more efficient operations. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
