--- 
# required metadata 
 
title: Create a closed-ended question
description: Closed-ended questions allow you to provide options for the respondent to choose from. 
author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: KMAnswerCollection, KMAnswer, KMQuestion, HcmLearningWorkspace  
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
# Create a closed-ended question

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Closed-ended questions provide options for the respondent to choose from. First, create the Answer group with the answers, and then create the question that uses the answer group. The demo data company used to create this procedure is USMF.

## Create an answer group

1. Go to **Questionnaire** > **Design** > **Answer groups**.
1. Select **New**.
1. In the **Answer group** field, enter a value.
1. In the **Description** field, enter a value.
    * Use the **Randomize** functionality to randomly place the answers in a different order each time the answer group is used for a question.  
1. Select **Answer**.
1. Select **New**.
    * Sequence number controls the order in which the answers are displayed, unless **Randomize** is selected for the **Answer group**.  
    * Points can be awarded to answers for use in scoring the questionnaire.  
1. In the **Points** field, enter a number.
    * Mark the correct answer to indicate that the selected answer is the correct one. Use this answer for scoring the questionnaire.  
1. In the **Answer** field, enter a value.
    * Continue to create answer selection options for the answer group.  
1. Select **New**.
1. In the **Points** field, enter a number.
1. In the **Answer** field, enter a value.
1. Select **New**.
1. In the **Points** field, enter a number.
1. In the **Answer** field, enter a value.
1. Select **New**.
1. In the **Points** field, enter a number.
1. In the **Answer** field, enter a value.
1. Select **New**.
1. In the **Points** field, enter a number.
1. In the **Answer** field, enter a value.
1. Close the page.
1. Close the page.

## Create the question

1. Go to **Questionnaire** > **Design** > **Questions**.
1. Select **New**.
1. Use the **Type** field to group related questions together.
        * For closed-ended questions, use input types such as **Checkbox**, **Alternative button**, or **Combo box**.  
1. In the **Input type** field, select an option.
1. In the **Answer group** field, enter or select a value.
1. In the **Text** field, type a value.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
