---
title: Check for highly variable dimensions 
description: Use a tool to check for highly variable dimensions in Dynamics 365 Finance. These financial dimensions are characterized by values that aren't reused, either individually or in combination with other values.
author: JodiChristiansen
ms.author: JChrist
ms.topic: how-to
ms.date: 05/15/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Check for highly variable dimensions

In Dynamics 365 Finance, managing financial dimensions efficiently is crucial for maintaining performance during key processes like year-end close, trial balance reporting, and consolidation. Highly variable dimensions, those with a large number of distinct values, can significantly impact system performance. To address this issue, Microsoft Dynamics 365 Finance 10.0.45 introduces a feature that identifies and monitors these dimensions. For more information on highly variable dimensions and how to avoid them, see [Highly variable dimensions](high-var-dimensions.md).

## Purpose of the check

The system runs a process called `LedgerDimensionUsageCountCheckAction` to count how many distinct values each financial dimension uses in a fiscal year for each company. This process helps users understand which dimensions might be causing performance problems and provides guidance for smoother financial operations.

## Enable the flights

Several feature flags enable this functionality with the default status disabled. To enable these feature flags, submit a support ticket. The first two feature flags need to be enabled to do the dimension counts, and the last three provide warning messages during the year-end close, trial balance report, and consolidations. To see the warning messages, all five feature flags need to be enabled.

- `LedgerDimensionUsageCountCheckFlight`: Enables the daily check action.
- `LedgerDimensionUsageCountScanFlight`: Enables the monthly scan action.
- `LedgerFiscalCloseHighlyVariableValidationFlight`: Warns users during year-end close if highly variable dimensions are present.
- `LedgerTrialBalanceHighlyVariableValidationFlight`: Alerts users during trial balance reporting.
- `LedgerConsolidateHighlyVariableValidateFlight`: Displays warnings during consolidation if problematic dimensions are used.

## How the check works

1. When you enable `LedgerDimensionUsageCountCheckFlight`, you can view the status of highly variable dimensions in **General Ledger > Period Close > Year-end close**. Select **Dimension usage count check history** in the action pane.
1. The system periodically checks the number of distinct values for each dimension by ledger and fiscal year. You can view the results on the **Dimension usage count check history** page.
1. The system categorizes dimensions based on thresholds:
   - Normal: less than 5,000 values
   - PossibleHigh: 5,000 values
   - High: 10,000 values
   - ExtremeHigh: 50,000 values
1. You can configure the thresholds and parameters in the `LedgerDimensionUsageCountParameters` table.
1. The check typically covers the most recent two fiscal years, including the current year.
1. The system stores results in two tables:
   - `LedgerDimensionUsageCountCheckHistory`: stores process metadata
   - `LedgerDimensionUsageCount`: stores counts and categories for each dimension
1. On the **Dimension usage count check history** page, select **Run dimension usage count check** to run the check and **Delete dimension usage count check** to delete the check.

## Scheduled actions and services

To keep the data up-to-date, this check runs several automated actions:

- `LedgerDimensionUsageCountScanAction` (monthly): Checks for new transactions and flags records for review.
- `LedgerDimensionUsageCountCheckAction` (daily): Executes checks on flagged records.
- `LedgerDimensionUsageCountCheckTask`: Runs the actual service to count dimension values, respecting a time limit (default: 1,800 seconds). If the task exceeds this limit, it resumes the next day.
- `LedgerDimensionUsageCountCheckService`: Performs the query and stores results for dimensions exceeding thresholds.
