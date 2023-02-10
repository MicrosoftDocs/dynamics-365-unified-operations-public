---
title: How to configure number Sequence and autonumber columns while using dual-write?
description: This article describes how to configure the Number sequences in F&O and Autonumber columns in Dataverse for business identifiers involved in dual-write. 
author: ramasri
ms.date: 01/12/2023
ms.topic: article
audience: Developer, Application User, IT Pro
ms.reviewer: johnmichalak
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2023-01-12
---

# How to configure number Sequence and autonumber columns while using dual-write?

[Number sequences](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview) of finance and operations applications and [autonumber columns](https://learn.microsoft.com/en-us/powerapps/maker/data-platform/autonumber-fields) of customer engagement applications are not connected. In a scenario that involves a multi-mastered table, you must either plan for separate number sequence formats or create a range for each application. Here are some examples:

- In the finance and operations application, use F0001, F0002, F0003. In the customer engagement application, use C0001, C0002, C0003. 
- In the finance and operations application, use US0001 to US4999. In the customer engagement application, use US5000 to US9999. 


If there is a need to perform live sync and for the examples above to work, in F&O data management, within the data entity mappings make sure that the data field 
validation for the autonumber field is un-ticked.  If there is a business reason for the validation to run, its recommended reviewing the F&O number sequence settings 
for the data entities in scope. These rules will be validated only when running initial sync, live sync is not affected. 

If during initial sync the field data validation for the autonumber field is enabled, you need to make sure that for both custom engagement app and finance and operation
apps the next are verified:

- The autonumber sequences length match.
- The customer and engagement app numeric sequence value should be in the interval defined by the Smallest and Largest values in the finance and operation apps number sequences settings.
- The constants used must be identical.

In finance and operations apps, for objects such as customers, orders or quotes the number sequence settings used by the respective data entities are located in 
Accounts receivable  parameters, Number sequences. For more information, see [Number sequences](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview)

If, during dual-write initial sync, you observe error messages such as ‘Field ABC does not allow editing. Number CE-20000001 does not match format ######. 
Validations failed.’ or  ‘Field ABC does not allow editing. Highest number allowed is 4999. Validations failed.’ , you need to review and update accordingly 
the customer and engagement app autonumber sequences and finance and operations app autonumber number settings. Another alternative is to skip the validation 
by disabling field validation at data entity level in F&O data management.
If a table is created in only one system, set up the number sequence in the source app only. For more information, see [Autonumber columns](https://learn.microsoft.com/en-us/powerapps/maker/data-platform/autonumber-fields).


## How to disable field validation in F&O data entity for dual-write initial sync
Navigate to F&O Data Management, Data entities, select to update a data entity, and for the autonumber field un-tick the Call validate Field method and click Save. [Learn more](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/sysadmin/optimize-data-migration)

![NumberSequence-1](media/numseq-1.png)


## F&O number sequence settings
When working with autonumbering in finance and operations apps, it is important to understand the [number sequence settings](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview): 

![NumberSequence-2](media/numseq-2.png)

- **Manual**, it should be No if we want the system to generate values. 
- **Smallest** defines the lowest numeric value allowed for the sequence.
- **Largest** defines the highest numeric value allowed for the sequence.
- **Next** indicates the next numeric value in the number sequence to be used.
- **To a higher number** and **To a lower number** flags allow users to enter a value higher or respectively lower than the Next value. 
- **Continuous** helps to avoid gaps in that it allows to re-use value in case records are deleted. You should carefully analyze performance impact if there is a requirement to enable this feature.

Also in the number sequence, we can have different segments that can be used to compose the full value such as constants or company name:

![NumberSequence-3](media/numseq-3.png)

Once the data validation is enabled and we have confirmed the format of the column (say Sales Order Number) on dataverse and Number Sequence matches, the user might still encounter the following error messages. 

|Error Message|Cause|
|-----|----|
|Field  XXX (say: 'Sales order') does not allow editing. Invalid specification of Sales order Number sequence Sale_293 does not allow change to a higher number. Validations failed | The number sequence setup doesn’t allow editing. This happens when the following settings are set to **No** - Manual, To a Lower Number (under allow user change), To a Higher Number (under allow user change). In order to fix this issue, enable one of these settings, and the issue will resolve. |
|Incoming XXX (say: Sales order no) < Lowest number allowed is 1000000. Validations failed | The incoming values (numeric part) need to be within the F&O number sequence number allocation range. (Should be less than the largest value) |
|Incoming XXX (say: Sales order no) > highest number allowed is NNN (say: 1000000.) Validations failed | The incoming values (numeric part) need to be within the F&O number sequence number allocation range. (Should be greater than smallest value) . |


## Dataverse autonumbering 
[Autonumber columns](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/autonumber-fields) are Dataverse columns that automatically generate alphanumeric strings whenever they are created. Makers can customize the format of these columns 
to their liking, and then rely on the system to generate matching values that automatically fill them in at runtime. For example, sales order number set up as 
autonumber type in Dataverse:

![NumberSequence-4](media/numseq-4.png)

## Prevent counter increments in F&O during initial sync 
During initial sync, if you wish to not increase the F&O counter when Dataverse records get created with initial sync, set in the respective F&O numbering sequence 
the value of Continuous flag to Yes. 

## Reaching largest value in F&O number sequence settings
This will throw an error messages similar to ‘Number sequence ABC has been exceeded. Number selection is cancelled’ .It can be resolved by increasing the largest 
value and/or the alphanumeric segment format length. For more information, see [Number sequences](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).
 




