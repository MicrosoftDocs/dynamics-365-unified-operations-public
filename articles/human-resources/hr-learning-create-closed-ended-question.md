--- 
# required metadata 
 
title: Create a closed-ended question
description: Closed-ended questions allow you to provide options for the respondent to choose from. 
author: twheeloc
ms.date: 08/26/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
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
# Create a closed ended question


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



Closed-ended questions allow you to provide options for the respondent to choose from. First, you need to create the Answer group with the answers, then create the question that will use the answer group. The demo data company used to create this procedure is USMF.


## Create an answer group
1. Go to **Questionnaire** > **Design** > **Answer groups**.
2. Click **New**.
3. In the **Answer group** field, type a value.
4. In the **Description** field, type a value.
    * Use the **Randomize** functionality to randomly place the answers in a different order each time the answer group is used for a question.  
5. Click **Answer**.
6. Click **New**.
    * Sequence number controls the order in which the answers are displayed, unless **Randomize** is selected for the **Answer group**.  
    * Points can be awarded to answers for use in scoring the questionnaire.  
7. In the **Points** field, enter a number.
    * The correct answer can be marked to indicate that the selected answer is the correct one. This can be used for scoring the questionnaire.  
8. In the **Answer** field, type a value.
    * Continue to create answer selection options for the answer group.  
9. Click **New**.
10. In the **Points** field, enter a number.
11. In the **Answer** field, type a value.
12. Click **New**.
13. In the **Points** field, enter a number.
14. In the **Answer** field, type a value.
15. Click **New**.
16. In the **Points** field, enter a number.
17. In the **Answer** field, type a value.
18. Click **New**.
19. In the **Points** field, enter a number.
20. In the **Answer** field, type a value.
21. Close the page.
22. Close the page.

## Create the question
1. Go to **Questionnaire** > **Design** > **Questions**.
2. Click **New**.
3. Use the **Type** field to group related questions together.
    * You can use input types of **Check box**, **Alternative button**, or **Combo box** for closed-ended questions.  
4. In the **Input type** field, select an option.
5. In the **Answer group** field, enter or select a value.
6. In the **Text** field, type a value.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
