--- 
# required metadata 
 
title: Distribute questionnaires using scheduling
description: Questionnaire scheduling allows you to plan and distribute questionnaires to multiple respondents. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KMKnowledgeCollectorPlanningTable, KMKnowledgeCollectorPlanningMulti, SysQueryForm, HcmPersonLookup, KMKnowledgeCollectorPlanning, HcmLearningWorkspace
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

# Distribute questionnaires using scheduling


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Questionnaire scheduling allows you to plan and distribute questionnaires to multiple respondents. The demo data company used to create this procedure is USMF.

## Create a questionnaire schedule

1. Go to **Questionnaire** > **Distribute** > **Questionnaire schedules**.

2. Click **New**.

3. In the **Scheduling** field, type a value.

4. In the **Description** field, type a value.
    * Set the schedule to **Anonymous** if the responses should be recorded without names associated to the response.  
    * Allowing anonymous results must be set up in the HR parameters first.  

5. In the **Type** field, select the planning type.  In this example, we will use the **Satisfaction** type.

6. In the list, find and select the desired record.

7. In the list, click the link in the selected row.

8. In the **Date** field, enter a date.

9. Expand the **Email for employee self service** section.

10. In the **Subject** field, type a value.

    * Example: Questionnaire available  

11. In the **Text** field, type the body of your email message. Note, the variable can be used to substitue values in the system.

    * Example: Dear %P%, Please log in to Employee Self Service to complete the Workforce Health questionnaire.  Contoso  

12. Click **Save**.

## Use the Setup details to select the questionnaire(s) to be answered as well as any queries to use to select respondents.

1. Click **Setup details**.

2. In the list, select a query to use to search the system for respondents for the questionnaire.

    * Example: Workers  

3. Click **View or modify query** to select specific people or adjust the query to find people who match specific criteria.

    * Note that all respondents must also be users in the system.  

4. In the list, mark the row for Person.

5. In the **Criteria** field, enter or select a value.

    * Select Julia Funderburk  

6. In the list, select Julia Funderburk

7. Click **OK**.

8. Click the **Questionnaires** tab.

9. In the tree, expand the node for the questionnaire type **Satisfaction Survey**.

10. In the tree, check 'Workforce Health Assessment'.

11. Click **OK**.

12. Click **Planned answer session**.

    * Note that **Planned answer sessions** have been created for each selected/queried user.  

13. Close the page.

## Start the questionnaire schedule in order to make the questionnaire available for respondents to complete.

1. Click **Functions**.

2. Click **Start**.

3. Click **OK**.

## Send the email to inform respondents of the available questionnaire.

1. Click **Functions**.

2. Click **Send email**.

3. Click **Cancel**.

## Use Planned answer sessions to monitor who needs to complete the questionnaire.

1. Click **Planned answer session**.

    * Delete any remaining planned answer session when you're ready to end the scheduled session.  

2. Click **Delete**.

3. Click **Yes**.

4. Close the page.

## End the schedule when all respondents have completed the questionnaire and/or all remaining Planned answer sessions have been deleted.

1. Click **Functions**.
2. Click **End**.
3. Click **OK**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
