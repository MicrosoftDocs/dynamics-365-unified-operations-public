---
title: Dual-write async in finance and operations apps FAQ (preview)
description: Get answers to frequently asked questions about dual-write async in Microsoft Dynamics 365 finance and operations apps.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 09/26/2024
ms.custom:
ms.reviewer: twheeloc
---

# Dual-write async in finance and operations apps FAQ (preview)

[This article is prerelease documentation and is subject to change.]

[!include [banner](../../includes/banner.md)]

This article provides answers to frequently asked questions about dual-write async in Microsoft Dynamics 365 finance and operations apps.

> [!IMPORTANT]
> This feature is a preview feature. Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release, so that customers can get early access and provide feedback.

## What does "eventual consistency" mean in the context of dual-write async?

In eventual consistency for distributed systems (finance and operations apps and Dataverse), data is available for a finite time. It eventually becomes consistent, based on the business validations and logical constraints that one platform or the other imposes. The async process decouples live transactions from committing the transaction at the same instant. The data movement is offloaded to an internal processing queue, so that a background process can sequence and transfer it. Dual-write async doesn't replicate the transaction, because platform limits affect the performance of the data movement and constrain its scalability. Dual-write async uses parallelization and dependency charts to scale the data movement in an optimal way, as defined by the parameters of the integration job.

## Which type of entities should be used for dual-write async?

Entities that can be grouped as part of a single transaction and are expected to have high volumes are good candidates for dual-write async. For example, a worksheet header and worksheet lines are grouped into a single transaction, where one or more header rows might have multiple child rows. During live synchronization, these entities routinely fail because of transaction, time-out, and size limits. We recommend that you check for functional correctness of the data movement based on the application logic, because some logic might be coded for real-time synchronization, not for eventual consistency.

## What entities are supported for dual-write async?

Some application entities that are being evaluated during public preview might not work for dual-write async.

## Which type of operations does dual-write async support?

Dual-write async is supported only for create and update operations. If a transaction has a delete operation, it goes through as a live synchronization operation and skips the async pipeline. Delete operations that are dependent on relationships can't easily be removed from either system, or they have a greater risk of failure in an eventual consistency model.

## What happens if a transaction has entities configured for live synchronization and dual-write async?

If a transaction has a combination of entities that are configured for live synchronization and entities that are configured as asynchronous, it fails. The error message shows which entities are misconfigured. Application customers are expected to fine-tune their dual-write async and live synchronization configuration. A transaction should have either all asynchronous entities or all synchronous entities. Deletes are an exception to the rule, because they are always synchronous.

## What does "primary for conflict detection" mean?

If the same record is edited at the same time in both systems, conflict detection determines which side is primary and overrides the record accordingly. For example, if finance and operations apps are primary for conflict detection, the finance and operations apps record overrides the Dataverse record. The update from Dataverse to finance and operations apps is rejected. Because an eventual consistency model is used, conflict detection depends on a snapshot in time. It doesn't depend on the record time, because records might not have a time field, and clocks aren't coordinated between systems.

## What impact does the sequencing of entities have in a group?

Sequencing defines the priority order of execution. The lower the number, the higher the priority order of execution. This sequencing helps address referential integrity from a data perspective.

## How are errors categorized?

Errors are categorized in the following way:

- **Application failures** – Failures that are a result of business validations or logical errors are categorized as application failures.
- **System failures** – Failures that are a result of unresolvable system errors are categorized as system failures. These failures can be retried. During a retry, if the record version is the latest, it's synced.
- **Concurrency failures** – In eventual consistency models, the records that are being processed sometimes aren't the latest versions. In these cases, the records are skipped, and the failures are categorized as concurrency failures. This behavior helps prevent multiple phantom updates for the same record. These failures can't be retried.
- **Conflict failures** – Failures that encounter the conflict that is mentioned in the conflict detection FAQ are categorized as conflict failures. These failures aren't visible in the synchronization errors. However, they are visible in the back-end table.

## Does dual-write async use DIXF for import into, or export from, finance and operations apps?

No, dual-write async doesn't use the Data Import/Export Framework (DIXF) to import data into, or export it from, finance and operations apps. Instead, the technology stack uses internal sequencing and queues to manage data movement. The queues don't hold data. They hold references to information to help with data movement.

## How does dual-write async compare to the asynchronous data synchronization capability of the Data integrator tool?

Data integrator also supports asynchronous data synchronization between finance and operations apps and Dataverse. However, there are some fundamental differences between the two, besides the technology stack. The following table describes these differences.

| Capability | Dual-write async | Data integrator |
|---|---|---|
| Support for bidirectional synchronization | Yes | No. Custom logic is required. |
| Loopback control and conflict management to ensure data integrity | Yes | Application layer customizations are required to ensure that bidirectional synchronization doesn't trigger multiple writes of the same record. |
| Support for functionality of dual-write synchronization, such as templates, company striping, and out-of-box default mappings | Yes | There are limited templates, and the functionality isn't applicable to dual-write maps. |
| The nature of the synchronization | Synchronization is driven by just-in-time events. | Synchronization is based on a schedule. Limits are imposed by the number of recurring jobs. |
