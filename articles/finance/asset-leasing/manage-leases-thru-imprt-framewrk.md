---
# required metadata

title: Manage leases through the Lease import framework
description: This topic describes the process of using the Lease import framework to adjust multiple leases in a single step.
author: moaamer
manager: Ann Beebe
ms.date: 08/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-18
ms.dyn365.ops.version: 10.0.14
---

# Manage leases through the Lease import framework

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process of using the Lease import framework to adjust multiple leases in a single step. Updating lease using the Lease import framework allows is  useful when integrating Dynamics 365 Finance with external systems where the adjustments are handled externally. Adjusting many leases at once can save time and help ensure more accurate adjustments by reducing the exposure to human error. This capability can also connect Dynamics 365 Finance with external data entities to create a more streamlined process of uploading data.

Asset leasing can integrate with external systems using the following data entities:

- Lease staging
- Payment contract staging
- Executory contract staging

When information is imported into the data entities, you can view and edit the leasing data, such as adjusting a lease, updating nonfinancial information, or adding new leases  before processing.

The system can run 3 different processes through the import suite functionality:

|     Process Type     	|     Description                                    	|
|----------------------	|-----------------------------------------------------	|
|     Add Record       	|     Leases migrated with this process type will create a lease   in the system. The payment schedule will not be confirmed, nor will the   initial recognition journal entry be posted upon migration.                                                                                                                             	|
|     Update Record    	|     Leases migrated with this process type will update field   values for a lease in the system. Only those fields selected in the Update   Fields Selection form will update. It is recommended that non-financial   fields are selected in the Update Fields Selection form as this process type   does not adjust the lease.    	|
|     Adjust Record    	|     Leases migrated with this process type will adjust the   lease causing a financial lease modification. Once processed, the system will   create a new payment schedule with the new inputs from the import suite. The   system will not confirm the payment schedule, nor will it post the adjustment   journal entry.         	|
	
1. Once information is upload through the Data management workspace, navigate to Asset leasing > Lease import framework > Import header. The Import header maintains a list of all imports into the data entities listed above.
2. Select Staging Data to view the lease staging data prior to processing.
3. To compare an individual lease record, select a lease and select Compare. The user should run the Compare process in order to generate the Differences report prior to migrating the lease records. The Compare functionality, compares the values in the staging data to those values for those leases currently in the system. Note: the Compare functionality does not work for leases with the Add record process type as there is nothing to compare against that lease.

 	Note: To compare multiple leases at once, select Compare in Asset leasing > Lease import framework > Periodic > Compare
	
4. The user can view the differences between what is currently in the system and what is in the staging tables for each of the entities by selecting the See differences button on each of the entities within the staging tables.

A window will display to show what the current value is, and what the proposed staging value is.

1. The user can also update the staging value by changing the value in the New Value column and clicking Update Staging.
2. The user can validate leases to ensure the records are suitable to be migrated into the system. The system runs several validations to ensure the record will be successfully migrated into the system prior to migrating lease record. To validate an individual lease, select Validate in the top ribbon.

 	Note: To validate multiple leases at once, select Compare in Asset leasing > Lease import framework > Periodic > Validate
	
3. To process an individual lease, select Migrate lease records in the Import Header. When migrating a lease, the system will perform the action indicated in the process type field.

 	Note: To validate multiple leases at once, select Compare in Asset leasing > Lease import framework > Periodic > Validate
	
4. Once the leases are compared, the user can run a report to view the > differences for each lease included in that import ID. To run the > report for one lease, highlight that lease in the staging data and > click Compare and view report > Differences report.

Note: To validate multiple leases at once, select Compare in Asset leasing > Inquries and reports > Differences report

## Set up update fields

If you're using the **Lease import framework** to update leases, you can select specific fields to update when the process type is **Update record**.

1. Navigate to Asset leasing > Lease Import Framework > Setup > Update field selection:
2. A form will appear where the user can highlight the fields and select the green arrow to move to the Selected fields window. Only those fields in the Selected fields window will be able to be updated through the lease import suite.
