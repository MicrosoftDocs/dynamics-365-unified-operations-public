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

This article provides answers to frequently asked questions about Dual-write async in Dynamics 365 finance and operations.

## What does eventual consistency mean in the context of Async mode? 

Eventual consistency for distributed systems (Dynamics 365 finance and operations and dataverse applications) means that the data is available in a finite time and is eventually consistent based 
on the business validations and logical constraints imposed by either platform. The async process decouples live transactions from committing the transaction at the same instant. The data movement is offloaded to
an internal processing queue to be sequenced and transferred by a background process. Async doesn't replicate the transaction as the platform limits impacts the performance of data movement and constricting the scalability of data movement. Async uses parallelization and dependency graphs to scale the data movement in an optimal way defined by the parameters on the integration job (namely sequence and conflict management).  

## Which type of entities should be used for Async? 

Entities that can be grouped as part of a single transaction and are expected to have high volumes are good candidates for async. For example, worksheet header and worksheet lines are grouped in a single 
transaction where one or few header rows may end up having multiple child rows. Such entities routinely fail on live sync due to limits of transaction (timeout and size).  It's recommended to check for functional correctness of data movement based on the application logic as some logic may be hardwired for real time sync and not for eventual consistency.  

        
## What entities are supported for Async? 
During public preview, application entities are being evaluating that may not work for async. 

### Which type of operations does Async support? 
Async is supported for create and update operations only. If the transaction has a delete operation, then it goes through as a live sync operation and it skips the async pipeline. From the insights gained on 
telemetry we observed that delete operations are dependent on relationships which can't be easily removed from either system or have a higher chance of failure in an eventual consistency model.  

## What happens if a transaction has entities configured in live sync and Async? 
If a transaction has a combination of entities configured as live sync and asynchronous, it fails with an error providing which entities are misconfigured. Application customers are expected to fine tune 
their Async and live sync configuration. The transaction is supposed to have either all asynchronous or synchronous entities. An exception to the rule is deletes which are always synchronous.  

### What does primary for conflict detection mean? 

If the same record gets edited at the same time between both systems, Dynamics 365 finance and operations and Dataverse applications, conflict detection checks which side is the primary and override
the record from that side. For example, if Dynamics 365 finance and operations is the primary for conflict detection, the finance and operations record overrides the Dataverse record. The update from Dataverse to 
Dynamics 365 finance and operations is rejected. Since it's eventually consistent, conflict detection depends upon a snapshot in time and not the record time, as records may not have the time field and 
clocks between systems are not coordinated.  

### How does sequencing of entities impact within a group? 
Sequencing defines the priority order of execution. The lower the number the higher the priority order of execution. This sequencing helps address referential integrity from a data perspective.  
 

### How are the errors categorized? 
Errors are categorized as follows: 
 - Application failure: Any failures because of business validations or logical errors are categorized as application failures.
 - System failure: Any failures due to unresolvable system errors are categorized as system failures. These can be retried and if the “record version” is the latest then it will get synced.
 - Concurrency failures: In eventual consistency models, sometimes the records being processed aren't the latest. In such cases, the records are skipped as concurrency failures. This is to avoid multiple phantom 
updates for the same record. Such failures are not retriable.
 - Conflict failures - Any failures that run into conflict mentioned in the conflict detection FAQ are logged as conflict failures. These aren't visible on the sync errors but are visible on the backend table. 
 

### Does Async use DIXF for import or export from FnO ? 
Async doesn't use DIXF for data import or export to finance and operations. The technology stack uses internal sequencing and queues to manage data movement. The queues don't hold data but references of information to help with data movement.  


### How does Dual-write Async compare to the asynchronous data synch capability in Data integrator tool? 
Data integrator also supports asynchronous data sync between Dynamics 365 finance and operations and Dataverse, but there are some fundamental differences between the two others than the technology stack.  

 

|Capability | Dual-write Async | Data integrator  |
|--------|---------|-------------|
| Supports bi-directional sync | Yes |No (requires custom logic).  |
|Loopback control and conflict management to ensure data integrity  | Yes |Needs application layer customizations (to ensure bidirectional synch does not trigger multiple writes of the same record) |
| Support for functionality of DW sync like templates, company striping, OOB default mappings. | Yes | Limited templates and is not applicable for DW maps. |
| Nature of sync | Just in time event driven.  Not schedule based. |Based on schedule.  Limits imposed by number of recurring jobs. |

