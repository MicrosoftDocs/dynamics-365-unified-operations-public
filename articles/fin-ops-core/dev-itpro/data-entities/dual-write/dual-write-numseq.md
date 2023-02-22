---
title: How to configure number Sequence and autonumber columns while using dual-write
description: This article describes how to configure the Number sequences in F&O and Autonumber columns in Microsoft Dataverse for business identifiers involved in dual-write. 
author: ramasri
ms.date: 02/21/2023
ms.topic: article
audience: Developer, Application User, IT Pro
ms.reviewer: johnmichalak
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2023-01-12
---

# How to configure number Sequence and autonumber columns while using dual-write

By default, the [Number sequences](../../../fin-ops/organization-administration/number-sequence-overview.md) in finance and operations apps and the [autonumber columns](/powerapps/maker/data-platform/autonumber-fields) of customer engagement applications aren't connected. In a scenario that involves a multi-mastered table, you must either plan for separate number sequence formats, or create a range for each application. Here are some examples:

- In the finance and operations application, use F0001, F0002, F0003. In the customer engagement application, use C0001, C0002, C0003. 
- In the finance and operations application, use US0001 to US4999. In the customer engagement application, use US5000 to US9999. 

When you need to perform a live sync, and for the examples above to work in finance and operations data management, within the data entity mappings make sure that the data field validation for the autonumber field isn't checked.  If there's a business reason to run the validation, we recommend that you review the number sequence settings of the data entities in scope in the finance and operations application. These rules are validated only when running the initial sync, live sync isn't affected. 

During the initial sync, if the field data validation for the autonumber field is enabled, you need to verify the following items for both the customer engagement app and the finance and operation apps:

- The autonumber sequences length match.
- The customer and engagement app numeric sequence value should be in the interval defined by the Smallest and Largest values in the finance and operation apps number sequences settings.
- The constants used must be identical.

The number sequence settings used by data entities such as customers, orders, or quotes in finance and operations apps can be found in **Accounts Receivable parameters** and **Number Sequences**. For more information, see [Number sequences](../../../fin-ops/organization-administration/number-sequence-overview.md)

If during dual-write initial sync, you observe an error message similar to **‘Field ABC does not allow editing. Number CE-20000001 does not match format ######. Validations failed.’** or **‘Field ABC does not allow editing. Highest number allowed is 4999. Validations failed.’**, you need to review the customer and engagement app autonumber sequences and finance and operations app autonumber number settings and update accordingly. Another alternative is to skip the validation by disabling field validation at data entity level in finance and operations data management.

If a table is created in only one system, set up the number sequence in the source app only. For more information, see [Autonumber columns](/powerapps/maker/data-platform/autonumber-fields).


## How to disable field validation in finance and operations data entity for dual-write initial sync

To disable filed validation in finance and operations data entity for dual-write initial sync, follow these steps.

1. Navigate to finance and operations Data Management > Data entities.
1. Select to update a data entity, and for the autonumber field uncheck the **Call validate Field** method.
1. Select **Save**. 

For more information, see [Optimize data migration for finance and operations apps](../../sysadmin/optimize-data-migration.md).

![Screenshot of the Map staging to target screen with the Call validate Field method highlighted for the SALESORDERNUMBER field](media/numseq-1.png)


## Finance and operations number sequence settings

When working with autonumbering in finance and operations apps, it's important to understand the [number sequence settings](../../../fin-ops/organization-administration/number-sequence-overview.md): 

![Screenshot of the General setup box for number allocation](media/numseq-2.png)

- **Manual**, it should be set to **No** if you want the system to generate values. 
- **Smallest** defines the lowest numeric value allowed for the sequence.
- **Largest** defines the highest numeric value allowed for the sequence.
- **Next** indicates the next numeric value to use in the number sequence.
- **To a higher number** and **To a lower number** flags allow users to enter a value higher or lower than the **Next** value. 
- **Continuous** avoids gaps and enables reusing values in case records are deleted. You should carefully analyze performance impact if there's a requirement to enable this feature.

Also in the number sequence, you can have different segments that can be used to compose the full value, such as constants or company name:

![Screenshot of the Segments dialog box that shows a Constant value of CE with 6 numbers and a format of CE######](media/numseq-3.png)

Once you enable data validation and confirm the format of the column (for example, the Sales Order Number) on Dataverse matches the number sequence, the user may still encounter the following error messages. 

|Error Message|Cause|
|-----|----|
|Field [Field name] does not allow editing. Invalid specification of Sales order Number sequence Sale_293 does not allow change to a higher number. Validations failed | The number sequence setup doesn’t allow editing. This error occurs when the settings for **Manual**, **To a Lower Number** (under allow user change), or **To a Higher Number** (under allow user change) are set to **No**. To fix this issue, enable one of these settings, and the issue will resolve. |
|Incoming [Field name] < Lowest number allowed is 1000000. Validations failed | The incoming values (numeric part) need to be within the finance and operations number sequence number allocation range. (The number should be less than the largest value.) |
|Incoming [Field name] > highest number allowed is NNN (say: 1000000.) Validations failed | The incoming values (numeric part) need to be within the F&O number sequence number allocation range. (Should be greater than smallest value) . |


## Dataverse autonumbering 
[Autonumber columns](/power-apps/maker/data-platform/autonumber-fields) are Dataverse columns that automatically generate alphanumeric strings whenever they're created. Makers can customize the format of these columns to their liking, and then rely on the system to generate matching values that automatically fill them in at runtime. For example, sales order number set up as autonumber type in Dataverse:

![Screenshot of the Edit column dialog box](media/numseq-4.png)

## Prevent counter increments in finance and operations apps during initial sync 

During initial sync, if you don't want to increase the finance and operations counter when Dataverse records get created with initial sync, for the respective finance and operations numbering sequence, set the value of **Continuous** to **Yes**. 

## Largest value reached in a finance and operations number sequence settings

When the largest value is reached, an error message displays similar to **'Number sequence [number] has been exceeded. Number selection is canceled’**. Resolve this error by increasing the largest value and/or the alphanumeric segment format length. For more information, see [Number sequences](../../../fin-ops/organization-administration/number-sequence-overview.md).
 




