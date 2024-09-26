---
title: Dual-write Async FAQ Dynamics 365 finance and operations apps
description: Learn about how to set up and manage errors in dual-write async in Dynamics 365 finance and operations apps.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 09/26/2024
ms.custom:
ms.reviewer: twheeloc
---

# Set up and manage errors in dual-write async in Dynamics 365 finance and operations apps

[!include [banner](../../includes/banner.md)]

This article provides answers to frequently asked questions about Dual-write asynch in Dynamics 365 finance and operations.

What does eventual consistency mean in the context of Async mode? 

Eventual consistency for distributed systems (Dynamics 365 Finance and Operations and Dataverse applications) means that the data would be made available in a finite time and would be eventually consistent based 
on the business validations and logical constraints imposed by either platform. The async process decouples live transaction from committing the transaction at the same instant. It offloads the data movement to
an internal processing queue to be sequenced and transferred by a background process. Async does not replicate the transaction as it would mean that the platform limits of transaction would still impact the 
performance of data movement and constricting the scalability of data movement. Async uses parallelization and dependency graphs to scale the data movement in an optimal way defined by the parameters on the 
integration job (namely sequence and conflict management).  

 

Which type of entities should be used for Async? 

Entities which can be grouped as part of a single transaction and are expected to have high volumes are good candidates for async. For example, worksheet header and worksheet lines are grouped in a single 
transaction where one or few header rows may end up having multiple child rows. Such entities routinely fail on live sync due to limits of transaction (timeout and size).  

However, it is recommended to check for functional correctness of data movement based on the application logic as some logic may be hardwired for real time sync and not for eventual consistency.  

        

What entities are supported for Async? 

In Public preview, there is currently no limitation. During preview, we will be evaluating which application entities may not work for async. 

 

Which type of operations does Async support? 

Async is supported for Create and Update operations only. If the transaction has a delete operation, then it goes through as a live sync operation and it skips the async pipeline. From the insights gained on 
telemetry we observed that delete operations are dependent on relationships which cannot be easily removed from either system or have a higher chance of failure in an eventual consistency model.  

 

What happens if a transaction has entities configured in live sync and Async? 

If a transaction has a combination of entities configured as live sync and asynchronous, it will fail with an error providing which entities are misconfigured. Application customers are expected to fine tune 
their Async and live sync configuration. The transaction is supposed to have either all asynchronous or synchronous entities. An exception to the rule is deletes which are always synchronous.  

 

What does primary for conflict detection mean? 

If the same record gets edited at the same time between both systems, (Dynamics 365 Finance and Operations and Dataverse applications) then conflict detection will check which side is the primary and override
the record from that side. E.g. If Dynamics 365 Finance and Operations is the primary for conflict detection, the Finance and Operations record will override the Dataverse record. The update from Dataverse to 
Dynamics 365 Finance and Operations will be rejected. Since it is eventually consistent, conflict detection depends upon a snapshot in time and not the record time, as records may not have the time field and 
clocks between systems are not coordinated.  

 

How does sequencing of entities impact within a group? 

Sequencing defines the priority order of execution. The lower the number the higher the priority order of execution. This sequencing helps address referential integrity from a data perspective.  

 

How are the errors categorized? 

Errors are categorized as follows: 

Application Failure: Any failures because of business validations or logical errors are categorized as application failures.  

System Failure: Any failures due to unresolvable system errors are categorized as system failures. These can be retried and if the “record version” is the latest then it will get synced. 

Concurrency Failures: In eventual consistency model sometimes the records being processed are not the latest. In such cases the records are skipped as concurrency failures. This is to avoid multiple phantom 
updates for the same record. Such failures are not retriable.  

Conflict Failures: Any failures that run into conflict mentioned in the conflict detection FAQ are logged as conflict failures. These are not visible on the Sync Errors UI but persisted on the backend table 

 

10. Does Async use DIXF for import or export from FnO ? 

Async does not use DIXF for data import or export to FnO. The technology stack uses internal sequencing and queues to manage data movement. The queues do not hold any data but references of information to help 
with data movement.  

 

How does Dual-write Async compare to the asynchronous data synch capability in Data integrator tool? 

Data integrator also supports asynchronous data sync between Dynamics 365 Finance and Operations and Dataverse, but there are some fundamental differences between the two others than the technology stack.  

 

|Capability | Dual-write Async | Data integrator  |
|--------|---------|-------------|
| Supports bi-directional sync | Yes |No (requires custom logic).  |
|Loopback control and conflict management to ensure data integrity  | Yes |Needs application layer customizations (to ensure bidirectional synch does not trigger multiple writes of the same record) |
| Support for functionality of DW sync like templates, company striping, OOB default mappings. | Yes | Limited templates and is not applicable for DW maps. |
| Nature of sync | Just in time event driven.  Not schedule based. |Based on schedule.  Limits imposed by number of recurring jobs. |

