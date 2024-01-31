---
# required metadata

title: Collections coordinator summary FAQ
description: This article answers some frequently asked questions about collections coordinator summary.
author: JodiChristiansen
ms.date: 01/31/2024
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

This article answers some frequently asked questions about the setup about collections coordinator summary. 

## Collections process automation setup

To set up **Collections process automation**, follow these steps:
1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Collections process automation** to set up the collection process automation parameters.
2. Set up the Collections process automation hierachy, go to **Credit and collections** > **Setup** > **Collections process setup**. 

### Does the Collections process setup replace the Collection letter sequence?
No, they work together, and both need to be set up.

### Do the “Days” in the Collection letter sequence need to match the “Days in relation to invoice due date” in Collections process setup?
No, they shouldn't match. The **Days** field on the **Collection letter sequence** is the grace days allowed. The grace period for **collection letter 1** is relative to the due date on the invoice. The grace period for **Collection letters 2** and greater than the date that the previous collection letter is posted or printed. For more information, see [Create a Collection letter sequence.](./tasks/create-collection-letter-sequence.md). 

On the **Collections process setup** page, **Process details**, the **Days in relation to due date** is the number of days after the invoice is due. It's not in relation to the previous step. 

### When running Collections process automation can it be run as of a specific date? 
No, it always runs as of today’s date. If there are errors when running, run it again. If the run is successful, it won't run more than once per day. 

### How should the Collections process automation be set up to use a Collection letter sequence? 
Below is an example to set up the **Collection letter sequence** with three collection letters. 

| **Collection letter code**   | **Description**      | **Currency** | **Days** |
|------------------------------|----------------------|--------------|----------|
| Collection letter 1          | First notification   | USD          |    1     |
| Collection letter 2          | Second notification  | USD          |    6     |
| Collection                   | Final notification   | USD          |    7     |

The **Create collection letters** process creates the first collection letter one day after the due date. The second collection letter is created six days after the first collection letter (seven days after the due date). The final collection letter is created seven days after the second collection letter (14 days after the due date). 
In **Collections process setup**, set the **Action** type to **Collection letter** to create the collection letters using the collection letter sequence above. 

| **Description** | **Action type**   | **Business document**      | **When**               | **Days in relation to invoice due date** | **Recipient** |
|-----------------|-------------------|----------------------------|------------------------|------------------------------------------|---------------|
| First notice    | Collection letter | Collection per customer    | After invoice due date |                    1                     |     None      |    
| Second notice   | Collection letter | Collection per customer    | After invoice due date |                    7                     |     None      |    
| Final notice    | Collection letter | Collection per customer    | After invoice due date |                    14                    |     None      | 

Collection letters are created per customer (not per transaction) using **Collections process automation**.
You can't choose a business document like **Collection letter 1** because this is set up in the **Collection letter sequence** and is used. Collections process automation only finds what step (process) should be run. The **Collection letter sequence** is used to create the collection letters. 

### Why does the Process simulation results only display Collection letter? Does this mean it creates the Final notification? 
No, it creates a collection letter according to the collection letter sequence. When **Collections process automation** runs it identifies which step of the process to do, based on the oldest invoice due. If that step is a collection letter, then the collection letter sequence is used. It doesn't display which collection letter is created. 

Using the setup above, the collection letters are created based on the date when process automation runs:
 - If running the collection process automation on January 16, it creates **Collection letter 1** because it's one day after the invoice due date.
 - If running the collection process automation on January 22, it creates **Collection letter 2** because it's 7 days after the invoice due date.
 - If running the collection process automation on January 29 or later, it creates **Collection letter 3** because it's 14 days after the invoice due date.

### Why did collections process automation skip creating the collection letters and only did the last step, like creating an activity?
A new parameter was added in Dynamics 365 Finance version 10.0.39 to address this situation. The following example shows this situation. 
The **Collections process automation** steps are set up as follows: 

| **Description** | **Action type**   | **Business document**    | **When**                | **Days in relation to invoice due date** | **Pre-dunning** | **Recipient** |
|-----------------|-------------------|--------------------------|-------------------------|------------------------------------------|-----------------|---------------|
| Pre-dunning     | Email             | User-defined             | Before invoice due date |                    5                     |       Yes       |    None       |
| First notice    | Collection letter | Collection per customer  | After invoice due date  |                    1                     |       No        |    None       |    
| Second notice   | Collection letter | Collection per customer  | After invoice due date  |                    7                     |       No        |    None       |    
| Final notice    | Collection letter | Collection per customer  | After invoice due date  |                    14                    |       No        |    None       | 
| Create activity | Activity          | User-defined             | After invoice due date  |                    15                    |       No        |    None       |

A customer invoice is due on January 15. In **Collections process setup**, two additional steps are added: **Email** and **Activity**.
 - If Collections process automation runs on January 10, an email is sent to the customer as a reminder that an invoice is coming due. This is the pre-dunning step.
 - If the collections status of the invoice has changed to **Disputed** or **Promised to pay**, Collections process automation skips that invoice when processing. When the collections status is changed to **Resolved** or **Promise to pay broken** and the invoice is overdue the Collections process automation picks up the invoice. On January 24, the status is updated and Collections process runs (9 days past due) the step that is closest to that date is the **Second notice** that runs.
 - If the collections status is updated on February 2 (17 days past due), the closest step is **Create activity** and only an activity is created.
 - If you want the collections process automation to start with the first step that is relevant (in this case it should start with Collection letter 1), select the **Track step in collections process automation** option on the **Collections process automation** page. **Collection letter 1** is sent on February 2. Collections process automation will continue to run and create the remaining collection letters and the activity based on the February 2 date.
