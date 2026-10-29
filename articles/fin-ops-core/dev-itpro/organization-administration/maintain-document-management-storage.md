---
title: Maintain document management storage
description: Understand document storage, configure retention, verify cleanup, and troubleshoot attachment and storage growth in Dynamics 365 Finance and Supply Chain Management.
author: cabeln
ms.author: cabeln
ms.date: 10/29/2026
ms.topic: how-to
ms.reviewer: twheeloc
ms.search.region: Global
ai-usage: ai-assisted
---

# Maintain document management storage

[!INCLUDE [banner](../../../finance/includes/banner.md)]

## Purpose

Document management storage includes attachment metadata, attachment history, and physical files. These components have related but separate lifecycles.

This article explains how to configure retention, maintain cleanup processes, monitor storage consumption, and troubleshoot growth or attachment-access problems in Dynamics 365 Finance and Supply Chain Management. Use it with [Configure document management](configure-document-management.md).

## Before you begin

Review retention obligations and storage capacity before you change configuration or resume cleanup.

### Review storage capacity and licensing

The [Finance and operations storage capacity report](/power-platform/admin/finance-operations-storage-capacity) compares storage consumption with licensed entitlement.

> [!IMPORTANT]
> **Current policy and enforcement changes:** The current public capacity guidance states that exceeding storage entitlements doesn't affect service availability and that stored data remains durable. Your organization must nevertheless have the appropriate licenses for its storage use. The guidance also describes possible suspension with reasonable notice when consumption exceeds documented entitlements or usage limits. Don't assume current service availability guarantees continued availability without sufficient entitlement. For changes to enforcement policy or timing, follow the current capacity guidance; this article doesn't announce a future enforcement date.

Monitor consumption, use supported mechanisms to remove information you no longer need to retain, and obtain additional capacity when needed.

### Review retention obligations

> [!IMPORTANT]
> Before changing retention or resuming cleanup, review your audit, regulatory, legal-hold, records-management, and attachment-recovery requirements. Resuming cleanup can remove information that's already eligible for deletion under the existing settings. Don't shorten retention solely to reduce storage consumption.

### Use supported cleanup only

> [!WARNING]
> Don't delete Document management records directly from database tables, such as `DocuRef`, `DocuValue`, or `DocuDeletedRef`, as routine maintenance. Don't directly delete permanent attachment files from Azure Blob storage. Direct database deletion can leave files without the relationships needed to manage them. Direct file deletion can leave valid attachment records pointing to missing content. Use supported application retention and cleanup mechanisms. If these mechanisms don't resolve the issue, contact Microsoft Support for a supported remediation path.

## Understand document storage and retention

