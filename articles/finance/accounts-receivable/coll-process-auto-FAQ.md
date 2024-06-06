---
title: Collections process automation FAQ
description: Access answers to some frequently asked questions about collections process automation, including questions about automation setup.
author: JodiChristiansen
ms.author: jchrist
ms.topic: conceptual
ms.date: 01/31/2024
ms.reviewer: twheeloc
ms.collection: bap-ai-copilot 
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.24
ms.search.form: 
---

# Collections process automation FAQ

This article answers some frequently asked questions about the setup of collections process automation. 

## Collections process automation setup

To set up collections process automation, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**. On the **Collections process automation** tab, set up the parameters for collections process automation.
2. Go to **Credit and collections** \> **Setup** \> **Collections process setup** to set up the collections process automation hierarchy. 

### Does the collections process setup replace the collection letter sequence?

No, the collections process setup and the collection letter sequence work together, and both must be set up.

### Does the "Days" value for the collection letter sequence have to match the "Days in relation to invoice due date" value for the collections process setup?

No, these values shouldn't match. The **Days** field for the collection letter sequence specifies the number of grace days that are allowed. The grace period for the first collection letter is relative to the due date on the invoice. The grace period for the second collection letter is after the date when the previous collection letter is posted or printed. For more information, see [Create a collection letter sequence](./tasks/create-collection-letter-sequence.md). 

On the **Collections process setup** page, under **Process details**, the **Days in relation to due date** field specifies the number of days after the invoice is due. The value isn't in relation to the previous step. 

### Can collections process automation be run as of a specific date? 

No, collections process automation always runs as of the current date. If errors occur while it's running, run it again. After collections process automation is successfully run, it won't run again on the same day. 

### How should collections process automation be set up to use a collection letter sequence?

The following table shows an example where the collection letter sequence is set up with three collection letters. 

| Collection letter code | Description         | Currency | Days |
|------------------------|---------------------|----------|------|
| Collection letter 1    | First notification  | USD      | 1    |
| Collection letter 2    | Second notification | USD      | 6    |
| Collection             | Final notification  | USD      | 7    |

The **Create collection letters** process creates the first collection letter one day after the due date. It creates the second collection letter six days after the first collection letter (that is, seven days after the due date). It creates the final collection letter seven days after the second collection letter (that is, 14 days after the due date).

On the **Collections process setup** page, set the **Action type** field to **Collection letter** to create the collection letters by using the previously described collection letter sequence. 

| Description   | Action type       | Business document       | When                   | Days in relation to invoice due date | Recipient |
|---------------|-------------------|-------------------------|------------------------|--------------------------------------|-----------|
| First notice  | Collection letter | Collection per customer | After invoice due date | 1                                    | None      |
| Second notice | Collection letter | Collection per customer | After invoice due date | 7                                    | None      |
| Final notice  | Collection letter | Collection per customer | After invoice due date | 14                                   | None      | 

When you use collections process automation, collection letters are created per customer, not per transaction.

You can't choose a business document such as **Collection letter 1**, because this document is set up in the collection letter sequence and is being used. Collections process automation only identifies what step (process) should be done. The collection letter sequence is used to create the collection letters. 

### Why does the process simulation result show only "Collection letter"? Does this result mean that the final notification was created? 

No, a collection letter was created according to the collection letter sequence. When collections process automation runs, it identifies which step of the process should be done, based on the oldest invoice that's due. If that step is a collection letter, the collection letter sequence is used. The results don't indicate which collection letter was created. 

For the setup that was described earlier, the collection letters are created based on the date when collections process automation runs.

- If collections process automation runs on January 16, it creates the first collection letter, because the date is one day after the invoice due date.
- If collections process automation runs on January 22, it creates the second collection letter, because the date is seven days after the invoice due date.
- If collections process automation runs on January 29 or later, it creates the final collection letter, because the date is 14 days after the invoice due date.

### Why did collections process automation skip the creation of collection letters and do only the last step, such as creating an activity?

A new parameter was added in Microsoft Dynamics 365 Finance version 10.0.39 to address this issue. The following example shows the situation. 

The collections process automation steps are set up in the following way.

| Description     | Action type       | Business document       | When                    | Days in relation to invoice due date | Pre-dunning | Recipient |
|-----------------|-------------------|-------------------------|-------------------------|--------------------------------------|-------------|-----------|
| Pre-dunning     | Email             | User-defined            | Before invoice due date | 5                                    | Yes         | None      |
| First notice    | Collection letter | Collection per customer | After invoice due date  | 1                                    | No          | None      |
| Second notice   | Collection letter | Collection per customer | After invoice due date  | 7                                    | No          | None      |
| Final notice    | Collection letter | Collection per customer | After invoice due date  | 14                                   | No          | None      | 
| Create activity | Activity          | User-defined            | After invoice due date  | 15                                   | No          | None      |

A customer invoice is due on January 15. In the collections process setup, two additional steps are added: **Email** and **Activity**.

- If collections process automation runs on January 10, an email is sent to the customer as a reminder that an invoice is coming due. This step is the **Pre-dunning** step.
- If the collections status of the invoice has changed to **Disputed** or **Promised to pay**, collections process automation skips that invoice during processing. If the collections status has changed to **Resolved** or **Promise to pay broken**, and the invoice is overdue, collections process automation picks up the invoice. On January 24 (when the invoice is nine days past due), the status is updated, and collections process automation runs the step that is closest to that date. That step is the **Second notice** step.
- If the collections status is updated on February 2 (when the invoice 17 days past due), the closest step is **Create activity**. In this case, only an activity is created.
- If you want collections process automation to start with the first step that's relevant, select the **Track step in collections process automation** option on the **Collections process automation** page. In this example, the relevant first step is **First notice**. Therefore, the first collection letter is sent on February 2. Collections process automation then continues to run. It creates the remaining collection letters and the activity, based on the February 2 date.
