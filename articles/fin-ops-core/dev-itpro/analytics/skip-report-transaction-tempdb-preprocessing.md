---
title: Reduce long-running transactions in TempDB preprocessing SSRS reports
description: Opt out your TempDB preprocessing report of the framework's transaction scope to reduce long-running transactions and tempDB log pressure.
author: ishaankochar
ms.author: ishaankochar
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/24/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2026-06-16
ms.dyn365.ops.version: Platform update 55
---

# Reduce long-running transactions in TempDB preprocessing reports

[!include [banner](../includes/banner.md)]

This article explains how to reduce long-running transactions and tempDB transaction log pressure caused by preprocessing SSRS reports that use the TempDB pattern, by opting out of the reporting framework's transaction scope.

This article is for anyone who maintains custom SSRS reports and whose Report Data Provider (RDP) class extends `SrsReportDataProviderPreProcessTempDB`.

## Applies to

Platform Update 55 and later. Every currently supported environment includes the fix.

## Background

Reports that use the TempDB preprocessing pattern stage their results in temporary database tables during a preprocessing step. By default, the reporting framework wraps the entire preprocessing step in a single transaction scope and commits only after preprocessing finishes.

On cloud deployments backed by Azure SQL, the tempDB transaction log is a shared resource. While a long-lived transaction stays open, log space can't be released. For reports that process large data sets, this behavior can hold a transaction open for the full duration of preprocessing, delay log truncation, and in extreme cases, fill the tempDB log and impact other workloads on the same database.

## What this capability changes

The framework exposes an opt-in switch (`parmSkipReportTransaction`) that lets a report data provider skip the framework's transaction scope. When a report opts in:

- The framework no longer opens transactions around your `processReport` method.
- Each statement you execute commits independently.
- Transaction log space is released as work progresses, instead of being held until the end of preprocessing.

This change isn't a runtime optimization for the report itself. The report does the same amount of work in roughly the same amount of time. What changes is the transaction boundary, which improves the health of the shared environment.

## When to use it

For any report that extends `SrsReportDataProviderPreProcessTempDB` and processes meaningful data volumes, **opting in is the recommended default**. The legacy behavior (a framework-managed transaction wrapping the entire preprocessing step) exists for historical reasons, not because it's the better design. Holding a single transaction open during preprocessing increases tempDB log pressure and can contend with other operations running in your environment at the same time: batch jobs, other reports, and interactive users.

The only valid reason to keep the legacy behavior is when your preprocessing step has a genuine business requirement for atomic rollback of the entire step, and the work can't be restructured into explicit transaction boundaries. This situation is uncommon. "It's easier to leave it as-is" isn't a valid reason. The transaction management you take on is straightforward and is fully covered in the next section.

## How to opt in

Override `parmSkipReportTransaction` in your report data provider so it returns `true`. The recommended pattern mirrors the platform team's reference implementation:

```xpp
public class MyLargeReportDP extends SrsReportDataProviderPreProcessTempDB
{
    public boolean parmSkipReportTransaction(boolean _skipReportTransaction = skipReportTransaction)
    {
        skipReportTransaction = true;
        return skipReportTransaction;
    }

    public void processReport()
    {
        // Your preprocessing logic.
        // See "Manage your own transactions" below.
    }
}
```

The override is read at run time, so the change is scoped to the report data providers you explicitly opt in to. All other reports continue to behave as before.

## Important: manage your own transactions

When you opt in, the framework removes **two** transactions that previously surrounded your `processReport` call:

| Transaction | What it covered | What replaces it when you opt in |
|---|---|---|
| Ambient transaction (`ttsbegin` / `ttscommit`) | Regular table operations in `processReport` | You wrap them yourself with `ttsbegin;` / `ttscommit;` where needed. |
| User connection transaction (`userConnection.ttsBegin()` / `ttsCommit()`) | Operations against tables attached to the report's user connection (the temp tables) | You wrap them yourself with `parmUserConnection().ttsBegin()` / `ttsCommit()`. |

The most common mistake is updating or deleting a user-connection-bound record without an open transaction on that connection. You see the following error message:

> Cannot select a record for update when the transaction is not started on the user connection attached. You need to begin transaction on the user connection first.

A plain `ttsbegin;` doesn't resolve this issue. The data tables are on the user connection, not the ambient connection. Begin the transaction on the user connection explicitly:

```xpp
public void processReport()
{
    UserConnection userConnection = this.parmUserConnection();

    // Wrap operations that update or delete user-connection-bound records.
    userConnection.ttsBegin();
    // selectForUpdate / update() / delete() against temp tables
    userConnection.ttsCommit();

    // Wrap operations against regular (non-temp) tables if they need atomicity.
    ttsbegin;
    // updates against regular tables
    ttscommit;
}
```

Guidelines:

- Prefer set-based operations (`insert_recordset`, `update_recordset`, `delete_from`). They minimize the time any transaction stays open.
- Watch for silent row-by-row downgrades. A set-based statement that is internally downgraded to row-by-row execution (for example, because a data event handler is registered on the table) reintroduces the same long-running pattern you were trying to avoid. Where possible, restructure the code or remove the cause of the downgrade.
- Keep each explicit transaction as small as possible. Wrapping the whole `processReport` body defeats the purpose of opting in.

## How to opt out

Opt-out is the default. To revert a report you previously opted in, change the override to return `false` or remove the override entirely, and redeploy.

## Things to keep in mind

- **No automatic rollback.** A failure partway through preprocessing no longer rolls back the whole step. If a section needs all-or-nothing behavior, define an explicit transaction boundary around it (on the right connection).
- **Review customizations.** Code paths that update or delete records during preprocessing are the most common source of the user-connection error. Audit them before enabling the switch.
- **Validate report output.** Confirm the report produces the same output as before, particularly in failure and cancellation scenarios.

## Recommended rollout

Roll out the change gradually so you can isolate and revert any individual report quickly.

1. **Development / test.** Opt in one report at a time. Exercise the update/delete paths and any failure paths. Confirm the report produces correct output.
1. **Sandbox (UAT) with production-like data.** Validate correctness at realistic scale and confirm that the long-running transaction is gone.
1. **Production.** Enable for a small set of high-impact reports first, then expand.

## Common issues

| Symptom | Likely cause | Action |
|---|---|---|
| "Can't select a record for update when the transaction isn't started on the user connection attached." | An update or delete on a user-connection-bound table is no longer inside a transaction. | Wrap the affected statements in `parmUserConnection().ttsBegin()` / `ttsCommit()`. A plain `ttsbegin` doesn't resolve this issue. |
| Partial or inconsistent data after a failure | No explicit transaction boundary around logic that needs atomicity. | Add an explicit transaction block around the section that must be all-or-nothing, on the correct connection (ambient or user connection). |
| Report compiles but `parmSkipReportTransaction` is reported as unknown. | Environment is on a platform build older than PU55. | Update the environment to a current platform release. |
