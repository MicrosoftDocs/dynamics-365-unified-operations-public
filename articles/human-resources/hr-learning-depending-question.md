--- 
# required metadata 
 
title: Make a question dependent on the answer of the previous question
description: Conditional questions allow you to specify what follow-up question will be presented to a respondent, based on the answer to the preceding question. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KMCollection, KMCollectionQuestion, KMCollectionQuestionTree, HcmLearningWorkspace  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Make a question dependent on the answer of the previous question


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



Conditional questions allow you to specify what follow-up question will be presented to a respondent, based on the answer to the preceding question. For example, if you ask "Do you prefer coffee or tea," a logical follow-up question can be determined depending on whether the respondent selects coffee or tea as their answer. The demo data company used to create this procedure is USMF.


## Find the existing questionnaire
1. Go to **Questionnaire** > **Design** > **Questionnaires**.
2. In the list, select the WorkFH questionnaire.

## Add all questions and sub-questions to the Questionnaire
1. Click **Questions**.
2. Click **New**.
3. In the **Question** field, select question number 00016.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click **Save**.
7. Close the page.

## Set the Questionnaire Sequence to Conditional and make the question dependent on the appropriate question
1. Click **Edit**.
2. Expand the **Setup** section.
3. In the **Question order** field, select 'Conditional'.
4. Click **Conditional** question.
5. In the tree, select 'Questions\Explain why you answered the previous question the way you did?'.
6. In the **Primary question** field, select question 00009.
7. In the list, click the link in the selected row.
8. In the **Answer** field, enter the answer sequence ID of the answer option you want to make the question dependent on. For example, enter 1 for the first answer option.
9. Click **Save**.
10. In the tree, select 'Questions\I am paid fairly for the work I do.'.
    * Note that the question tree updated to show the dependency.  



[!INCLUDE[footer-include](../includes/footer-banner.md)]
