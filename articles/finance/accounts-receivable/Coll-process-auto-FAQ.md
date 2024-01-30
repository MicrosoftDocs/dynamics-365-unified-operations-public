---
# required metadata

title: Collections coordinator summary
description: This article answers some frequently asked questions about collections process automation and how it relates to the setup of the collection letter sequence.
author: JodiChristiansen
ms.date: 08/02/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.24
ms.collection: bap-ai-copilot   

---
# Collections process automation FAQ

This article answers some frequently asked questions about the setup of Collections process automation and how it relates to the collections letter sequence and setup. 

To open the Collections process automation parameters go to **Accounts receivable > Setup > Accounts receivable parameters > Collections process automation** and select the **General tab**. To setup the Collections process automation go to **Credit and collections > Setup > Collections process setup**. 

### Does the Collections process setup replace the Collection letter sequence?
No, they work together, and both need to be set up.

### Does the “Days” in the Collection letter sequence need to match the “Days in relation to invoice due date” in Collections process setup?
No, they should not match. The **Days** field on the Collection letter sequence is the grace days allowed. The grace period for collection letter 1 is relative to the due date on the invoice. The grace period for collection letters 2 and higher is relative to the date that the previous collection letter is posted or printed. *See Create a collection letter sequence - Finance | Dynamics 365 | Microsoft Learn for more information*. 
On the Collections process setup, Process details, the **Days in relation to due date** is the number of days after the invoice is due. It is not in relation to the step before. See question #4.

### When running Collections process automation can you set it to run as of a specific date? 
No, it always runs as of today’s date. If there are errors when running you can run it again but when successful, it will not run more than once per day. 

### How should the Collections process automation be set up to use a Collection letter sequence? 
Here is one example of how to set it up. The Collection letter sequence is set up with three collection letters. There are more columns available on the page, this is just for illustration purposes. 

| **Collection letter code**   | **Description**      | **Currency** | **Days** |
|------------------------------|----------------------|--------------|----------|
| Collection letter 1          | First notification   | USD          |    1     |
| Collection letter 2          | Second notification  | USD          |    6     |
| Collection                   | Final notification   | USD          |    7     |

This means that if using the standard Create collection letters process the first collection letter is created 1 day after the due date. The second collection letter is created 6 days after the first collection letter (7 days after the due date). The final collection letter is created 7 days after the second collection letter (14 days after the due date). 
In Collections process setup this is how you could setup the Action type of Collection letter to create the collection letters using the collection letter sequence above. There are more columns available on the page, this is just for illustration purposes.

| **Description** | **Action type**   | **Business document**      | **When**               | **Days in relation to invoice due date** | **Recipient** |
|-----------------|-------------------|----------------------------|------------------------|------------------------------------------|---------------|
| First notice    | Collection letter | Collection per customer    | After invoice due date |                    1                     |     None      |    
| Second notice   | Collection letter | Collection per customer    | After invoice due date |                    7                     |     None      |    
| Final notice    | Collection letter | Collection per customer    | After invoice due date |                    14                    |     None      | 

Collection letters are always created per customer (not per transaction) using Collections process automation.
You cannot choose a Business document like Collection letter 1 because this is already setup in the Collection letter sequence and will be used. Collections process automation only finds what step (process) should be run. The Collection letter sequence is still used to create the collection letters. 

### Why does the Process simulation results only display Collection letter? Does this mean it will create the Final notification? 
No,  this means that it will create a collection letter according to the collection letter sequence. When Collections process automation runs it only identifies which step of the process to do, based on the oldest invoice due. If that step is a collection letter, then it does use the collection letter sequence. It does not display which collection letter is created. 

Using the setup above the collection letters are created based on the date when process automation runs:
 - If running the collection process automation on January 16 it would create Collection letter 1 in the sequence because it is one day after the invoice due date.
 - If running the collection process automation on January 22 it would create collection letter 2 because it is 7 days after the invoice due date.
 - If running the collection process automation on January 29 or later it would create collection letter 3 because it is 14 days after the invoice due date.

### Why did collections process automation skip creating the collection letters and only did the last step, like creating an activity?
A new parameter was added in 10.0.39 to solve this issue. It is best explained with this example. Collections process automation steps are setup as follows: 

| **Description** | **Action type**   | **Business document**    | **When**                | **Days in relation to invoice due date** | **Pre-dunning** | **Recipient** |
|-----------------|-------------------|--------------------------|-------------------------|------------------------------------------|-----------------|---------------|
| Pre-dunning     | Email             | User-defined             | Before invoice due date |                    5                     |       Yes       |    None       |
| First notice    | Collection letter | Collection per customer  | After invoice due date  |                    1                     |       No        |    None       |    
| Second notice   | Collection letter | Collection per customer  | After invoice due date  |                    7                     |       No        |    None       |    
| Final notice    | Collection letter | Collection per customer  | After invoice due date  |                    14                    |       No        |    None       | 
| Create activity | Activity          | User-defined             | After invoice due date  |                    15                    |       No        |    None       |

A customer invoice is due on January 15 but now in the Collections process setup I added 2 more steps, one Email and one Activity.
 - If Collections process automation runs on January 10 an email is sent to the customer as a reminder that an invoice is coming due. This is the pre-dunning step.
 - If the collections status of the invoice has changed to **Disputed** or **Promised to pay**, then Collections process automation will skip that invoice when processing. When the collections status is changed to **Resolved** or **Promise to pay broken** and the invoice is overdue the Collections process automation will pick up the invoice. If it is January 24 when the status is updated and Collections process runs (9 days past due) the step that is closet to that date is the Second notice so that is the step runs.
 - If the collections status is updated on February 2 (17 days past due) the closet step is the Create activity and only an activity is created.
 - If you want the collections process automation to start with the first step that is relevant (in this case it should start with Collection letter 1) then mark the option **Track step in collections process automation** under Accounts receivable > Setup > Accounts receivable parameters > Collections process automation. Collection letter 1 will be sent on February 2. Collections process automation will continue to run and create the remaining collection letters and the activity based on the February 2 date.