Document management connects attachments to business records through metadata in the finance and operations database. File content uses the storage location configured for the document type. An attachment can also be a note or URL rather than a stored file. For storage configuration, see [Configure document types](configure-document-management.md#configure-document-types).

Distinguish these lifecycle components when you investigate storage growth.

| Component | Purpose | Storage-maintenance consideration |
|---|---|---|
| Attachment metadata | Connects an attachment to its business record and associated content. | Metadata and physical files aren't the same thing. Removing one directly can leave the other inconsistent. |
| Document attachment history | Records actions such as attachment creation, pending deletion, restoration, deletion, and movement. | The default history retention is 180 days. History cleanup is separate from attachment-file deletion. |
| Deferred deletion and attachment recovery | Keeps deleted attachments recoverable for a configured period. | The default is 30 days. A value of `0` keeps deleted attachments recoverable indefinitely. |
| Orphaned attachment references | References that remain when the parent business record no longer exists. | These references require orphan-reference processing, not history cleanup. |
| Physical attachment files | Stores the file content associated with file attachments. | Files have a deletion lifecycle distinct from history and attachment metadata. |

### Retention determines eligibility; cleanup performs deletion

A retention setting determines when information becomes eligible for deletion. The corresponding supported cleanup process performs the cleanup.

Changing a retention period isn't itself a cleanup operation. If the relevant process is disabled, inactive, failing, or unable to process an accumulated backlog, eligible information can remain and storage can continue growing.

For example, `DOCUHISTORY` can continue growing even after you configure history retention. Check the attachment-history cleanup process, not just the retention value.

## Configure retention

History retention and deferred deletion serve different purposes. Configure each according to your organization's requirements.

### Configure document attachment history

1. Open **Document management parameters** > **General** > **History**.
2. Set **Enable document history** according to your audit requirements.
3. Review **Number of days to retain history**. The default is 180 days.
4. Verify the associated history-cleanup process. See [Attachment-history cleanup](#attachment-history-cleanup).

History retention applies to attachment-history information. Don't use it as an attachment-recovery setting or expect it to delete attachment files. Disabling history recording doesn't remove an existing history backlog.

### Configure attachment recovery and deferred deletion

1. Open **Document management parameters** > **General** > **Deferred deletion**.
2. Set **Deferred deletion enabled** according to your recovery requirements.
3. Review **Number of days to defer deletion**. The default is 30 days.
4. Verify the existing batch job **Scans for deleted references which have reached the end of their retention period**. See [Verify and resume cleanup processes](#verify-and-resume-cleanup-processes).

This process uses **Number of days to defer deletion** and the attachment's **Deleted date and time** to determine retention. For recovery actions, see [Attachment recovery](configure-document-management.md#attachment-recovery).

> [!NOTE]
> If **Number of days to defer deletion** is `0`, deleted attachments remain recoverable indefinitely. Don't interpret zero as immediate deletion. Use this setting only when indefinite recovery is intentional and consistent with your storage and records-management requirements.

## Maintain the attachment lifecycle

Use the process that corresponds to the lifecycle stage you need to maintain. The following responsibilities aren't interchangeable. The job descriptions shown here are in English; descriptions can be localized or changed in your environment.

### Attachment-history cleanup

The batch job **Deletes the document history records which have reached the end of their retention period** removes history records that exceed the configured history-retention period.

If `DOCUHISTORY` grows, review the history-retention setting and verify this process. Changing the attachment-recovery period or running orphan cleanup doesn't replace history cleanup.

### Orphan-reference cleanup

The batch job **Scan for orphaned document references** addresses attachment references whose parent business record no longer exists.

A valid attachment record whose physical file is missing isn't an orphaned reference merely because the attachment won't open. Orphan cleanup doesn't recreate missing file content.

### Deferred-deletion cleanup

The batch job **Scans for deleted references which have reached the end of their retention period** identifies deleted references that have reached the end of the configured recovery period.

Verify this process when deleted attachments remain retained beyond the intended period. Check the configured value before assuming there's a failure: `0` means indefinite recovery.

Deferred-deletion processing isn't a substitute for history cleanup. Identifying an eligible deleted reference and deleting the physical file are separate stages.

### Physical-file deletion

The batch job **Scan for document files that have been scheduled for physical deletion** processes files that have reached the appropriate stage of the supported deletion lifecycle.

Don't assume that removing history or processing attachment references produces an immediate reduction in file storage. Also, don't assume this process discovers arbitrary files in storage that have no corresponding current application metadata.

### Verify and resume cleanup processes

Review retention obligations before resuming deletion. Use the existing jobs rather than creating duplicate or replacement tasks.

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
2. Locate the jobs described in the preceding sections. Clear filters that could hide inactive jobs. If you can't identify a required job, contact Microsoft Support rather than creating a replacement.
3. Record each job's ID, status, recurrence, next scheduled execution, and any errors. Determine whether it was intentionally withheld, its recurrence expired, it failed, or it's already executing.
4. For a job confirmed as disabled and approved to resume, select **Batch job** > **Functions** > **Change status** > **Waiting**, and then select **OK**. Don't force-cancel a job that's already executing.
5. Confirm that the recurrence is still valid and has a future execution. Follow supported configuration for your version; don't force an arbitrary interval onto a product-managed process.
6. Review task status, available execution history, and messages after execution. Investigate failures rather than relying on the scheduled state.
7. Monitor the storage trend alongside execution results and current attachment activity.

> [!NOTE]
> A **Waiting** status doesn't prove that a recurring job last succeeded: recurring jobs can return to **Waiting** after success or failure. History availability also depends on the job's history-logging configuration. Missing successful-history entries alone don't prove inactivity.

Not every inactive process indicates a failure. For example, cleanup might not be needed when the corresponding feature isn't in use and no retained data remains. If a job repeatedly fails, disables itself unexpectedly, or completes without an understood storage trend, contact Microsoft Support.

For general status controls, recurrence, and history settings, see [Create a batch job](../../fin-ops/sysadmin/create-batch-job.md). Don't use its task-creation procedure to recreate missing Document management system tasks.

### Address an accumulated backlog

If cleanup hasn't operated for an extended period, eligible information can accumulate. Restoring cleanup doesn't guarantee an immediate drop in database or file-storage consumption. A backlog can take many executions to process.

> [!NOTE]
> Retention periods aren't cleanup-completion deadlines. The default 180-day history-retention period and 30-day attachment-recovery period determine eligibility, not how long cleanup takes to finish. History cleanup removes eligible history records; it doesn't remove attachment files. Deleted file attachments pass through deferred-deletion processing and a separate physical-file deletion stage. A completed run of one process doesn't establish that another stage has finished.

Verify that the appropriate process continues operating, investigate errors, and monitor trends. Information still within the approved retention period remains retained.

This article doesn't specify cleanup throughput, a completion time, or a service-level commitment. Don't repeatedly shorten retention, change product-managed schedules, or use direct deletion to force a faster result.

## Monitor storage consumption

Use capacity reporting together with application configuration and cleanup execution results. A retention value alone isn't evidence that cleanup is operating.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. Select **Licensing** > **Capacity add-ons** > **Finance and Operations**.
3. Review the affected environment's reported database and file consumption.
4. Select the value in **Finance and operations database usage** to open the table-level view.
5. Identify large or fast-growing document-related tables, including `DOCUHISTORY` when it's reported.
6. Use **View as chart** to review trends or **Export to CSV** to compare observations over time.
7. Review the corresponding Document management retention settings and cleanup processes.
8. Continue monitoring while a backlog is processed.

The table-level drill-down describes database consumption, not individual physical attachment files. Don't infer file-level causes from a database table's size alone. For current reporting instructions, see [Finance and operations storage capacity](/power-platform/admin/finance-operations-storage-capacity).

### Use supported telemetry and prepare a support request

Use available batch history, messages, and [batch alerts](../sysadmin/batch-processing-overview.md) to investigate failures.

If your environment sends telemetry to Application Insights, supported batch signals and X++ exceptions can provide additional evidence. Follow [Get started with monitoring and telemetry](../monitoring-telemetry/monitoring-getting-started.md), and check [Available telemetry](../monitoring-telemetry/monitoring-available-telemetry.md#batch-telemetry) for the applicable version, build, and signal requirements. Don't assume every environment emits every signal.

When opening a support request, provide the following information through the authorized support channel:

- The environment ID and application version/build.
- The affected business record, legal entity, document type, and attachment context visible in the application.
- The exact application error and the date and time of the failure, including the time zone.
- The relevant job IDs, statuses, scheduled execution times, and available error messages.
- The configured history and deferred-deletion retention values.
- Recent database refresh, copy, or restore operations and the observed storage trend.

Don't include file contents, credentials, or storage access tokens in diagnostic messages. Don't run ad hoc SQL to obtain underlying provider or storage values.

## Troubleshooting questions and answers

Use these answers to match the symptom to the relevant lifecycle stage.

### Why does DOCUHISTORY keep growing even though I reduced the retention period?

Retention determines eligibility; it doesn't delete records by itself. Verify **Deletes the document history records which have reached the end of their retention period** and review its execution results. A backlog can remain after you restore cleanup. Don't repeatedly shorten retention to compensate for a cleanup failure.

### Which Document management cleanup process should I run?

Match the process to the lifecycle stage. History cleanup addresses attachment history. Orphan cleanup addresses references whose parent business record no longer exists. Deferred-deletion processing addresses deleted references after their recovery period. Physical-file deletion handles files that have reached the appropriate deletion stage. See [Maintain the attachment lifecycle](#maintain-the-attachment-lifecycle) for the job descriptions.

### Can I lower retention simply to reduce storage consumption?

No. First confirm your audit, regulatory, legal-hold, records-management, and recovery requirements. A shorter retention period can make additional information eligible for deletion. Consider supported removal of unneeded data and additional licensed capacity without compromising retention obligations.

### Can Microsoft or an administrator delete Document management records directly with SQL?

Direct SQL deletion isn't a supported routine-maintenance approach. It can break relationships between attachment records and physical files. Use application cleanup. If that doesn't resolve the issue, contact Microsoft Support for an appropriate remediation rather than requesting or running a generic deletion script.

### Can I delete attachment files directly from Azure Blob storage?

No, not as routine maintenance. Valid database references can remain after file content is deleted. Use the supported application lifecycle or a specifically supported remediation process.

### Why didn't storage drop immediately after cleanup was enabled?

A substantial backlog can take time to process. Verify execution results and monitor the storage trend. A completed run doesn't establish that all eligible information has been processed or that every stage of physical-file deletion has finished. Don't assume a completion time or keep changing retention to force a reduction.

### Why is file storage still high after a database refresh or environment copy?

A database operation doesn't establish that physical file storage was copied, removed, or reconciled. Review the documented behavior and attachment-copy options for your specific operation. Files can remain without corresponding current metadata. Don't assume ordinary Document management cleanup discovers arbitrary blob-only content. See [Environment copy and document attachments](#environment-copy-and-document-attachments).

### Attachments no longer open after an environment or database movement. What should I check?

Check whether the attachment reference exists, whether its parent business record exists, and whether the file is accessible through the configured storage provider. Review whether the applicable supported attachment-copy operation was required and completed.

If application checks don't establish the cause, contact Microsoft Support with the environment, operation, attachment context, and error message. Don't edit underlying table values or copy and delete blobs manually.

### Can orphan cleanup fix a valid attachment whose physical file is missing?

No. Orphan cleanup addresses a reference whose parent business record no longer exists. It doesn't restore a missing file for an otherwise valid attachment. Missing content requires separate diagnosis and a supported recovery or remediation path.

### What happens if storage-provider information is invalid or missing?

The attachment might not be accessible. Treat this as a diagnosis issue, not permission to delete or alter attachment records. Capture the application error and affected attachment context, and contact Microsoft Support. Don't use ad hoc SQL to inspect or repair underlying provider values.

### Will exceeding licensed storage immediately stop the service?

The current [Finance and operations storage capacity guidance](/power-platform/admin/finance-operations-storage-capacity) states that exceeding storage entitlements doesn't affect service availability and that stored data remains durable. It also requires appropriate licensing and describes possible suspension with reasonable notice when consumption exceeds documented entitlements or usage limits.

These statements aren't a promise of indefinite service without sufficient capacity. Refer to the current guidance and your licensing terms. This article doesn't announce a future enforcement date or a separate enforcement policy.

### How do I know whether cleanup is operating correctly?

Check the relevant process, not just its existence or recurrence. Review execution results and available messages, investigate failures, and compare storage trends with retention settings and attachment activity. A **Waiting** status alone doesn't establish success. See [Verify and resume cleanup processes](#verify-and-resume-cleanup-processes).

### How should I copy attachments between sandbox and production environments?

Use the supported attachment-copy option or procedure for the specific environment movement. Don't assume database copy includes attachment-file copy. If the applicable procedure isn't clear, contact Microsoft Support before the operation. Don't use on-premises migration instructions as a general cloud-to-cloud copy recipe.

### Why can attachments be missing after a point-in-time restore?

A database restore changes attachment metadata, but it doesn't restore physical file storage to the same point in time. Restored metadata can refer to a file that's since been deleted. Files added after the restore point can also remain in storage without corresponding restored metadata.

Don't assume that attachment recovery or orphan cleanup can restore that content. See [Database point-in-time restore](../database/database-point-in-time-restore.md#data-elements-that-need-attention-after-restore) and contact Microsoft Support if you can't establish a supported recovery path.

### Should I enable Use active document tables to reduce storage?

Don't treat this option as a storage-cleanup control. It enables an allow list and disables attachments on tables outside that list. See [Other configuration](configure-document-management.md#other-configuration) for its documented behavior. If the option causes attachment-access problems, contact Microsoft Support before changing a configuration that your organization depends on.

## Environment copy and document attachments

Treat database metadata and physical attachment files as separate parts of an environment movement.

The [database-refresh conditions](../database/database-refresh.md#conditions-of-a-database-refresh) explain that a database refresh alone doesn't copy Azure Blob storage files between environments. Review the supported attachment-copy option or procedure for your operation separately. Don't generalize database-refresh behavior to every environment-copy operation.

The [point-in-time restore guidance](../database/database-point-in-time-restore.md#data-elements-that-need-attention-after-restore) explains that restore changes database references without restoring Azure Blob storage itself. For the on-premises-to-cloud migration scenario specifically, follow [Repeat the migration to production](../lifecycle-services/move-on-prem-to-cloud.md#repeat-the-migration-to-production). Its support-assisted attachment-copy instructions aren't a general procedure for all environment movements.

Before a movement, review the operation's prerequisites and attachment-file handling. Afterward, validate attachment access and check the relevant cleanup processes before resuming normal maintenance. Database refresh sets batch jobs to **Withhold**, so verify their intended state after the operation.

Distinguish these conditions when investigating an attachment or storage issue:

| Condition | What to establish through supported application checks |
|---|---|
| Missing database reference | Whether the expected attachment metadata exists in the target application. |
| Orphaned reference | Whether the attachment reference remains but its parent business record no longer exists. |
| Missing physical file | Whether a valid attachment record points to content that's unavailable in the configured storage location. |
| Physical content without current metadata | Whether content remains in storage without corresponding current application records; contact Microsoft Support when application checks don't expose enough information. |

> [!IMPORTANT]
> Standard Document management cleanup isn't a universal scanner for arbitrary blob-only content. Orphan-reference cleanup doesn't restore missing physical files. Don't use direct database or blob deletion to reconcile these conditions yourself.

## Related information

- [Configure document management](configure-document-management.md).
- [Cleanup routines](../sysadmin/cleanuproutines.md).
- [Finance and operations storage capacity](/power-platform/admin/finance-operations-storage-capacity).
- [Refresh database](../database/database-refresh.md).
- [Database point-in-time restore](../database/database-point-in-time-restore.md).
- [Get started with monitoring and telemetry](../monitoring-telemetry/monitoring-getting-started.md).

## Editorial validation checklist

This section is for draft review only. Resolve these items and remove this section before publication.

- Confirm the four English job descriptions and supported status controls in the applicable product releases. The descriptions are verified against engineering support guidance; localized or customized job descriptions can differ.
- Confirm setup and visibility across supported releases. Don't publish instructions to create missing system tasks or force product-managed recurrence.
- [VALIDATION REQUIRED: add authoritative Copy document attachments Learn URL] The scoped on-premises-to-cloud migration link doesn't replace a general attachment-copy procedure. Confirm the scope and current instructions for the attachment-copy option before changing database-movement procedures.
- [LICENSING/LEGAL VALIDATION REQUIRED] Approve a publishable source for any additional statement about a future capacity-enforcement phase. No future date or transition commitment is asserted here.
- [PRODUCT OWNER VALIDATION REQUIRED: deprecation status, release vehicle, effective version and replacement guidance] Proposed direction: describe **Use active document tables** as on a path to deprecation and advise against new use. Don't publish that policy until approved.
- Recheck retention defaults, capacity navigation, licensing wording, and telemetry prerequisites before publication.
- Confirm the supported cleanup warnings and escalation guidance. Don't add internal SQL, telemetry queries, approval paths, scheduler thresholds, or cleanup completion promises.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
