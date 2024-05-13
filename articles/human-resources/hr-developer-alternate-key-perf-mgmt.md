---
title: Alternate keys in performance management tables
description: This article discribes new alternate keys in performance management tables.
author: twheeloc
ms.author: RAM.Magadum
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

## List of fields
To enable the set-based operations on data entities for the below list of tables in performance management, below is a list of fields as alternate keys as part of Dynamics 365 Human Resources release 10.0.40 or 
later.

|Table |                                                 Fields|
|-----|-------|
|HcmPerfJournalLinks                 |     LinkId|
|HcmPerfJournalComment            | CommentId|
|HcmPerfJournal                    |           EntryId|
|HcmDiscussionTemplate              |  TemplateId|

### Upgrade

While upgrading the environments, some of the environments might encounter errors due to customization or old demo data. 
**Exception: System.InvalidOperationException: Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name**.

>[!Note]
> Uniqueness is enforced for these fields as part of previous upgrades. Due to customizations, backend database interventions, or very old demo data, fields containing non-unique records result in DBsync errors and
> the upgrade fails.  

### Mitigation
To avoid the error, follow these steps before upgrading the environment. 
1.	Go to **Batch job** or go to **System administration > Inquiries > Batch job**.
2.	Filter the **Job description** with each of following for specific tables:
	  - HcmPerfJournalLinksUpdateLinkIds.updateLinkIds
    - HcmPerfJournalCommentUpdateCommentIds.updateCommentIds
    - HcmPerfJournalUpdateEntryIds.updateEntryIds
    - HcmDiscussionTemplateUpdateTemplateIds.updateTemplateIds

>[!Note]
> The selected batch job should have a batch task. Select the batch job that contains tasks.

3. Change the status of the batch job to **Waiting**. This re-executes the job and removes the duplicates for the specific table.
4. The upgrade can now be started. 

[!Note] if you don’t see the Batch job or if you run into an error after running the Batch job, contact Microsoft support. 
