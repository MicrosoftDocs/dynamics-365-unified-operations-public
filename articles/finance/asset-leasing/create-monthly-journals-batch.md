---
# required metadata

title: Confirm payment schedules in batch
description:  This topic describes the process of creating journal entries in batch to increase efficiency when recording the monthly lease expense.
author: moaamer
manager: Ann Beebe
ms.date: 08/07/2020
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
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: 10.0.14
---

# Create monthly journal entries in batch

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process of creating journal entries in batch to increase efficiency when recording the monthly lease expense. The batch processing can be used for journal entries from multiple schedules, including lease payments, liability amortization, right-of-use asset amortization, and executory costs expenses. It can also be used to initially recognize multiple leases at once, or to perform transition adjustments for multiple leases at once.

1.	To setup a batch job or to process payment invoices, depreciation, or interest for multiple leases, navigate to (**Asset leasing > Periodic > Batch journal creation**).
2.	A parameters diaglog will appear where you can select the schedule that the journal entries will be created from, as well as whether to run the batch process for certain entities, lease groups, or individual lease books.

|     Name                      	|     Description                                                                                                                                                                                                           	|
|-------------------------------	|------------------------------------------	|
|     Legal Entity              	|     Select the legal entity in which to create journal   entries. Note: this field will be disabled if the Cross Entity Batch   parameter is disabled in the Lease Posting Parameters.                                    	|
|     Select Schedule           	|     Select the schedule from which the journal entries will be   created.                                                                                                                                                 	|
|     From Date                 	|     Select the starting date from which the journal entries   will be created. The application will create all applicable journal entries   that fall between the From Date and To Date.                                  	|
|     To Date                   	|     Select the ending date of the period the journal entries   will be created.                                                                                                                                           	|
|     Summarize Entry           	|     This field gives the user the option to consolidate the   entry for each lease. Select “Yes” to consolidate multiple entries from one   schedule into a single journal entry.                                         	|
|     Posting Date              	|     If the Summarize entry field is enabled, this field will   appear and will determine the date on which the entries will post                                                                                          	|
|     Post                      	|     Select “Yes” if the journal entries will be simultaneously   created and posted. If “No” is selected, the journal entries will be created,   but the user will have to go into the journal and post them manually.    	|
|     Book ID                   	|     Select the lease book on which the batch process will be   run. If no lease or lease group is selected, the application will run the   batch process on all applicable leases for that given legal entity.            	|
|     Lease Group               	|     Select the lease group on which the batch process will be   run. If no lease group or lease is selected, the application will run the   batch process on all applicable leases for that given legal entity.           	|
|     Expense Type              	|     Select the type of executory expense to create journal   entries against.                                                                                                                                             	|
|     Due In                    	|     Enter the number of days from the system date to create   journal entries based upon the due date from the respective schedule. This   function will allow a user to post journal entries due in the future.          	|
|     Preview before Running    	|     Enable to view the journal entries in a separate preview   window prior to creation or posting.                                                                                                                       	|

If the Preview before running parameter is enabled, a table will appear showing all journal entries that will be posted. The table will also have an Error tab that will show all the expected errors from the batch process, if any exist.

> [!Note]
> The journal entries are created but will not post until the user clicks Run.
