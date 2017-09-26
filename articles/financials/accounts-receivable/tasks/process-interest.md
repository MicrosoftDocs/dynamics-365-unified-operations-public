--- 
# required metadata 
 
title: Process interest
description: This procedure shows how to create, print, and post interest notes. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 11/10/2016
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
# Process interest

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to create, print, and post interest notes. This task uses the USMF demo company.


## Set up interest on the posting profile
1. Go to Credit and collections > Setup > Customer posting profiles.
2. Click Edit.
    * Select an interest code from the drop-down list. If you do not want interest calculated for transactions using this posting profile, leave the field blank.  
    * The Table restriction tab allows you to change the way that interest is processed. If this field is set to Yes, then interest will be calculated for this posting profile.  

## Calculate interest
1. Go to Credit and collections > Interest > Create interest notes.
    * You must select the transaction types for which you will calculate interest. All of the open transactions for these types will be included in the calculation.  
    * If you select Interest, you will calculate interest on interest. You may want to check the laws governing the calculation of interest on interest before including these transactions.  
    * Interest will be calculated from this date to the "To date". If you do not specific a "From date", then all unposted interest notes will be canceled and interest will be recalculated from the transaction date.  
2. Enter the date of the interest note.
    * There are three posting profile options:   Account – Use the posting profile that is assigned to the customer account for each interest note.   Select – Use the posting profile that you select in the Posting profile field.   Transaction – Use the individual posting profile from transactions on which interest is calculated for each interest note. Transactions that do not have an assigned posting profile will use the posting profile that is specified in the Ledger and sales tax area of the Accounts receivable parameters form.  
    * Select a posting profile here if you changed "Use posting profile from" to "Select".  
3. Expand or collapse the Records to include section.
4. Click Filter.
5. In the Criteria field, enter a Customer ID. For example, enter 'US-001'..
6. Click OK.
7. Click OK.

## Print interest notes
1. Go to Credit and collections > Interest > Review and process interest notes.
2. In the Status field, select 'Created'.
3. In the Printed field, select 'Not printed'.
4. Click Print.
5. Expand or collapse the Records to include section.
6. Click OK.
7. Close the page.

## Post the interest note
1. Select an interest note that is ready to post (status is created).
2. Click Post.
3. Enter the posting date for the interest note.
    * Select Yes to create a general ledger transaction for each interest note.     If you do not select Yes, the interest on all interest notes to the customer is accumulated and posted to the general ledger in one transaction.  
4. Expand or collapse the Records to include section.
5. Click OK.
6. In the Status field, select 'Posted'.

