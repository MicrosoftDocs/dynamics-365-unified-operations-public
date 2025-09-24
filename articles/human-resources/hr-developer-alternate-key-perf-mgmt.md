---
title: Alternate keys in performance management tables
description: This article discribes new alternate keys in performance management tables.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.search.form:
ms.topic: how-to
ms.date: 05/13/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Alternate keys in performance management tables

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The following table shows the fields that are available as alternate keys in Microsoft Dynamics 365 Human Resources release 10.0.40 and later to enable set-based operations on data entities for specific tables in performance management.

| Table | Field |
|---|---|
| HcmPerfJournalLinks | LinkId |
| HcmPerfJournalComment | CommentId |
| HcmPerfJournal | EntryId |
| HcmDiscussionTemplate | TemplateId |

## Upgrade error

When you upgrade the environments, some of them might encounter the following error because of customizations or old demo data:

> Exception: System.InvalidOperationException: Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name.

> [!NOTE]
> Uniqueness for the preceding fields is enforced as part of previous upgrades. Because of customizations, back-end database interventions, or very old demo data, fields that contain non-unique records lead to DBsync errors and upgrade failure.

### Mitigation

To avoid the error, follow these steps before you upgrade the environments.

1. Go to **Batch job**, or go to **System administration** \> **Inquiries** \> **Batch job**.
2. Filter **Job description** by each of the following values for specific tables:

    - HcmPerfJournalLinksUpdateLinkIds.updateLinkIds
    - HcmPerfJournalCommentUpdateCommentIds.updateCommentIds
    - HcmPerfJournalUpdateEntryIds.updateEntryIds
    - HcmDiscussionTemplateUpdateTemplateIds.updateTemplateIds

    > [!NOTE]
    > The selected batch job should have a batch task. Select the batch job that contains tasks.

3. Change the status of the batch job to **Waiting**. The job is rerun and removes the duplicates for the specific table.
4. You can now start the upgrade.

> [!NOTE]
> If you don't see the batch job, or if you encounter an error after you run it, contact Microsoft Support.
