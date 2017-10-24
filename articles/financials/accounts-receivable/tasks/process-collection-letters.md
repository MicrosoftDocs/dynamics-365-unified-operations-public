--- 
# required metadata 
 
title: Process collection letters
description: This procedure shows how to create, print, and post collection letters. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 10/23/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Process collection letters

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create, print, and post collection letters. This task uses the USMF demo company.


## Set up a collection letter sequence on the posting profile
1. Go to Credit and collections > Setup > Customer posting profiles.
2. Click Edit.
    * Select a collection letter sequence from the drop-down list. If you do not want generate collection letters for transactions using this posting profile, leave the field blank.  
    * The table restriction tab allows you to change the way that collection letters are processed. If this field is set to Yes, then collection letters will be created for this posting profile.  
3. Close the page.

## Create collection letters
1. Go to Credit and collections > Collection letter > Create collection letters.
    * You must select the transaction types for which you will collect letters. All of the open transactions for these types will be included in the calculation.  
2. In the Collection letter field, select an option.
3. Enter the date of the collection letter.
    * There are two posting profile options:   Account – Use the posting profile that is assigned to the customer account for each interest note.   Select – Use the posting profile that you select in the Posting profile field.  
    * Select a posting profile if you changed "Use posting profile from" to "Select".  
4. Expand the Records to include section.
5. Click Filter.
6. In the Criteria field, In the Criteria field, enter a Customer ID. For example, enter 'US-001'..
7. Click OK.
8. Click OK.

## Print collection letters
1. Go to Credit and collections > Collection letter > Review and process collection letters.
2. In the Status field, select 'Created'.
3. In the Printed field, select 'Not printed'.
4. Click Print.
5. Click Collection letter note.
6. Expand the Records to include section.
7. Enter the cutoff date for postings
8. Click OK to print the collection letter.

## Post the collection letter
1. Click Post.
2. Enter the posting date for the collection letter.
3. Expand the Records to include section.
4. Click OK.
5. In the Status field, select 'Posted'.
6. In the Printed field, select an option.

