--- 
# required metadata 
 
title: Process collection letters
description: This procedure shows how to create, print, and post collection letters. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 12/04/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPosting, SysQueryForm, CustCollectionLetterNote   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0

---
# Process collection letters

[!include [banner](../../includes/banner.md)]

This procedure shows how to create, print, and post collection letters. This task uses the USMF demo company.


## Set up a collection letter sequence on the posting profile
1. Go to **Credit and collections > Setup > Customer posting profiles**.
2. Click **Edit**.
3. Select a collection letter sequence from the drop-down list. If you do not want to generate collection letters for transactions using this posting profile, leave the field blank.  
4. Expand the table restriction tab to change the way that collection letters are processed. If this field is set to Yes, then collection letters will be created for this posting profile.  

## Create collection letters
1. Go to **Credit and collections > Collection letter > Create collection letters**.
2. Select the transaction types for which you will collect letters. All of the open transactions for these types will be included in the calculation.  
2. In the **Collection letter** field, select an option.
3. Enter the date of the collection letter.
4. Select a posting profile if you changed **Use posting profile from** to **Select**. There are two posting profile options:   
   - **Account** – Use the posting profile that is assigned to the customer account for each interest note.   
   - **Select** – Use the posting profile that you select in the **Posting profile** field.  
5. Expand the **Records to include** section.
6. Click **Filter**.
7. In the **Criteria** field, enter a Customer ID. For example, enter 'US-001'.
8. Click **OK**.
9. Click **OK**.

## Print collection letters
1. Go to **Credit and collections > Collection letter > Review and process collection letters**.
2. In the **Status** field, select **Created**.
3. In the **Printed** field, select **Not printed**.
4. Click **Print**.
5. Click **Collection letter note**.
6. Expand the **Records to include** section.
7. Enter the cutoff date for postings.
8. Click **OK** to print the collection letter.
9. Post the collection letter.
   1. Click **Post**.
   2. Enter the posting date for the collection letter.
   3. Expand the **Records to include** section.
   4. Click **OK**.
   5. In the **Status** field, select **Posted**.
   6. In the **Printed** field, select an option.

## Control collection letters at the customer level
You can now choose to set up collection letters at the customer level so that the collection letter code for each transaction is 
tracked but the collection letter processing will be based on a single collection letter level that is stored on the customer. 
The single collection letter will contain all transactions that are overdue for the customer. Since the grace days are 
now tracked on the customer level, the next collection letter will not be sent until the number of grace days has 
passed for the next collection letter in the sequence, even though transactions become overdue after 
the last collection letter was sent. This option reduces the number of collection letters you will send per customer. 

### Set up the customer to control collection letters at the customer level
1.  Go to **Credit and collections > Setup > Accounts receivable parameters** and click on the Collections tab. 
2.  Change the value of **Create collection letter per** to **Customer**. 
3.  Go to **Credit and collections > Collection letter > Review and process collection letters**. Only one collection letter will be generated for a customer with all the overdue transactions.

## Ignore payments and credit memos when calculating the collection letter code
If you include payments and credit memos in the transactions that will be included in the collection letters, you may have payments or credit memos that will trigger a collection letter. You can control how payments and credit memos control the collection letter code by changing the value of the **Ignore payments and credit memos when calculating the collection letter code** parameter. 

To ignore payments and credit memos when calculating the collection letter code, do the following.
1. Go to **Credit and collections > Setup > Accounts receivable parameters** and click on the Collections tab. 
2. Change the value of **Ignore payments and credit memos when calculating the collection letter code** to Yes.


